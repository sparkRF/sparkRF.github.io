---
layout: post
title:  "Analog - ESD"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 3
---

ESD = Electrostatic Discharge<br>
<br>
사람은 정전기를 만나면 따끔한 정도지만,<br>
IC는 정전기의 높은 전압때문에 문제가 생길 수도 있다.<br>
<br>
그래서 IC에 ESD cell 회로를 넣어 정전기의 영향을 막고,<br>
ESD test로 IC가 정전기에 버틸 수 있는지 테스트한다.<br>
<br>
<br>
ESD test에서는 정전기 전압을 모델링한 ESD Model을 사용한다.<br>
<br>
ESD Model:<br>
HBM(Human Body Model): 인체에 의한 정전기를 표현한 모델<br>
MM (Machine Model): 기계에 의한 정전기를 표현한 모델<br>
CDM(Charged Device Model): 공기 중 전하에 의한 정전기를 표현한 모델<br>
<br>