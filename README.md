# Embedded_daily_study (20.08.25 ~)
<br>

:pushpin: **20.08.25**

#### LPF
- Low Pass Filter
- 저주파 전류만 통과하도록 만든 필터 → capacitor를 이용
- capacitor는 고주파(AC)의 입장에서는 저항이 작게 느껴지고, 저주파(DC)의 입장에서는 저항이 크게 느껴짐
- 따라서, capacitor를 회로에 넣어서 고주파만 흐르도록 해서 GND로 버림

#### HPF
- High Pass Filter
- 고주파 전류만 통과하도록 만든 필터 → inductor를 이용
- inductor는 저주파(DC)만 통과할 수 있음
- 따라서, DC 전류만 흐르도록 해서 필터링함

#### Transistor
- Trans-resistor
- 저항을 조절해서 전류를 조절 → 목적은 전류를 제어하는 것!
- npn, pnp 타입이 있음
- Base, Controller, Emitter → base 부분은 switch가 존재

#### pull-up, pull-down
- 사람의 손 접촉 또는 정전기 등으로 칩에 의도치 않은 전압이 인가되는 상황이 발생하면 원하지 않는 결과를 가질 수 있음. → 이래서 필요한 것
- pull-up : default 상태로 high 값을 주도록 회로 구성 → 주로 low active 일 때 사용함
- pull-down : default 상태로 low 값을 주도록 회로 구성 → 주로 high active 일 때 사용함

#### Register
- 1bit 단위로 정보를 저장하는 기억 소자
- 고액, 빠른 속도로 cpu 내에서 cache 용도로 사용함. → 하지만, cpu 외부에서도 사용할 수 있음
- flip-flop으로 구성되고, 1개의 flip-flop은 1bit 정보를 저장함
- 따라서, n-bits register이라고 하면 n개의 flip-flop으로 구성된 것

#### Flip-Flop
- flip-flop은 latch의 일종임 → 1bit 단위로 정보 저장
- level trigger : write의 0, 1 값을 기준으로 flip-flop이 데이터를 update함. → latch

    → write가 High로 올라가 있는 동안 입력된 Data In 값을 저장하고 있음.

    → 클록 동기화 X

- edge trigger : clock이 0에서 1 또는 1에서 0으로 값이 바뀔 때 데이터를 update함. → flip-flop

    → 클록 동기화 O
