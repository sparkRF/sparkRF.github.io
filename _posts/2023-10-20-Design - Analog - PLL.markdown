---
layout: post
title:  "Analog - PLL"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 3
---

PLL : Phase Locked Loops<br>
<br>
<br>
원래는 주파수 높은 clock을 만들려고 쓰지만, 동작 주파수가 낮은 경우에도 clock의 jitter를 없애기 위해 PLL을 쓰기도 한다.
PLL이 Lock되면, PLL block에서 Lock 신호를 high로 올려준다.
다른 block들은 그거 보고 동작하기 시작하면 된다.

chip이 켜지면 Analog trimming data 등 정보가 들어있는 Flash memory를 읽는데,
Flash memory를 PLL이 Lock 되기 전에 읽기도 한다. PLL이 Lock되는 데에는 시간이 좀 걸리니까, 시간 아끼기 위해서다.

PLL은 출력 신호의 phase와 입력 신호의 phase를 비교하는 feedback system이다.
비교는 PLL 안의 phase detector에서 진행된다.

그니까, 이런 식이다.

*그냥, XOR gate를 phase detector로 사용할 수 있다
이상적인 phase detector면 출력 전압의 시간 평균과 phase 차이가 비례하며, phase 차이가 0이면 출력 전압의 시간 평균도 0이다.



생각해보면, PD가 XOR gate랑 상당히 비슷하다는 것을 알 수 있다.

그래서 PD는 그렇다 치고, PLL은 뭔가?

우리가 VCO를 동작시키고 있는데, VCO의 출력파형의 phase가 reference clock의 phase랑 딱 맞았으면 좋겠을 경우, 어떻게 해야 할까?

VCO에 넣는 전압을 잠시 바꿨다가 원래대로 돌려놓으면 된다.
전압이 바뀌면 출력 파형의 주파수가 변하니까, 이걸로 phase 맞춰놓고 다시 전압 복구해서 원래 주파수로 돌려놓으면 된다.



PLL 안에 loop filter가 있어서, 나중에 lock이 안풀리는 문제가 있었던 적이 있다.

PLL에서 왜 lock detection을 하나? 처음에는 PLL 주파수랑 external 주파수랑 좀 다르니까.
주파수가 같아지면 그때 PLL clock으로 바꿔준다. 그게 external과 lock이 된 상태다.

PLL을 왜 쓰냐? 여기서는 피에조센서에 쓸 PWM이 필요하다보니 clock boosting이 필요해서 썼다.

PLL:
보통 오실레이터에서 출력되는 클락은 8MHz, 12MHz, 16MHz라서 실제 시스템 동작속도보다 느리다
그래서 PLL은 주파수를 올리고 안정적으로 만든다
여기서 나온 클락신호가 cpu에 전달된다

Mcu 내의 다른 로직들은 보통 cpu보다 구동 주파수가 낮다. 그래서 prescaler(전치분주기)로 주파수를 내려준다


PLL은 lock되면 lock신호가 high가 된다. high가 되면 다른 block들이 동작하면 된다.
Flash 읽을때, PLL이 lock 되기 전에 읽는 경우도 있다. 시간 아끼기 위해서 이런 동작을 한다. Lock되는데에 시간이 좀 걸리니까.

주파수가 16MHz밖에 안되는데 PLL을 쓰는 경우도 있었다. 이건 jitter 줄이려고 쓴거다.

prescaler: clock을 다른 주파수로 만든다. /2, /4, /8 등.
clock gating: 안쓰는 block은 clock마저 안들어가게 꺼버리는거. power 아끼려고 쓰는 기술이다.

DMA: Direct Memory Access
CPU를 통하지 않고도 메모리에 접근할 수 있게 하는 기능.
이게 있으면, 다른 block이 memory에 접근해야 할때 CPU는 데이터 전송하라고만 해놓고
다른거 하다가 DMAC(DMA Controller)한테 interrupt 신호 받으면 아 전송 다 끝났구나 한다.

WDT: Watchdog Timer
비정상 상태, 무한루프 등 이상한 상태에 빠지면 System을 리셋하는 장치

ECC Memory: Error Correction Code Memory
데이터 손상을 복구하는 메모리.
우주선 중성자 방사능 때문에 cell에 저장된 정보가 바뀔 수 있어 필요하다.
이런 에러는 고도가 증가하면 엄청나게 늘어난다.
ECC Memory가 정보를 복구하는 알고리즘을 ECC logic이라 부른다.

SCU: System Controller Unit
각 peripheral들이 clock, memory 등 resource를 사용할때, 그걸 관리해준다.
SCFW(System Controller Firmware)에 의해 동작한다.
그래서 온갖 subsystem들을 SCU에서 관리한다.

PMU: Power Management Unit

RTC: Real Time Clock
그냥 시간 재는 회로다.

Boot sequence:
Power on -> POR/BOR 동작 ->
HIS OSC켜짐 -> PLL 켜짐 -> PLL Lock까지 대기 -> flash clock 켜짐 ->(Always on Block들)
flash에서 analog block 읽기(Flash Controller)
-> AHB prescaler, APB prescaler, Timer prescaler, clock gating 켜짐(clock generatro)