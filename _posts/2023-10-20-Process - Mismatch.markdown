---
layout: post
title:  "Mismatch"
date:   2023-10-04 19:31:29 +0900
categories: Process
order: 14
---

Mistmatch는 lithography, etching, diffusion, implant 등 공정의 결과가 균일하지 못한 현상을 말한다.<br>
직선이 아닌 울퉁불퉁한 선이 그려지는 현상,<br>
Doping이 균일하지 못한 현상 등이 해당된다.<br>
<br>
Mismatch는 모든 소자에 생기는 현상이며, 완전히 방지할 수는 없는 현상이다.<br>
따라서 mismatch의 영향을 최소화하는 설계로 대응하는 것이 최선이다.<br>
<br>
<br>
Mismatch의 영향을 줄이는 두가지 설계 방식이 있다.<br>
<br>
<br>
먼저, 소자 면적을 늘려서 소자 내 mismatch의 비중을 줄일 수 있다.<br>
소자가 넓어지면 울퉁불퉁한 테두리의 영향이 줄어들고,<br>
device length, channel doping, oxide thickness, sheet resistance, capacitance등 소자 특성들의 편차도 줄어든다.<br>
<br>
Mismatch의 영향을 줄이려면 소자를 정사각형으로 Layout하는 것이 가장 좋다.<br>
울퉁불퉁한 테두리를 줄이기 위해 둘레 길이는 짧은 것이 좋고,<br>
소자 특성 편차를 줄이기 위해 면적은 넓은 것이 좋은데,<br>
최소한의 둘레 길이로 최대한의 면적을 가지는 사각형이 정사각형이기 때문이다.<br>
<br>
<br>
또는, Layout을 '섞어서' mismatch의 영향을 줄일 수도 있다.<br>
<br>
웨이퍼는 완전히 평평하지 않기 때문에, 소자를 어디에 배치하느냐에 따라 소자 특성이 변한다.<br>
특성을 균등하게 만들기 위해, 소자를 여러개로 나눠 골고루 배치한다.<br>
<br>
예를 들어 A 소자와 B 소자의 특성을 균등하게 만들고 싶다면,<br>
각 소자를 작은 소자 여러개로 쪼갠 뒤:<br>
<br>
1차원 배치:<br>
ABBA<br>
<br>
2차원 배치:<br>
AB ABBA<br>
BA BAAB<br>
<br>
위 형태로 소자를 배치해 두 소자가 mismatch의 영향을 균등하게 받도록 한다.<br>
<br>
위와 같은 Layout 형태를 Common Centroid 구조라고 부르며,<br>
Layout을 섞는다고 부르기도 한다.<br>
<br>
<br>
Common Centroid 구조 외에도 Layout에서 신경써줘야 하는 사항들이 있다.<br>
<br>
소자를 배치할때는 커다란 소자 하나가 아니라 작은 소자 여러개를 붙여 배치한다.<br>
<br>
같은 전압이 걸려야 하는 곳은 모든 것을 똑같게 해줘야 한다.<br>
배선 길이, parasitic capacitance 등 모두 가능한 한 동일하게 해줘야 한다.<br>
<br>
서로 다른 종류의 소자들은 고르게 배치해봐야 mismatch에 의해 받는 영향이 다르기에 특성이 균등해지지 않는다.<br>
같은 종류의 소자들끼리 모아서, 거리가 멀수록 편차가 커지는 점에 유의해 배치해야 한다.<br>
<br>
<br>
Mismatch를 시뮬레이션에서 확인할 경우, EDA 프로그램의 MonteCarlo Simulation에서 확인할 수 있다.<br>
<br>
<br>
웨이퍼 상태에서는 Mismatch가 없었더라도:<br>
패키징 과정에서는 압력 변화에 의해,<br>
실제 이용시에는 온도 변화에 의해 소자마다 특성이 달라질 수 있다.<br>
<br>
<br>
웨이퍼가 완성되면, 웨이퍼를 잘라서 die를 만들고 그걸 패키징 공정을 통해 포장한다.<br>
이때, 포장된 die는 테두리 부분에서 비교적 높은 압력을 받게 된다.<br>
<br>
Silicon은 Piezoresistive 효과가 있어서, 압력이 높아지면 저항이 늘어난다.<br>
즉 die의 가운데 부분과 가장자리 부분에서의 소자 특성이 달라지게 되는 것이다.<br>
<br>
하지만 각 회로들 크기보다 die 전체의 면적이 훨씬 커서,<br>
둥근 지구가 평평하게 보이듯 각 회로에 주는 영향은 크지 않다.<br>
<br>
<br>
온도는 압력과 달리 문제가 될 수 있다.<br>
<br>
회로가 동작하면, die 내에 뜨거운 곳과 덜 뜨거운 곳이 생기게 된다.<br>
그러면 뜨거운 곳과 덜 뜨거운 곳의 소자 특성이 달라지게 된다.<br>
<br>
이 효과는 Common Centroid 구조로 어느정도 방지할 수 있다.<br>
그만큼 Common Centroid 구조에 신경을 써야 한다.<br>


유전체는 압력을 받아도 크기나 유전율이 별로 안변해서 Capacitance는 압력으로 안변한다.
하지만 저항은 바뀌니까 저항을 신경써주면 된다.