---
layout: post
title:  "Analog - Amplifier Class"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 3
---

Amplifier에서는 linearity, signal gain, efficiency, power output 등을 생각해줘야 한다.
다른 특성을 갖는 amplifier들을 구분하기 위해, amplifier class를 사용한다.

amplifier 분류는:
High linearity, low efficiency amplifer와
Low linearity, high efficiency amplifer 사이를 구분해놓은거다.
그니까 linearity가 높으면 efficiency가 낮다는 뜻이고,
각 특성을 얼마나 높게 설정했는지에 따라 class가 구분된다.

Amplifier class들은 크게 2가지로 구분될 수 있다.
A, B, AB, C : Output stage TR들이 완전히 켜짐과 꺼짐의 중간 상태에서 동작한다.

D, E, F, G, S, T 등: Output stage TR들이 switching operation을 해서 껐다 켜진다.
즉, saturation region 갔다가 cutoff region 갔다가를 반복하며 PWM(Pulse Width Modulation) 동작을 한다.

Class A Amplifier:
Class A amplifier는 output switching transistor 하나만 있으면 되기 때문에 많이 쓰인다.
여기 쓰이는 output transistor는 Q-point(operating point)에 bias되어 있어서, cutoff region이나 saturation region으로 날아가버리지 않는다.
그래서 전압 위상에 관계없이 전류를 잘 출력할 수 있다는 장점이 있다.

단점은, 항상 켜져있어서 전류 소모가 계속 일어난ㄷ는 점이다.

class A amplifier는 gain이 크고, distortion이 적고, linearity가 훌륭하다.
그래서 high-fidelity audio amplifier 설계에 많이 쓰인다.
하지만 thermal power supply consideration 때문에 high power에서는 잘 안쓰인다.

class A amplifier는 linear region에서 동작해야 하기 때문에, DC biasing voltage가 잘 인가되어야 한다.
안그러면 동작이 이상해질 수도 있고, distortion이 생길 수도 있다.

근데, output transistor가 항상 켜져있기 때문에, 항상 전류가 흐르고 있는 상태다.
그래서 지속적인 열손실이 발생하고, 효율이 30%정도밖에 안된다.
그래서 high power amplification에서는 이런 구조를 못쓴다. 손실도 많고 뜨거워지니까.

Class B amplifier:
input signal이 positive일 때는 위쪽 트랜지스터만, negative일 때는 아래쪽 트랜지스터만 켜지는 구조다.
여기서는 이 구조를 push-pull 구조라고 부른다.

당연히 class A amplifier보다는 효율이 높은 구조지만, 새로운 문제가 또 생긴다.
입력 전압이 -0.7V~0.7V동안은 위아래 트랜지스터가 둘 다 꺼져서 출력이 안나온다.

이거때문에 zero-crossing distortion(Crossover distortion이라고도 한다)이 생겨서,
class B amplifier는 audio amplifier같은 곳에 못쓴다.

Class AB amplifier:
이름에서 보이듯, Class A랑 Class B를 합친 구조다.
audio power amplifier design에서 많이 쓰이는 구조다.

class B를 조금 변형한 구조인데, crossover point에서 두 트랜지스터가 꺼지지 않고 켜져있는 구조다.

여기 들어가는 트랜지스터들은 걸려있는 bias voltage가 아주 작다. cutoff point보다 아주 조금 높은 전압이다.
이렇게 되면 트랜지스터가 조금 더 오래 켜져있다. half cycle보다 조금 더 길게 켜져있다.

Class B는 half cycle보다 짧게, Class A는 항상 켜져있으니 그 사이에 있다는 의미로 class AB라 한다.
하여간, half cycle보다 길게 켜져있기에, crossover distortion이 일어나지 않는다.
efficiency는 50~60% 정도다.

Class C amplifier:
Class C amplifer는 효율이 꽤 높지만, linearity가 많이 떨어진다.
Class A, AB, B는 linear amplifier로 분류되지만, C는 그렇지 못한다.

Class C amplifier는 절반도 훨씬 안되게, 90도 정도만 켜진다.
그래서 효율은 80%정도 되긴 하는데, 엄청난 distortion이 생긴다.
Sine wave가 들어오면 머리만 참수해서 내보내는 수준이니까.

그래서, class C amplifier는 high frequency sine wave oscillator나 RF amplifier에 쓰인다.
고주파에서는 amplifier에 의해 발생한 current가 LC resonance circuit에 의해 특정 주파수의 sine wave로 바뀔 수 있기 때문이다.

class D~T는 switching operation을 한디.