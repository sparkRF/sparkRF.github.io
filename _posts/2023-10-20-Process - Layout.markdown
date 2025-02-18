---
layout: post
title:  "Layout"
date:   2023-10-04 19:31:29 +0900
categories: Process
order: 14
---

Layout: 설계한 회로가 칩으로 제작될 수 있도록, 회로를 물리적 구조로 구현한 것

LPE를 하면 Metal과 metal 사이 C, Metal 내 저항 성분들을 뽑아내준다.




Layout이 완성되면, Layout에 맞춰 포토마스크가 제작된다.
그리고 포토마스크에 그려진 대로 회로가 웨이퍼에 새겨지게 된다.


동일한 회로라도 사용 목적, Layout 설계자에 의해 다른 형태의 Layout이 나올 수 있다.
Layout 내 소자 제작 및 연결 방법에 따라 다른 Parasitic R, C 성분이 생겨 소자 특성이 달라진다.
그래서, 최대한 원래 설계 의도와 동일하게 회로가 동작할 수 있도록 Layout을 잘 만들어줘야 한다.

여기서 소자라 함은 주로 MOSFET, 저항, 캐패시터를 말한다.


MOSFET Layout:
Source와 Drain 사이, Drain과 Body 사이의 Junction Capacitance 최소화
Source, Drain 영역의 Contact 간격 균일화를 통해 균일한 전위 분배
동일한 입력 Bias 전압이 가해지는 TR이라면, 일정한  TR Unit width 비율 유지

각각의 Process에 적당한 Physical Size가 결정되어 있음
Layout design 단계에서는 Physical Value(전기적 특성)을 고려한 Place & Route를 적용
Width 와 Length의 비가 보통 10~200 범위 내 유지
특별한 Output driver 단에서는 1000배 이상 되는 것도 있음


저항 Layout:
Value의 정확도와 크기에 따라 재료 선택
재료에 따라 편차가 있으며 Chip상에서 차지하는 면적과 정확도를 고려하여 적용
Layout Design에서는 일반적으로 정확한 값을 구현하기 유리한 Poly저항을 이용
정확도는 떨어지지만 큰 값을 구현하기 위해 Diffusion 저항을 사용하기도 함
Gradient를 최소화 하기 위해서 inter-digitized 및 Centroid 구조를 주로 사용


캐패시터 Layout:
물리적 특성상 재료의 유전율,  Area, Distance에 의해 Value가 결정
주변 소자와의 배치된 상태에 따라서도 Variation이 발생
 Layout Design에서는 주변소자, Route 종류, 배치 방법 등 Cross Talk를 최소화 하면서 정확한 Value를 유지하기 위한 많은 방법들을 적용


배선 Layout:
일단 전류가 많이 흐르는 곳은 도체가 두꺼워야 한다.
그리고 도체들이 overlap되거나 하면 coupling capacitance가 생길 수 있는데,
이 Capacitance때문에 계산한 gain이 안나온다거나 PSRR이 안좋아진다거나 할 수 있다.
배선은 최대한 간소화한다. 민감한 Analog 배선을 굳이 길게 만들 필요가 없으니, 최대한 짧게 만든다.


Matching:
Matching 관련해서는 아예 파일이 따로 있으니까 그거 보고 정리
Parasitic R, C 성분을 완전히 제거할 수는 없다.

Matching이 요구되는 소자(MOS, CAP, RES):
Matching을 요하는 소자들의 위치는 가깝게 할 수록 유리
3차원적인 고려를 통하여 주변 또는 상하의 조건을 동일하게 감안하여 Layout 진행
Layout에서는  parasitic 성분을 완전히 제거할 수 없음
최소화 하거나 parasitic 성분을 입력 TR에서 동일하게 해 주어야 함(Matching의 중요성)
입력  TR은 중간에 배치하는 것이 유리(AMP 의 offset을 최소화 할 수 있음)
Source를 공유하여 작업하면 면적상 유리
     - but source를 공유하면  revision 작업 시 회로 분리 불가능


Guard ring technique:
Guard ring에 clock noise를 차단하는 방법
Substrate contact 또는 well contact 사용
Analog와 Digital Guard ring Voltage source 분리


Noise Coupling:
Analog line과 Digital line 사이의 Coupling Capacitance, Crosstalk에 의한 영향
Analog와 Digital line이 병렬로 구성되어 있을 때 Coupling 발생, 겹치면서 혼선이 생겼을 때 발생 
Shielding 작업으로 해결


Shielding 작업:
Analog Line과 Digital Line 사이에 GND Line을 깔아놓는다.


Latchup:
NMOS TR과 PMOS TR의 전압차가 크고 근접해 있을때 Latchup이 발생하기 쉽다.
Latchup이 발생하면 회로 short, 회로 기능 상실, 과전류 등 문제가 생긴다.

Latchup을 방지하려면 전압차가 큰 TR은 원거리 배치하고, bulk bias를 많이 넣는다.
아마 같은 전압 TR끼리는 가까이 배치하고, 인접 block과의 거리를 멀리한다.

Guardring 작업도 한다.

단차:
각 소자의 Pattern 및 소자 사이를 연결하는 배선이 고르지 못한 표면에 형성
Chip은 무척 많은 공정을 거처 제작
각 공정을 거치면서 필수적으로 나타나는 현상
TEXT 도포 및 식각 공정에 의해 위로 볼록하게 나오기도 하고 밑으로 오목하게 들어가는 Pattern 발생 
동일한 길이로 배선을 연결  실제 Chip에서 만들어지는 길이는 다르게 됨(연관된 각 소자의 동작 특성에 영향을 미침)
작은 변화가 증폭기를 거치게 되면 큰 차이로 나타나게 되므로 이에 대한 감안이 필요


소자간 isolation:
P-substrate에는 가장 낮은 전압, N-well에는 가장 높은 전압
이러면 역방향 다이오드라서, 다른 소자와 분리하는 isolation 역할을 하게 된다.

Chip을 구성하는 각 block들은 인가되는 신호와 주파수가 다르고, 사용되는 전원이 다른 경우도 많다. 그 block들이 서로 영향을 미치는 현상이 일어날 수 있으니, Guard ring 작업을 해줘야 한다.

Sub이 흔들리면 안되니까, deep nwell로 isolation을 해줘야 한다. - 이건 여기얘기가 맞나


Floor plan:
layout에서, 트랜지스터 단위 배치가 아닌 block 단위 배치
면적을 최대한 줄이는 것이 좋다.
면적이 작을수록 웨이퍼 하나당 chip을 더 많이 생산할 수 있다.

Floor plan을 할 때 고려해야 할 점:
Noise의 민감도는 Digital에서 Analog로 갈 수록 민감도가 커지지만, Noise는 Analog에서 Digital로 갈수록 커진다.
*뭔소린지 모르겠으니 좀 알아보겠다.
Analog와 Digital의 Power는 반드시 분리하며, 특별히 주의가 필요한 Block의 경우 추가로 Power를 분리한다.


Verification rule:
검증 (LVS, DRC, Antenna, LPE, ... 등) Rule
검증 rule(최종버전 확인, DRC/LVS/QRC 사전 확인, Dummy 소자 인식 확인 필수)
Layout grid 설정
Floor plan 확인
Estimate Layout TAT 산출
Estimate Layout TAT (Turn-Around Time) 산출
Design Rule
Layout Notice
Critical / Dirty Path
Power / GND Path
Resistance / Capacitance of Path
Substrate Contact
ESD / Latch-up
PIN / PAN Assignment for Assembly
DRC / LVS/LPE
Origin
Index


LGPG Flow(Layer Generation Pattern Generation):
Rule file과 GDS file을 준비한다.
마지막이:
Job deck view

mask 제작 

M1을 세로로 배선했으면 M2 배선은 가로로, M3배선은 세로로 한다.
metal layer마다 가로세로를 번갈아 하는 것이다.
바로 다음 layer랑 같은 방향으로 쭉 뻗어있으면 사이에 capacitance가 크게 생겨서 그렇다.

capacitance가 작아야 하는 node는 높은 layer를 쓰기도 한다.
다른 node들은 metal1,2로 연결하고 중요한 node는 metal4,5로 연결하는 식
높이 떨어뜨려놔야 사이 거리가 늘어나서 capacitance가 줄어든다.


power line 저항을 줄이기 위해 metal 배선을 넓게 하는데, 이걸로도 부족할 수도 있다.
이럴 때는 Metal 1,2를 둘다 깔아놓고 Via로 쭉 연결해둔다.


display driver에는 amp가 1000개씩 들어간다.
그래서 power line도 길기 때문에 IR drop에 의해 각 amp에 전압이 다르게 들어갈 수 있다.
Amp 1000개면 LPE도 제대로 못돌린다. 너무 소자가 많으니까.

Digital에서는 IR drop 문제될때가 많다. 한번에 전류를 크게 당기니까 전압이 많이 떨어져서 들어온다.
그래서 digital block 바로 옆에 decap cell을 달아서 문제를 어느정도 해결한다.
전류를 decap cell에서 당기면 IR drop이 안보이니까.

PCB에서 IC 바로 옆에 캐패시터 붙이는 것도, PCB 배선에 의한 L,R 최소한으로 보려고 그러는거다.


RDL: Redistribution Layer

IO Block은 layout할때 Ring 모양으로 하는게 좋다.


DDI처럼 Amp가 500~1000개씩 있어서 LPE가 불가능한 경우에는
도체 면적과 ILD, IMD의 유전율로 캐패시턴스를 예상해볼 수 있다.
근데 요즘은 파운드리에서 ILD, IMD값을 암호화해서 주기 떄문에 좀 어렵다.

만약 안다면, 계산해서 나온 값에 2배정도 하면 대강 맞다.
2배 하는 이유는 fringing field영향 반영이다.

