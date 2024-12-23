---
layout: post
title:  "Digital - CPU"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 5
---

CPU: Central Processing Unit<br>




ISA: Instruction Set Architecture<br>
<br>
ISA는 CPU에서 사용되는 명령어들의 집합을 말한다.<br>
정상적인 CPU 동작을 위해서는 그 CPU에 맞는 ISA를 사용해야 한다.<br>
<br>
ISA는 크게 RISC 계열과 CISC 계열이 있다.<br>
ARM CPU는 RISC, x86-64 CPU는 CISC 계열 ISA를 사용한다.<br>
<br>
RISC ISA는 명령어 수를 최소화하고, 명령어 크기를 고정한 ISA다.<br>
각 명령어들의 동작을 최적화해 효율을 높인다.<br>
<br>
CISC ISA는 여러 명령어들을 묶은 복합 명령어를 많이 갖고 있는 ISA다.<br>
그래서 한 개 명령어로 구현할 수 있는 동작이 많다.<br>
<br>
<br>
RISC CPU
명령어 수 적음
명령어 크기 고정
1개 명령어 처리속도 빠름
프로그래밍 코드 복잡


CISC CPU
명령어 수 많음
명령어 크기 명령어마다 다름
1개 명령어 처리속도 명령어마다 다름
프로그래밍코드 단순



왜 cisc는 명령어마다 길이가 다르냐?
여러 명령들을 묶어서 만든 복합 명령들이 많아서 그렇다

Risc는 명령 크기를 16비트, 32비트 이런식으로 고정해둔다

처리 속도:
Risc는 명령어마다 1클럭 또는 2클럭 안에 끝내게 되어 있다
Cisc는 명령어마다 다르다. 복합 명령들이 읶으니까

프로그래밍 편의:
Cisc에서 모든 명령을 다 숙지하고 있다면, 딱 적합한 명령어를 써서 프로그래밍을 단순하게 할 수 있다

근데 그렇게 되는거 자체거 힘든 일이라, 꼭 cisc가 risc보다 프로그래밍이 쉽다고는 할 수 없다



Intel SGX, AMD TrustZone:

CPU: 명령어를 수행하는 역할
OS: 어떤 시스템이 언제 수행될지 순서, 스케줄링을 해주는 역할

그래서, 사실 CPU는 OS가 없어도 동작할 수 있다.
명령어랑 메모리만 주어지면 동작한다.

OS로부터 분리된 Enclave라는 곳에 메모리, 명령어를 넣어두면
OS가 해킹당해도 CPU가 Enclave에 적힌대로 동작할 수 있다.


데이터는 SSD에 저장되지만, SSD는 CPU에 비해 너무 느리다.
그래서 데이터를 RAM에 담아두고, CPU는 RAM과 소통한다.

컴퓨터 내 메모리는 SSD, RAM, Cache, Register가 있다.
오른쪽으로 갈수록 빠르고, 비싸고, 용량이 작다.

Register는 CPU 내에서 데이터를 잠깐 저장하는 장치다. 얘가 제일 빠르다.

Cache메모리에는 L1 L2 L3이 있다 (Level의 L)
L1이 제일 빠르고 용량이 작다.

CPU는 필요한 데이터를 L1 L2 L3 RAM 순으로 찾는다
속도가 빠른 메모리부터 찾아보는 순서다

CPU가 메모리에서 데이터를 읽어올 때,
16비트면 메모리에서 한번에 16비트, 32비트면 한번에 32비트 데이터를 읽어온다.

CPU의 각 process를 thread라 부른다.
속도를 높이고 싶다면 core 하나에서 여러개 thread를 실행시키면 될 것이다.
가능하다면, core 수를 늘려도 CPU 속도가 빨라질 것이다.