---
layout: post
title:  "혈당센서 목표스펙"
date:   2023-10-04 19:31:29 +0900
categories: Miscellaneous
order: 2
---

혈당센서 목표스펙:<br>
전류가 좀 작아야 한다. 3V전지 두개로 2년을 가야 한다.<br>
High frequency에서 100uA 이하, 1ow sleep current를 원한다.<br>
<br>
Clock은 crystal로 만드는데, crystal 안의 인덕턴스가 변해서 주파수가 변한다?<br>
<br>
DAC으로는 Delta-Sigma 또는 R2R을 생각중이다. 둘 다 전류를 많이 먹는 구조는 아니다.<br>
<br>
Brownout: 전원의 전류가 부족해서 전압이 정상적으로 인가되지 않는 상황. 어원은 백열전구에 전압이 덜 걸리면 갈색으로 보이는 현상<br>
<br>
MCU에서 Brownout이라 부르는 현상도 비슷한 현상이다. 전원의 전류가 딸려서 전압이 충분히 안걸리는건데, 이러다가 전원전압이 동작전압 범위를 벗어나 더 아래로 내려가버리면 MCU가 이상하게 동작할 수 있다.<br>
<br>
동작 범위를 벗어났다가 돌아와도 문제가 남아있을 수 있다. MCU 내 CPU가 이상동작으로 플래시메모리 지워버린다거나 하는 문제가 발생할 수 있다.<br>
<br>
이런 일을 막는게 BOR(Brownout Reset)이다. 전원 전압이 동작범위 아래로 내려가 Brownout이 발생하면 device 자체를 reset state에 넣어버리는게 BOR이다. 그 후 전원전압이 복구되면 device를 다시 켠다.<br>
<br>
POR Power on Reset도 있다. POR은 device가 켜질 때 device 전체를 reset해서, device가 확실히 ‘known state’에 있도록 해준다.<br>
<br>
Logic cell에 쓰이는 라이브러리들:<br>
RVT: Regular Voltage Threshold<br>
HVT: High Voltage Threshold<br>
LVT: Low Voltage Threshold<br>
SLVT: Super Lowe Voltage Threshold<br>
<br>
Threshold가 높으면 속도가 느리지만 leakage가 적고,<br>
Threshold가 낮으면 속도가 빠르지만 leakage가 많다.<br>
<br>
그래서 어디는 HVT, 어디는 LVT로 만들어 최적화할 수 있을 것이다.<br>
<br>
그런걸 ‘Multi Threshold Voltage Design’이라 부른다.<br>
<br>
삼성전자는 MPW로 칩 만들어주는거 신청을 상시로 받지는 않는다. 예를 들어 10월에는 LFR6LP, 12월에는 LF6S 공정을 신청받는다. 주문이 모여야 공장을 돌리니까. 하나하나 공장을 돌려줄수는 없지 않은가.<br>
<br>
LF6S: Logic 전압 1.5V, 공정 80nm (S=Shrink라 80nm)<br>
LFR6LP: Logic 전압 1.2V, 공정 90nm (LP=Low Power)<br>
<br>
LF6S는 Oxide가 두꺼워서 전압을 높게 가져갈 수 있다.<br>
<br>
DRC(Design Rule Check): 이 공정으로 chip 만들거면 layout이 이런저런 식으로 되어 있어야 한다 를 말하는게 Design Rule이다. 그리고 이게 지켜졌는지 확인하는게 DRC다.<br>
<br>
Design rule에는 width rule, spacing rule, enclosure rule 등이 있다. 각각 가능한 최소 width, 필요한 최소 spacing, 덮을때 필요한 최소 면적을 규정한다.<br>
<br>
LVS(Layout Versus Schematic): Layout이 schematic과 일치하는지 확인하는 작업<br>
<br>
LPE(Layout Parasitic Extraction): Layout을 보고, 발생할 수 있는 parasitic 성분을 확인하는 작업<br>
