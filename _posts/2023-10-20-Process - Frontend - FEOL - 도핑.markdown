---
layout: post
title:  "Frontend - FEOL - Doping"
date:   2023-10-04 19:31:29 +0900
categories: Process
order: 2
---

웨이퍼에 적절한 불순물을 섞어넣어 전기적 특성을 바꾸는 공정을 Doping(도핑) 공정이라 부른다.


먼저, 소자가 들어갈 웨이퍼 영역을 정한다.
이 영역을 active region이라 부른다.
Active region이 정해지면, 도핑을 통해 active region에 Well과 Diffusion을 만들게 된다.

Well과 diffusion의 차이는, well이 더 

웨이퍼를 사용할 때에는, 먼저 웨이퍼 어디에 어떤 소자가 만들어질지 정한다.<br>
소자가 형성되는 영역을 Active Region이라 부른다.<br>
Active Region이 정해지면, 도핑을 통해 필요한 곳에 Well을 만들게 된다.<br>
<br>
P-Epi 웨이퍼를 사용할 때에는 PMOS가 만들어질 곳에 N-Well을 만들어줘야 하고,<br>
N-Epi 웨이퍼를 사용할 때에는 NMOS가 만들어질 곳에 P-Well을 만들어줘야 한다.<br>
<br>
<br>
Epi에 Well을 만들기 위해서는, Epi를 도핑해야 한다.
그러기 위해서, Well이 생겨야 하는 위치의 oxide를 제거할 필요가 있다.
Oxide를 제거한 틈으로 이온을 쏴서 도핑을 하게 된다.

일단 웨이퍼 전체에 photoresist를 뿌린다. 세로로 Epi - Oxide - Photoresist 구조가 된다.
이제 mask로 oxide를 제거해야 하는 부분을 표시하고, oxide를 제거한다.
그러면 그 위에는 아무것도 없고, 틈이 아닌 곳에는 oxide + photoresist가 있다. etch했으니까.
그리고 여기다가 이온을 쏴서 도핑한다.



ion을 때려박은 뒤에는 가열해서 ion이 안쪽까지 diffusion되어 들어가게 한다.
(Well Drive In)
이렇게 하면 위쪽에도 oxide가 다시 생긴다. 가열했으니까.
일단 도핑 방법중 하나가 'Ion implantation'이다.<br>
말 그대로 이온을 가속해서 웨이퍼에다가 때려박아 필요한 부분을 도핑하는 방식이다.<br>
근데, Ion implantation에는 두가지 문제가 있다.<br>
<br>
1\. Channeling Effect<br>
쏘다보면 특정 부분만 이온이 깊게 들어갈 수도 있다.<br>
그래서 웨이퍼를 다양한 방향으로 기울이거나 회전시켜 이온이 골고루 박히도록 해야 한다.<br>
<br>
2\. Annealing<br>
웨이퍼에 이온들을 쏘다보면 웨이퍼 표면이 울퉁불퉁해진다.<br>
철판에 총쏘면 철판이 울퉁불퉁해지는거랑 같은 이치다.<br>
후속 열처리 과정을 통해 표면을 복구해줘야 하는데, 이 복구 과정을 Annealing이라 부른다.<br>
<br>
Ion Implant는 이런 단점들을 갖고 있음에도 널리 쓰인다.<br>
왜냐하면, 이온을 몇개나 써서 도핑할지 내 맘대로 정할 수 있기 때문이다.<br>
<br>
이런 문제도 발생하긴 한다.<br>
원래는 SiO2가 이온들을 다 막아줘야 하지만, SiO2는 비정질(Amorphous Solid)라서 원자 배열에 규칙이 없고,<br>
그래서 이온들이 중간중간 있는 빈칸들에 들어가버리는 경우가 생긴다. 이 현상을 '트랩'이라 부른다.<br>
근데 이 트랩은 Annealing을 하면 다 없어진다.<br>
<br>
Ion implantation 말고 Solid State Diffusion이라는 방법도 있다.<br>
이건 도체 표면에 dopant를 올려놓고, 웨이퍼로 확산되기를 기다려서 도핑하는 방식이다.<br>
이때, 다른 곳에는 SiO2가 깔려있기 때문에 dopant가 이상한 곳으로 들어가지 못한다.<br>
<br>
이 방식은 diffusion 기반이니까, 오래 diffusion시킬수록 dopant가 더 깊이 들어간다.<br>
하지만 너무 깊이 들어가버리면 parasitic capacitance가 생겨버릴 수 있다.<br>



이렇게 하면 Si에 Well이 생긴 상태가 되고, 그 위도 oxide로 덮여 있다.


이온주입/열처리

이온주입법이 없을 때에는, 불순물을 웨이퍼 위에 올려놓고 웨이퍼로 확산되기를 기다렸다
근데 이러면 오래걸리고, 특정 영역만 n형 p형으로 만들기가 어렵다.

확산은 태양전지에서는 지금도 쓴다.

이온주입은 이온을 때려박는거다.
이후에는 결정회복을 위한 열처리가 필요하다.

이온주입을 할때는, 이온주입할곳만 남겨놓고 나머지 영역은 포토레지스트로 가려놓는다.
이온주입 한 뒤에는 포토레지스트 다 지우고 열처리한다

레지스트가 열에 견디지 못할 경우에는 hard mask(실리콘 산화막+질화막)을 쓴다. 이때도 패턴은 리소그래피+에칭을 활용한다.

이온주입을 대체하는 기술로은 플라스마 도핑, 레이저 도핑이 연구되고 있다.
플라스마 도핑은 웨이퍼 옆면에도 도핑이 돼서, 트랜지스터가 3차원이 되면 쓰일수도 있다.
레이저 도핑은 실리콘을 녹이면서 도핑을 하기 때문에, 열처리를 따로 해줄 필오가 없다

단결정 실리콘에 이온주입이 되면,
실리콘 격자와 이온의 충돌로 실리콘 원자가 흐트러져 있다. 주입된 이온도 격자에 맞게 배치 안되고 이상한 곳에 가 있다. 그래서 이걸 가열해서 격자를 다시 만들어준다



Well Proximity Effect:<br>
앞에서 말했던 내용들 중 웨이퍼에 well을 만드는 내용이 있었다. Substrate 위에 well을 만들 곳을 정해놓고, 그 외 영역을 photoresist로 덮어버린 후 이온을 쏴서 도핑하는 방식이었다.<br>
<br>
근데 이러면 문제가, 끄트머리에서 튕겨나온 이온들 때문에 well의 가장자리는 원래 의도했던 수치보다 더 높게 도핑된다.<br>
<br>
그래서 well 끄트머리에 설치된 MOSFET과 안쪽에 설치된 MOSFET은 다르게 동작할 수 있다. Well의 Doping 농도가 다르기 때문이다.<br>
<br>
이 문제를 해결하기 위해, layout 만들때 Well 영역을 일부러 조금 더 길게 잡을수도 있고, Dummy Transistor를 가장자리에 끼워서 해당 효과를 피할 수도 있다.<br>
<br>
근데, 그냥 중요한 MOSFET이면 가장자리에서 멀리 떼어놓는게 좋다.<br>

https://kor-razavai.tistory.com/29

웨이퍼 제조사들은 웨이퍼가 완성되면 표면에 산화막을 만들어서 고객사에게 보낸다.<br>
고객사는 산화막을 갈아버리고, 새로 위에 산화막 씌울 준비를 한다.<br>


그렇게 보관하다가, 이제 무슨 패턴 그려야 할지 정해지면 그걸 들고 온다.
P-Epi면 N-Well, N-Epi면 P-Well을 만들어야 할 것이다.

N-Well, P-Well이 생겨야 하는 위치에 oxide를 etch해서 틈을 만든다.
틈 위에는 아무것도 없고, 틈이 아닌 곳에는 oxide + photoresist가 있다. etch했으니까.
그리고 거기다가 ion을 때려박는다.

ion을 때려박은 뒤에는 가열해서 ion이 안쪽까지 diffusion되어 들어가게 한다.
(Well Drive In)
이렇게 하면 위쪽에도 oxide가 다시 생긴다. 가열했으니까.

이렇게 하면 Si에 Well이 생긴 상태가 되고, 그 위도 oxide로 덮여 있다.

이렇게 만들어진 Well은 counterdoping으로 만들어진거다.
그래서, Well 안은 dopant concentration이 높고,
그래서 majority carrier의 mobility가 조금 떨어진다.

그래서 Well에 올라가야 하는 소자는 성능이 조금 떨어지게 된다.
P-Epi를 쓰면 N-Well을 만들고 거기에 PMOS를 올리게 된다.
그래서 PMOS의 성능을 조금 희생해 NMOS 성능을 최대화한 상황이 된다.

N-Epi를 쓰면 반대로, P-well을 만들고 거기에 NMOS를 올리게 된다.
이때는 NMOS의 성능을 조금 희생해 PMOS 성능을 최대화한거다.

근데, 그래도 NMOS가 더 빠르다. 전자 mobility가 hole mobility보다 애초에 크기 때문이다.

N-well process에서는 p-sub를 ground에 박아야 하고, P-well process에서는 N-sub를 최대한 높은 전압에 꽂아야 한다. 보통 circuit designer들은 ground에 꽂는걸 선호한다. Multiple power supply를 쓰면 가장 높은 전압에 연결하기 어렵다.

Field oxide는 두꺼워야 한다. Field oxide의 threshold voltage는 커야 하기도 하고, 커다래야 금속과 그 아래 silicon 사이의 parasitic capacitance가 작다.

CMOS process는 선택적으로 field oxide를 만들고, active device가 만들어질 영역에는 얇은 pad oxide만 남기기 위해 LOCOS technology를 쓴다.(이 기술은 bird’s beak 현상 등 문제로 지금은 DTI로 대체된걸로 알고 있다)
Field oxide가 생길 영역을 field region, 안생길 영역을 moat region이라 부른다.

LOCOS process는 일단 웨이퍼 전체에 nitride를 deposit한다.
그리고 inverse moat mask를 가져와서 nitride에 패턴을 그린다
그다음 selective etch로 field region에서 nitride를 제거한다.

LOCOS에 쓰이는 nitride layer는 pad oxide 위에 생겨야 한다. 그냥 Silicon 위에 바로 만들면 nitride growth때문에 mechanical stress가 들어가고, silicon lattice가 움직일 수 있다(dislocation)
Pad oxide가 nitride 영향으로부터 Si를 보호해준다

근데, 이 thick field주변에 생기는 thick-field transistor의 threshold voltage가 최대 동작 전압보다 확실하게 높아야 할 것이다. 안그러면 제대로 분리가 안됐다고 봐야겠지. 거기서 막 동작이 일어날텐데

그래서, 여기 threshold voltage 더 높여주기 위해서, P-epi의 field region에 p-type channel stop implant를 한다. N-well field region에는 N-type channel stop implant를 한다.
Channel stop에는 다양한 방법들이 있는데, 여기서는 blanket boron implant 후 patterned phosphorus implant를 하는 방법을 쓴다.
Boron implant는 LOCOS nitride 만들고 남은 photoresist를 쓴다.
지금 상황은 웨이퍼 위에 pad oxide가 있고, 그 위 nitride가 남아잇는 moat region과 nitride가 없는 field region이 있는 상황이다. 그리고 moat region의 nitride 위에는 photoresist가 남아있다.
그래서, photoresist가 없는 곳에 전부 blanket boron implant를 한다. 이렇게 하면 epi region의 thick-field threshold가 올라간다.
그 다음에는 웨이퍼 전체를 photoresist로 덮는다.
아까 남아있던 photoresist가 남아있어도 상관 없다. 어차피 moat region은 안건드릴거다.
그다음에 웨이퍼에 다시 패턴을 그린다. Channel stop mask를 이용한다.
이걸 하고 나면 N-well field region만 노출되게 된다.
그럼 거기에 phosphorus를 implant한다. 이게 앞서 implant된 blanket boron을 counterdope해서 NMOS thick-field threshold를 끌어올린다. 이렇게 해서 thick-field threshold가 모두 최대 동작 전압을 넘어가도록 한다.
그 다음에는 photoresist를 전부 제거한다. 







그런데, 웨이퍼에 n-well과 p-well을 깔다보면 웨이퍼에 pn junction이 생긴다.<br>
의도하지 않은 pn junction에 의해 원하지 않은 전류가 흐를 수 있다.<br>
그래서, 절연체를 통해 두 영역을 isolation해줘야 한다.<br>


Isolation:
Isolation에는 LOCOS, STI, DTI가 있다.


LOCOS(Local Oxidation of Silicon):
옛날에는 LOCOS(Local Oxidation of Silicon)라고 해서, n영역 p영역 사이에 SiO2를 대충 끼워넣었다.<br>
그랬더니 SiO2가 양 옆을 밀어내며 gate electrode 아래까지 밀고 들어오는 현상이 발생했다.<br>
이렇게 되면 MOSFET의 채널에 영향을 주게 된다.<br>
이 현상을 bird's beak 현상이라 부른다. SiO2가 옆을 밀어내는 모양이 새 부리같이 생겨서 그렇다.<br>


STI(Shallow Trench Isolation):
그래서, LOCOS 대신 STI(Shallow Trench Isolation) 공정을 사용하기 시작했다.<br>
Trench를 파고, 그 안에 SiO2를 집어넣어 pn junction을 방지하는 방식이다.<br>
<br>
LOCOS보다는 낫지만, 그래도 STI를 쓴다고 해서 SiO2가 양 옆을 아예 안밀어내는건 아니다.<br>
STI의 SiO2에 의해 반도체 영역이 stress를 받는걸 STI stress effect라 한다.<br>
STI stress에 의한 영향을 방지하려면, active region을 더미로라도 꽉 채워놓아야 한다.
STI stress effect는 모델링하는 파운드리 회사도 있고, 그렇지 않은 파운드리 회사도 있다.<br>
<br>
STI 공정을 쓰면 chip size를 작게 할 수 있다.<br>
원래 PN junction을 분리하려면 거리가 필요했는데, STI로 isolation을 하면 거리 없이도 isolation을 할 수 있다.<br>
결과적으로, 회로의 집적도를 높일 수 있다.<br>
<br>
STI Stress를 고려해서, layout시 바깥쪽에 source가 가도록 한다. 또는 양쪽 끝에 dummy transistor를 넣는다. Finger로 구성할 때 이야기고, N은 Vss 쪽으로, P는 VDD쪽으로 갈 가능성이 높아서 그렇다. 고 하는데 무슨 뜻인지는 알아봐야 한다.<br>


DTI(Deep Trench Isolation):
DTI는 STI보다 훨씬 깊게 파는 공정인데, 옆 소자와 분리돼야 SNR이 증가하는 이미지 센서 등에 사용된다.
삼성전자에서는 이미지 센서에서 Cell들을 분리하는 기술은 ‘ISOCELL’ 기술이라 불린다. Isolation + Cell<br>


Well Proximity Effect:<br>
앞에서 말했던 내용들 중 웨이퍼에 well을 만드는 내용이 있었다. Substrate 위에 well을 만들 곳을 정해놓고, 그 외 영역을 photoresist로 덮어버린 후 이온을 쏴서 도핑하는 방식이었다.<br>
<br>
근데 이러면 문제가, 끄트머리에서 튕겨나온 이온들 때문에 well의 가장자리는 원래 의도했던 수치보다 더 높게 도핑된다.<br>
<br>
그래서 well 끄트머리에 설치된 MOSFET과 안쪽에 설치된 MOSFET은 다르게 동작할 수 있다. Well의 Doping 농도가 다르기 때문이다.<br>
<br>
이 문제를 해결하기 위해, layout 만들때 Well 영역을 일부러 조금 더 길게 잡을수도 있고, Dummy Transistor를 가장자리에 끼워서 해당 효과를 피할 수도 있다.<br>
<br>
근데, 그냥 중요한 MOSFET이면 가장자리에서 멀리 떼어놓는게 좋다.<br>

https://kor-razavai.tistory.com/29



WPE:
Nwell을 형성하기 위해 ion implant를 할 떄,
photoresist 없는 영역에는 이온이 박히고,
photoresist 있는 영역은 photoresist에 막혀서 이온이 안 박힌다.

이때, 일부 이온이 photoresist에 튕겨져 나와 well에 들어간다.
그 결과, well의 edge 부분에는 더 많은 이온이 박혀 doping 농도가 증가한다.

이러면 무슨 문제가 생기냐?
Nwell 위에 PMOS를 만들어야 하는데,
Nwell 농도가 높으면 channel에 hole 모이기 힘들어진다.
그래서 channel이 만들어지기 더 힘들게 되어 Vth가 증가한다.

그니까, well의 edge쪽 트랜지스터들은 원래 의도보다 Vth가 높아지는거다.
이러면 켜지는 전압도 높아지고, 켜졌을때 전류도 줄어든다.

이걸 예방하려면, 소자들은 well edge로부터 멀리 떨어뜨려야 한다.

멀리 떨어뜨리는게 확실해서 좋겠지만,
너무 멀리 떨어뜨리면 소자들을 연결하는 배선이 길어져 metal 저항이 늘어나고, 전체 layout 크기도 늘어나게 된다.

그래서 적당히 떨어뜨려줘야 한다.

Well을 만든 뒤 guardring을 쳐두면 WPE 효과가 거의 안보인다. guardring 두께가 있으니까.

Sheet gate Oxide는 고전압 트랜지스터에서 나타나는 현상인데, 비슷한 현상이다.

