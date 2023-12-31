---
layout: post
title:  "EMMI"
date:   2023-10-04 19:31:29 +0900
categories: Circuits
order: 1
---

Leakage current가 많이 나올 때는 EMMI라는 장치로 IC를 살펴봐야 한다.<br>
EMMI: Emission Microscope<br>
<br>
EMMI로 IC를 분석해보려면, 일단 위쪽 패키징을 없애야 한다. 이렇게 패키징 없애는걸 decap이라 한다. Decapsulation인 듯 하다.<br>
<br>
패키징 종류는 그림이랑 같이.<br>
<br>
DW7601에서 사용한건 QFN이었다. 이 패키징의 윗면을 화학약품을 쓰든 Decap장비를 쓰단 해서 없애고 EMMI로 IC를 관찰한다.<br>
EMMI를 쓰는 경우는 원인이 뭐든간에 IC에 불량이 있는 경우다. 그래서 EMMI를 쓸 때는 IC에 전원도 넣고 필요한 벡터도 넣어서 고장 현상을 재현한다. 그러면 불량 위치에서 비정상적인 열이나 빛이 나오고, EMMI는 이걸 보는거다.<br>
<br>
그래서 측정 전에 decap을 해줘야 한다. 안그러면 안보인다.<br>
<br>
열을 보는 EMMI는 THEMOS(Thermal Emission Microscope Operating System)이라 하고 THEMOS는 InGaAs 카메라를 쓴다.<br>
<br>
빛을 보는 EMMI는 PHEMOS(Photon Emission Microscope Operating System)이라 하고, PHEMOS는 InSb 카메라를 쓴다.<br>
<br>
그리고 OBIRCH(Optical Beam Induced Resistance Change)라는 방식도 있다. OBIRCH는 LSM(Laser Scanning Microscope)을 쓴다.<br>
<br>
OBRICH는 Seebeck effect(제벡 효과)를 이용한 방식이다. Seebeck effect는 서로 다른 두 종류의 금속을 붙여놓고 한쪽에 열을 가하면 전류가 흐르는 현상이다. 기전력이 발생한다고 봐도 된다. 그래서, OBRICH는 레이저를 쏴서 특정 부분을 가열하고 기전력이 생기는지 확인한다.<br>
<br>
만약 가열했을 때 기전력이 생긴다면, 그 위치에는 서로 다른 금속이 붙어있는 것이니, 거기서 불량이 생겼다는 것을 알 수 있다.<br>
<br>
정밀한건 OBIRCH > PHEMOS > THEMOS인데, OBIRCH는 제약 사항이 좀 많다. 그리고 PHEMOS는 빛을 보는 거라 암실에서 진행되어야 한다. THEMOS는 상관 없다.<br>
<br>
THEMOS: 주로 Metal 관련 불량이 잘 보인다. 열이 나는 원리가 I^2R이니까, metal에 흐르는 전류에 의해 열이 생기기 때문이다. 대표적인 불량으로는 Metal melting, Bridge short, oxide crack, metal particle, migration, contact spike등이 있다.<br>
<br>
열은 InSb 카메라로만 검출할 수 있어서 THEMOS가 InSb 카메라를 쓴다. IC에 전원이랑 신호 넣기 전에 한번 찍고, 전원이랑 신호 넣은 후 찍어서 비교적 뜨거워진 곳을 고장 위치로 판정한다.<br>
<br>
PHEMOS: 주로 gate 관련 불량이 잘 보인다. Photon은 Si layer에서 나온다. 대표적인 불량으로는 Source to Drain leakage, gate leakage, oxidation breakdown, ESD failure, hot carrier, latch-up 등이 있다.<br>
<br>
Photon 검출은 InGaAs 카메라를 이용한다. 이때, photon을 검출해야 하니 외부 빛을 모두 차단한 암실에서 사용한다. 그리고 photon은 트랜지스터가 스위칭될 때 방출되기도 하기 때문에, 정상 sample 한번 찍어보고 이상한 sample 한번 찍어서 비교해야 한다.<br>
<br>