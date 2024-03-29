---
layout: post
title:  "Materials - Wafer"
date:   2023-10-04 19:31:29 +0900
categories: Process
order: 12
---

반도체를 왜 쓰는건가? 스위치를 만들려고. 옛날에는 진공관을 썼는데, 이게 트랜지스터로 대체된거다. 크기도 작고 효율도 좋고 쉽게 깨지지도 않으니까

BJT에서 CMOS로 변하기도 했었다. 이건 기억이 안나네 왜더라

원래 반도체는 Ge를 썼다.<br>
근데 왜 Si로 넘어갔나? 녹는점 높아서, 더 구하기 쉬워서.<br>
<br>
근데 고성능 반도체 소자가 필요해지면서, 다른 반도체 물질을 사용하는 경우가 많이 생겼다.

더 ideal한 스위치를 만들기 위함이다.

여기서 ideal switch:
무한히 빠른 switching speed, 전기저항 0, 가격 0

<br>
<br>
![alt text](/public/img/material1.png)<br>
Common semiconductor material characteristics. [1]<br>
<br>

SiGe:

SiC:

GaAs:

GaN:

InP:







![alt text](/public/img/material2.png)<br>
Comparison of millimeter-wave technology options.<br>
<br>
![alt text](/public/img/material3.png)<br>
반도체별 주요 소자 및 특징.<br>
<br>
![alt text](/public/img/material4.png)<br>
HBT vs FET.<br>
<br>
[1] SiGe and CMOS Technology for State-of-the-Art Millimeter-Wave Transceivers<br>
[2] ETRI GaN,GaAsMMIC개발 및 전망
[3] Comparing GaAs and GaN technologies for RF, J. L. Jimenez

<br>
<br>
Wireless Transceiver에는 원래 GaAs가 많이 쓰였는데, 요즘은 CMOS와 BiCMOS가 많이 쓰인다.
fabrication 비용이 낮고, 디지털 시스템과의 연결이 용이하기 때문이다.

아직 GaAs, GaN을 쓰는 분야도 많다. GaAs는 noise가 적다.

MMIC = Monolithic Microwave Integrated Circuit

MMIC 시장의 상당 부분은 자동차 레이더 transceiver가 차지한다.
그래서 wideband Si MMIC가 요즘 많이 쓰인다.

주파수가 높은 전파는 멀리 못간다.
Oxygen absorption의 영향으로 attenuate된다.

Oxygen absorption은 60GHz정도에서 최대다.

멀리 못가는게 장점일때도 있다. 바로 옆동네에서도 그 주파수를 쓸 수 있다. 안섞이니까.

E-band 전파는 비교적 멀리 가고, V-band 전파는 비교적 멀리 못간다.

그래서 E-band transceiver에는 CMOS, BiCMOS보다 GaN, GaAs를 많이 쓴다.
Output power를 더 크게 낼 수 있고, linearity가 비교적 좋기 때문이다.

V-band는 신호가 멀리 못가니까 power가 좀 적어도 된다. 그래서 CMOS, BiCMOS를 많이 쓴다.
CMOS, BiCMOS를 쓰면 Digital radio들과 함께 한번에 찍어낼 수 있기 때문에 더 경제적이다.

원래 100GHz 위에서는 InP가 자주 보였는데, 요즘은 다른 technology들도 보인다.

FDSOI CMOS?

InP devices : HBT, HEMT

GaN device들은 noise가 적어 sensitive receiver에 쓰인다.

GaAs도 고주파에서 noise 성능이 우수하다.

mHEMT(metamorphic HEMT)를 쓴 GaAs LNA(Low Noise Amplifier) 예시도 있다.

scale돼서 크기가 작아진 CMOS공정, 즉 scaled CMOS공정은:
크기가 작아서 input capacitance는 작아서 좋지만,
interconnect parasitic때문에 ft가 악화되기 쉽다.

실제로는 45nm, 28nm CMOS 정도가 성능이 최대치를 갖는 지점이다.
이거보다 작으면 소자들이 parasitic gate capacitance, resistance에 크게 영향받는다.
그래서 RF performance가 안좋아진다.
그래서 RF에서는 더 줄이는게 의미가 없다.

그래도, FDSOI, SOI 등으로 RF performance 개선하려고 노력하긴 한다.

FDSOI: Fully Depleted Silicon On Insulator

Bipolar transistor들은 CMOS 대비 더 높은 gm, 더 낮은 1/f noise를 갖는다.
breakdown voltage도 더 높고, reliability도 더 높다.

Hot carrier injection:
MOS thermal reliability 저해
이렇게 되면 Vds가 클 경우 gm, Vt가 degrade된다.

Silicon substrate를 쓸 때, 어떻게 ground reference를 만들 것인가?
III-V에서는 off-chip ground plane을 자주 쓴다. multi-MMIC design에서도 그렇다.
multi-MMIC에서는 1개 metallization layer가 모든 ground node들을 연결한다.

Silicon에서는 on-chip metal layer로 ground plane을 만들어야 한다.


ETRI GaN,GaAsMMIC개발 및 전망:

MMIC 기술은 RF부품을 설계하고 제작하는 기술이다

옛날 RF시스템은 hybrid 형태였는데,
1980년대부터 hybrid 회로(HMIC)들이 MMIC로 대체되기 시작했다.

여러 기능의 회로들을 한 칩 위에 집적해 소형화, 경량화, 원가 절감이 가능해졌다.

하지만 MMIC는 HMIC와 달리 한번 제작 후에는 튜닝이 불가능하다.
그리고 소자들 사이 간격이 좁아 crosstalk, coupling 등 parasitic effect가 HMIC보다 크다.

Bandgap은 GaN이 가장 크다.

기판의 물질 특성에 의해 능동소자 특성이 결정되고, 그거에 따라 적용 응용분야가 달라진다.

InP MMIC는 GaAs MMIC보다 제작 비용이 비싸지만, 주파수 특성이 고주파에 적합하다.

SiGe MMIC는 Si기판 위에 만들 수 있기에, 기존 Si공정에 단계만 추가하면 된다.
그래서 생산 효율이 높아 가격이 싸다는 장점이 있다.

GaN MMIC는 전자 이동도는 낮지만 고전압 동장이 가능하고, 높은 전력 밀도를 만들 수 있다.

GaN은 열 전도도가 Si보다 3배, GaAs보다 7배정도 높아 냉각이 쉽다.


Qorvo의 Comparing GaAs and GaN technologies for RF:

정보를 더 많이 보낼수록, 더 확실한 linearity가 문제가 된다.

더 많은 channel -> device당 더 많은 전력 필요 -> linearity가 줄어든다

symbol constellation이 더 복잡해짐 -> symbol 사이 거리가 줄어든다 -> linearity가 더 중요해진다

Shannon's Capacity Equation:
C = BW * log2(SNR)

GaN:
큰 Bandgap -> 강한 전기장
High Saturation Velocity, high Charge capability -> 큰 전류

그리고 강한 전기장과 큰 전류는 높은 power density를 가능하게 한다.

RF power, power electronics 분야에서는 FET의 성능을 3개 variable로 평가한다.
IDmax, Vbr, Ron 3가지다.

IDmax, Vbr은 power density를 보여주고,
Vbr, Ron은 efficiency를 보여준다.

근데, power density가 왜 중요한가?
device를 더 작게 만들 수 있기 때문이다.

device를 더 작게 만들면 뭐가 좋은가?
capacitance가 더 작어지고, insertion loss가 줄어든다.
capacitance가 작기 때문에 BW가 커지고,
insertion loss가 작기 때문에 Efficiency가 높아진다.

GaN on SiC:
GaN crystal과 SiC crystal은 입자 사이 거리가 다르다.
그거때문에 gate current가 크고, trapping도 더 높다.

GaN의 heat flux는 엄청나다. 즉, 열이 많이 난다.

GaN은 bandgap이 큰 물질이다. -> strong Ionic bond
아마 그래서 chemical etch가 어려워 physical etch를 해야 하고, 그래서 stop etch layer가 없다는 것 같다.

bandgap이 크기 때문에 생기는 문제는 또 있다.
bandgap이 크면 p-doping이 잘 안된다는 것 같은데, 확인 필요

시장 규모는 GaAs > GaN on SiC다.

왜냐?
p-doping이 잘 안되고, stop etch layer가 없기 때문에 GaN에서는 좋은 HBT를 만들 수가 없다.

근데 모바일에서는 HBT가 중요하다.
HBT는 주어진 전압에 대해, FET보다 효율적이고 linear한 device라 그렇다.

HBT vs FET, Efficiency:
HBT의 vertical current는 FET의 horizontal current와 비교했을때, HBT가 더 작은 Ron을 가질 수 있게 한다.

Ron이 더 작으면 RF efficiency가 더 좋아지며, 낮은 전압에서는 이게 더 중요하다.

그리고 전류를 미분해보면 HBT의 beta가 FET의 gm보다 더 linear하다.

근데 GaN은 이 HBT를 제대로 만들 수 없다고 했잖아?
그래서 GaAs 시장이 더 큰거다.

그니까, GaAs vs GaN이라고 보기보다는 HBT vs FET이라고 보는게 더 적합할거다.

수많은 III-V 기술자들이 power density를 늘리기 위해 연구하고 있긴 하지만, 현재 III-V 시장은 linearity spec에 의해 굴러가고 있다.


EPC라는 회사 사이트:
GaN 기반 power device들은 Si 기반 power device들보다 훨씬 성능이 좋다.
high conductivity 덕분에 higher breakdown strength, faster switching speed, higher thermal conductivity and lower on-resistance 덕분이다

GaN은 다양한 substrate들 위에 만들어질 수 있다.
사파이어, SiC, Si 등.

Si 위에 GaN Epi layer를 만들 경우, 기존 Si 생산시설을 활용할 수 있다. 따라서 더 경제적이다.

GaN은 반도체 power device, RF components, LED 등에 쓰인다.

HEMT(High Electron Mobility Transistors)는,
서로 다른 bandgap을 갖는 2가지 물질의 junction에서 발생하는 2DEG(2-Dimensional Electron Gas)를 이용한 소자다.

GaN based HEMT는 Si 기반 소자들보다 빠른 switching speed, 높은 열전도율, 낮은 on-resistance를 갖는다.

그래서, GaN transistor, GaN IC를 power conversion system 내 회로에 사용해 efficiency를 늘리고, 크기를 줄이고, 가격을 줄일 수 있다.

GaN은 Si보다 천배 효율적으로 전자를 conduct할 수 있다.

GaN 공정은 Si보다 근본적으로 저렴하다.
각 소자가 Si 소자보다 훨씬 작기 때문에, 각 웨이퍼마다 소자가 더 많이 생산될 수 있다.

그래서 GaN이 high-efficiency power transistor에 많이 쓰이게 됐는데, 이게 어떻게 동작하나?

2DEG 생성:
GaN 결정 위에 얇은 AlGaN층을 만든다.
interface에 strain이 발생하고, 그걸 compensate하기 위해 2DEG가 생긴다.
전기장이 걸리면, 2DEG를 통해 전류가 원활히 흐른다.

Efficient conduction:
2DEG는 전자를 interface의 아주 좁은 영역에 가둬놓고 전류가 흐르게 한다. 이렇게 가둬놓기 때문에 전자의 mobility가 올라간다.
unstrained GaN에서는 1000cm2/Vs, 2DEG 영역에서는 1500~2000cm2/Vs

GaN이 새로운 application을 가능하게 하는가?:
GaN-on-Si 트랜지스터는 MOSFET보다 10배, IGBT보다 100배 빠르게 switching을 한다.

이렇게 GaN이 빠른 동작을 할 수 있었기 때문에,
4G/LTE base station에서 RF envelope tracking을 위해,
LiDAR에서 자율주행을 위해 쓰이게 됐다.
빠른 동작이 필요한 분야다.

GaN 트랜지스터들은 빠를 뿐 아니라 크기도 작았다.
그래서 로보틱스, 의료전자, 인공위성, 드론 등에도 쓰인다.

GaN device는 같은 전압에서, 단위면적당 on-resistance가 Si, SiC device보다 훨씬 낮다. -> smaller die, smaller packaging 가능

fast switching -> passive component들의 크기 감소 가능
그러면 또 size, weight 감소 가능


GaN은 power level device와 signal level device를 같은 웨이퍼에 만들 수 있다는 장점이 있다. 그니까, same substrate

discrete device들은 점점 높은 power density로 동작하는데,
원래 얘네는 전류를 외부와 연결된 bump를 통해 끌어와야 한다.
근데 점점 power density가 높아지면 이게 어려워질 수 있다.

그래서, 한번에 integrated된 solution으로 GaN 소자들이 쓰일 수 있다.
-> monolithic integration

GaN 트랜지스터는 크기가 작아서 PCB 면적을 줄일 수 있다. 가격 절감

chip scale packaging을 하면 power transistor의 저항, 인덕턴스, 크기, 열저항, 가격을 줄일 수 있다.

package 때문에 인덕턴스가 생길 경우, power transistor들이 더 느리게 켜지고 꺼지게 된다.

thermal resistance도 작다.
eliminating all barriers between the active device and the ambient environment gives heat the most direct path to the outside world.

eGaN?

GaN과 SiC 모두 wide bandgap semiconductor solution이다.
high voltage, high frequency에서 동작 가능하다.

SiC는 900V 이상 전압에 적합하고,
GaN-on-Si는 700V 이하에 적합하다.

격전지는 700V~900V다.
여기가 전기차용 전자장치들이 쓰이는 영역인데,
GaN, SiC, Si IGBT들이 싸운다.

GaN 시장은 점점 커질 것으로 전망된다.
fast charger, class-D audio, power bank, ToF센서 등.
이런 application들에서 ToF는 더 우수한 

신재생에너지가 많이 쓰이게 되면서, Solar microinverts, optimizers, ESS 제조사들은 점점 GaN을 쓰고 있다.
높은 효율, 높은 전력밀도, 개선된 reliability.

원래 datacenter에서는:
backplane에서 48V를 받고, 그걸 12V로 바꿔서 processing board에 주고, 그걸 다시 1V정도로 바꿔서 digital chip들에게 줬다.
근데 GaN을 쓰면 switching speed가 더 빨라서  48V를 바로 1V로 바꿀 수 있다.
아마 DC DC converter 원리인듯?

LiDAR에서, 레이저가 더 빠르게 발사될수록 liDAR의 resolution이 올라갈 수 있다.
GaN소자를 쓰면 Si소자보다 더 빠르게 레이저를 발사할 수 있다.


GaN 소자는 우주에서도 쓰인다.
GaN은 선천적으로 radiation tolerant하다.

Si에서는 radiation을 막으려면 특별한 fabrication 방식, 특별한 packaging 방식이 필요하다.
GaN은 그딴거 필요 없다.

그래서 space application에 아주 적합하다.


GaN은 medical application에 많이 쓰인다.
무선 전력 전송으로 몸 안의 장비를 충전해야 하는 경우가 있다. 여기에 GaN이 쓰인다.

heart pump, pain scintillators 등.
wire로 충전하면 몸에 구멍을 내야 하니 안좋다. 감염 위험도 있다.

MRI에서도 더 높은 해상도를 얻기 위해 GaN을 쓴다. 10~100배 높은 해상도를 얻을 수 있다.

Si MOSFET에서 높은 전력밀도를 쓰려면 비싼 냉각시스템을 써야 했다.

GaN은 microinverter나, 분리된 MPPT/optimizer에 적합하다.

ESS:
GaN을 쓰면 더 작고 더 낮은 전압을 쓰는 소자를 쓸 수 있다.
이러면 dV/dt가 줄어들고, equivalent output frequency가 늘어나고,
결과적으로 더 높은 효율과 밀도를 제공하고
열 발생을 낮춰 cooling 부담을 덜고 소자들에 들어가는 stress를 줄여 lifetime을 늘린다.

Solar Optimizer:
이게 뭔지는 좀 알아보긴 해야 할듯
여기에도 쓰인다.

dToF는 time difference, iToF는 phase difference
이거 추가해놓자

GaN FET, IC들은 극히 작은 pulse width를 갖는 high-current pulse를 만들 수 있다.
그 덕분에 해상도가 높아지고, 측정가능거리가 길어질 수 있다.


https://epc-co.com/epc/about-epc/gan-talk-blog/post/17602/egan-vs-silicon
https://epc-co.com/epc/design-support/application-notes/an003-using-enhancement-mode
https://www.electronicdesign.com/technologies/power/article/21807592/the-great-semi-debate-sic-or-gan