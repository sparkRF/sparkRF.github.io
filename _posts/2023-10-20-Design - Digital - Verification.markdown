---
layout: post
title:  "Digital - Verification"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 6
---

Digital 회로 Verification:

일단, RTL로 이루어진 IP들을 다 받아와서, 그걸로 Top module을 만든다.
모든 IP를 RTL로 만드는건 아니고, DRAM 등은 System Verilog, System C 또는 C로 모델링하기도 한다.

Top module에는 트랜지스터가 수억개 있다.
이걸 FPGA나 에뮬레이터에 넣어야 하는거라, Resource 낭비를 최대한 줄여야 한다.
DRAM같은거 그냥 넣으면, 그 block 하나가 FPGA 안에서 flipflop 엄청나게 잡아먹는다.


펌웨어 등은 C언어로 ELF 단계까지만 compile하고, hex code로 변환시킨다.
그리고 이 hex code가 RTL 안 CPU에 올라가도록 구현한다.(테스트벤치로)

그 다음, HDL side와 HVL side를 명확하게 구분한 다음 이것을 각각의 domain으로 진행시킨다.
말 그대로 time domain이 다른거다.
이것을 two top structure라 한다.

테스트벤치는 컴퓨터 CPU의 clock대로 동작하고,
HDL side는 FPGA에 들어가서 FPGA의 clock대로 동작한다.

여기서 중요한 점은, 둘 사이 transaction을 최대한 최적화해야 한다는 점이다.

FPGA가 매 clock마다 HVL에서 데이터를 받아온다면, FPGA의 빠른 system clock을 전혀 활용하지 못하는 꼴이 된다.
계속 데이터 받아오느라 동작 끊길거면 FPGA를 왜 쓰냐? 그냥 시뮬레이터 쓰면 되지

그냥 시뮬레이터를 써서, testbench가 DUT를 감싸는 방식을 one top simulation이라 부른다.


Verification을 확실히 해줘야 제품 하드웨어에 문제가 없다.
펌웨어 문제면 업데이트하면 되는데, 하드웨어 문제는 답이 없다.