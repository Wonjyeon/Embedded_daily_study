# Embedded_daily_study (20.08.24 ~)
<br>

## :pushpin: 20.08.24

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
<br>

## :pushpin: 20.08.25

#### RAM
- Random Access Memory
- 정보를 기록하고 기록한 정보를 읽거나 수정할 수 있는 메모리
- 전원이 끊어지면 기록된 정보도 지워지는 휘발성 메모리
- 어느 위치에 저장된 데이터든지 접근하는데 걸리는 시간이 동일함
- 램에 저장되어 있는 데이터는 컴퓨터가 작동하는 동안에만 유지되며, 컴퓨터의 전원이 꺼지면 램에 있는 데이터는 사라짐.
- 따라서, 주로 컴퓨터의 주기억장치, 응용 프로그램의 일시적 로딩, 데이터의 일시적 저장에 사용됨.
- 종류 : SRAM, DRAM (모두 반도체)

#### SRAM

- Static Random Access Memory
- 전원이 공급되는 한 데이터가 지워지지 않는다. (전원이 끊기면 사라지는 휘발성 메모리)
- DRAM보다 빠르고 비싸다
- 각 cell은 6개의 트랜지스터로 one bit를 저장함
- cache 메모리에 사용됨

#### DRAM

- Dynamic Random Access Memory
- 용량이 크고 속도가 빠르기 때문에 컴퓨터의 주력 메모리로 사용하는 램 (메인메모리)
- D램은 전원이 차단될 경우 저장된 데이터가 소멸하는 휘발성 기억소자
- 시간이 지나면서 축적된 전하가 감소되기 때문에 전원이 차단되지 않더라도 저장된 데이터가 자연히 소멸된다는 단점이 있음
- 따라서, 일정 시간마다 데이터를 유지해주는 기능인 리프레시가 필요
- D램은 정보를 저장하는 방인 셀을 가지는데, 메모리셀은 트랜지스터와 커패시터 각각 1개로 구성됨 (고밀도 집적에 유리)
- 커패시터에 전하를 축적함

#### ROM

- Read Only Memory
- 한 번 기록된 정보를 읽을 수만 있고 수정할 수 없는 메모리
- 고정 기억 장치
- 전원이 공급되지 않아도 기록된 정보가 지워지지 않는 비휘발성 메모리
- `Mask ROM`

    : 가장 기본적인 ROM. 제조과정에서 미리 내용을 기록해 논 메모리로, 사용자가 내용을 수정할 수 없음.

- `PROM`

    : 사용자가 한 번 기록할 수 있는 ROM

- `EPROM`

    : 필요 시 기억된 내용을 지우고 다른 내용으로 기록할 수 있음.

    (UVEPROM : 강한 자외선으로 데이터 삭제 / EEPROM : 전기로 데이터 삭제)

- HDD(Hard disk drive) : 반도체 아님. 자기디스크 / SSD(Solid state drive) : 반도체

#### Flash Memory

- ROM의 일종이나 특별한 control 과정을 거치면 지울 수도 있고 그 위에 다시 쓸 수도 있음
- upgrade에도 유리하고 심지어 지울 수 있는 기능 때문에 file system storage로도 사용됨
- NOR > NAND (가격)
- NAND, NOR 관계 없이 block 단위로만 지울 수 있음
- NAND는 32 or 64개의 page로 이루어져 있고, NOR도 128KB 단위의 block 단위를 가짐
- NAND나 NOR의 erase는 0으로 지우는 것이 아니라, charging을 하는 경우라서 지우고 난 block은 모두 1로 채워져 있음 → 16진수로 보면 0xFF로 가득 차 있음.

#### NOR Flash Memory

- cell이 병렬로 연결되어 있음 → address line과 data line을 모두 가질 수 있음

    → RAM처럼 byte 단위로 Random Access가 가능함 → XIP를 지원함.

    → software를 메모리에 로드하여 실행하는 대신 플래시에서 직접 수행 가능 (XIP)

- XIP : word 단위의 access가 가능하여 software를 실행할 수 있는 것
- 쓰기와 지우기는 느리지만 읽기가 빠름
- 코드 저장용이라는 말이 쓰이기도 함

#### NAND Flash Memory

- cell이 직렬로 연결되어 있음 → 작은 단위로는 읽을 수 없고, 한 번 읽을 때 1page 단위로만 읽을 수 있음
- small page를 지원하는 NAND는 512 byte 크기로만 읽을 수 있고, large page를 지원하는 NAND는 2KB씩 한 번에 읽을 수 있음
- 읽기는 느리지만 쓰기와 저장이 빠름
- 대용량 저장이 가능
- 데이터 저장용이라는 말이 쓰이기도 함

#### MCP

- Multi Chip Package
- 플래쉬 메모리 + RAM

#### LSI

- Large Scale Integrated circuit
- 대규모 집적 회로.
- 일반 IC보다 집적도를 한층 높여 한 개의 IC 속에 수천에서 수천만 개가 넘는 트랜지스터 등을 집적시킨 것.
- 컴퓨터의 CPU 또는 대규모 메모리 등이 대표적이다
- 아날로그용 IC로는 거의 만들어지지 않고 대부분 디지털용으로 만들어진다고 할 수 있음
- 디지털 기재를 만들 경우 대량 생산한다면 개별 IC로 만드는 것 보다 그 기재 전용 LSI를 개발하는 편이 가격 면에서 저렴
- 따라서 신기종마다 새로운 LSI를 개발하는 경향이 있음

#### CPU

- Central Processing Unit

#### MPU

- Micro Processing Unit
- 컴퓨터의 CPU를 LSI화한 것으로 레지스터, 연산회로, 제어회로를 내포 명령을 해독하여 연산, 제어 동작을 실행하는 연산 장치
- 마이크로프로세서는 일반적으로 MPU로 불려지며 한 개의 LSI로 집적돼 있지만 몇 개의 LSI로 분할되는 경우도 있으며 8비트 MPU 또는 32비트 MPU 하는 식으로 비트 수와 함께 부르는 것이 보통임
- 컴퓨터의 기본 구성 장치가 연산 처리장치와 주기억장치, 그리고 입.출력 장치로 돼 있는 데, MPU는 그 중의 연산처리장치임
- MPU에는 종래 소프트웨어로 실행하고 있던 기능과 명령을 하드웨어로 실행하기 위한 복잡한 명령 세트를 갖는 CISC(Complex Instruction Set Computer), 가급적 간단한 명령 세트만을 사용해 하드웨어를 단순화한 RISC(Reduced Instruction Set Computer), 4비트 또는 2비트의 MPU를 몇 개씩 접속해 비트 수를 사용자의 희망에 맞춘 비트스라이스 MPU 등이 있다.
- 마이크로 프로세서를 처음 개발한 것은 미국의 인텔사

#### MCU

- Micro Controller Unit
- 특정 시스템을 제어하기 위한 전용 프로세서
- 자동차나 밥솥, 냉장고, 세탁기 등의 제품을 제어하기 위한 전용 프로세서로 컴퓨터의 중앙연산처리장치(CPU)에 해당된다.
- 제품의 다양한 특성을 컨트롤하는 역할을 하는 비메모리 반도체(시스템 반도체)
- 롬(ROM)과 램(RAM) 회로까지 내장, 사실상 초소형 컴퓨터의 역할을 하고 있어 '원칩(One Chip) 컴퓨터' 또는 '마이콤'으로 불리우기도 한다.
- cpu 이외의 여러 가지 기능까지 덧붙여서 (Flash, UART, I/O ...) 한 개의 chip으로 만든 것
<br>

## :pushpin: 20.08.26

#### Register 분류
- General Purpose Register
    - Address Register : 외부 메모리에 데이터를 쓰거나 읽을 때 data가 들어있는 주소를 가리키는 값을 넣어둠
    - Data Register : 외부 메모리에서 읽어온 데이터 값을 임시 저장함
    - Instruction Register : 외부 메모리에서 읽어온 Op-code(명령어)를 저장함
- Special Purpose Register
    - Program Counter : 현재 실행되고 있는 주소를 가리킴
    - Stack Pointer : 현재 사용하고 있는 Stack 영역에서 마지막에 데이터가 push된 곳의 주소를 가리킴
    - Linked Register : 현재 수행하고 있는 것을 마치고 돌아갈 주소를 가리킴
    - Status Register : MCU의 현재 상태를 나타냄. (현재의 mode, 계산 결과 값의 상태 등)
- I/O Register
    - 기억장소처럼 보이지만, 실제로 D Flip Flop으로 구성되어 방금 저장된 값을 기억하기도 하고, 밀어내는 역할을 함

#### CPU의 동작
- Decoder : IR에 가져온 명령어를 해독하여 CU에게 알려줌
- CU(Central Unit) : Decoder에게서 받아온 것을 각종 제어 신호로 변환하여 제어 신호를 발생시킴
- ALU : 산술 연산 장치

#### ARM Processor
- Advanced RISC Machine
- 32 bit RISC Processor, Big/Little Endian 지원, Fast interrupt response
- register bank : 32bit 크기의 범용 register 31개, status register 6개가 묶여 있음.

#### CISC
- Complex Instruction Set Computer
- 많은 수의 명령어와 데이터 형태, addressing 기법들을 모두 채택
- chip의 크기가 크고, 명령어가 복잡, chip이 복잡하게 생김

#### RISC
- Reduced Instruction Set Computer
- 많이 사용되는 명령어, 데이터 형태, addressing 기법 등을 모아 만든 단순한 micro processor
- chip의 크기가 작아지고 단순해지고 전력소비가 줄어듦

#### Pipeline
- 하나의 명령어를 처리함에 있어서 병렬 처리가 가능하도록 함
- 각각의 단계는 1 clock에 해당된다.
- Fetch : 외부 메모리에서 명령어를 가져옴
- Decode : 가져온 명령어를 해석 및 register 확인
- Execution : 명령어 실행
<br>

## :pushpin: 20.08.27

#### ARM Modes
- Normal Mode : USR / Privileged Mode : SVC, SYS, IRQ, FIQ, UND, ABT
- normal과 privileged 모드 차이점
    + 특권 모드는 IRQ나 FIQ 등의 interrupt 사용 가능 유무를 직접 설정 가능.
    + 또한, 특권 모드는 서로간의 모드 전환이 가능함. 특권 -> normal 가능. normal -> 특권은 불가능.
- ARM의 default mode는 SVC -> boot up 때 ARM에 대한 모든 권한을 행사할 수 있음.
- User : Normal Program execution mode
- System : Run privileged operating system tasks
- FIQ : When a high priority (fast) interrupt is raised
- IRQ : When a low priority (normal) interrupt is raised
- Supervisor : A protected mode for the operating system, entered when a SWI instruction is executed
- Abort : Used to handle memory access violations
- Undef : Used to handle undefined instructions

#### ARM register와 context
- ARM Processor의 register는 총 37개
- R0~R15 (16개) + CPSR + banked register
- Banked Register : 일반 사용자모드가 아니고, 슈퍼유저 모드일때 (특권 모드)일때 사용되는 register -> 각 mode별로 따로 사용하는 register
- 모든 모드가 공유하는 register : R0~R7, PC, CPSR -> 얘네는 한 개씩 존재함

#### CPSR
- Current Program Status Register
- 32 bit register
- 28 ~ 31 bit : NZCV -> 연산한 후에 set되는 register
    + N : 연산한 결과가 Negative
    + Z : 연산한 결과가 0
    + C : 연산 결과 carry 발생
    + V : 연산 결과 overflow 발생
- 7번째 bit : IRQ disable(1)/ enable(0)
- 6번째 bit : FIQ disable(1)/ enable(0)
- 5번째 bit : Thumb mode / Arm mode
- 0~4 bit : 현재의 mode -> SYS와 USR은 mode bit만 차이나고 나머지는 같이 사용

#### SPSR
- Saved Program Status Register
- CPSR을 복사해놓는 레지스터 -> 모드 전환 후 이전 모드로 돌아올 때 SPSR에 백업해둔 CPSR의 값을 다시 CPSR에 복사해서 전환함.

#### R14 (LR) 
- Linked Register
- branch (jump) 할 때 어디에서 branch 해 왔는지 저장 -> 나중에 돌아갈 위치를 알 수 있음.

#### R13 (SP)
- Stack Pointer
- 어디까지 stack을 쌓아 두었는지 알 수 있음.

#### R15 (PC)
- Program Counter
- 실행하는 위치를 가리키고 있는게 아니라 현재 instruction을 fetch해 온 위치를 가리킴
<br>

## :pushpin: 20.08.28

#### Context
- register set의 snap shot 느낌
- R0 ~ R15, CPSR의 값들을 보면 MCU의 현재 상황을 알 수 있음.
- 다른 일을 하더라도 특정순간에 저장했던 Context를 다시 복원만 해줄 수 있다면 그 특정순간으로 돌아갈 수 있음

#### ARM Exceptions
- ARM은 발생하는 exception에 따라 mode가 변경됨
- Exception vector table : exception 발생 시 pc를 jump 시켜야 하는 주소(exception vector)를 저장한 테이블
- user 모드와 system 모드로 진입하는 exception은 없음. -> user 모드가 되면 다른 exception이 발생하지 않는 이상 다른 모드로 변경 불가
- 위 2개의 모드는 전환하려면 CPSR의 mode bit를 직접 수정하면 됨, SPSR이 존재하지 않음. (얘네로 진입하는 exception이 없으니까 돌아갈 CPSR 값을 저장할 필요가 없음)

#### Exception 우선순위
1. Reset -> SVC
2. Data abort -> ABT
3. FIQ
4. IRQ
5. Prefetch abort -> ABT
6. Undefined instruction -> UND
7. SWI -> SVC

#### Exception 발생 후 진행되는 순서 (ex. SVC -> IRQ)
1. CPSR을 SPSR_irq에 복사
2. CPSR의 mode를 IRQ로 변경, sp도 변경됨
3. IRQ disable 설정, ARM mode로 변경
4. R14_irq에 현재 PC값 저장 (돌아갈 주소)
5. PC를 exception vector 값으로 저장
6. R0 ~ R12를 R13_irq가 가리키는 스택에 저장
7. 돌아갈 주소 보정 (LR에 아까 PC값 저장했으니까 sub lr, lr, #4 이렇게 보정) -> 현재 

8. CPSR에 SPSR_irq 값을 넣음
9. stack에 저장했던 register값들 복원
10. PC에 R14_irq 값을 저장

#### mode의 장점
- 각 모드마다 register를 가지고 있으니까 각각의 mode를 적당히 사용하면 빠르게 전환이 가능함.
- user 모드에서 IRQ로 전환 -> 레지스터 복사 필요없이 mode를 전환
<br>

## :pushpin: 20.08.29

#### AAPCS
- Procedure Call Standard for ARM Architecture
- 레지스터들을 어떤 용도로 사용할 것인지 정해 놓은 규칙
- R0 ~ R3 : Argument, Result, Scratch
- R4 ~ R11 : variable -> 호출 된 함수가 해당 레지스터를 사용하려면 stack에 백업해두고 쓴 후에 다시 복원시켜서 return
- R12 ~ R15 : Special
  + R12 : IP (Intra) -> ARM-Thumb interworking 또는 long branch시에 Veneer를 통해 주소 할당 시에 임시 보관소로 사용함.
  + R13 : SP (Stack Pointer)
  + R14 : LR (Linked Register)
  + R15 : PC (Program Counter)
- 각 용도 별로 레지스터 개수가 더 필요하다면 stack에 저장함

#### ARM - Interrupt
- ISR : Interrupt Service Routine
- interrupt가 발생하면 실행 주소가 exception vector 중에 IRQ나 FIQ로 변경되고, 그 vector에는 실제 handler로 브랜치 하기 위한 코드가 들어있음.
- handler 내부에는 Interrupt가 여러 가지 종류가 있을 테니, 그 각각의 Interrupt에 따른 응답이 다름 -> 이게 ISR

#### SoC
- System on Chip
- ARM이 core design만 팔다 보니, core에 여러 가지 기능을 덧붙여서 하나의 chip으로 만드는 기술 -> 이러한 구조가 SoC
- ARM core를 바탕으로 웬만한 device들을 block화 해서 한 chip에 집어 넣겠다는 의미
- 이런 각각의 기능을 가진 SoC내부의 block들을 IP (Intellectual Property)라고 함
- MPU : Micro Processor Unit -> CPU의 성격이 강해서 외부 device들이 있어야 동작 가능
- MCU : Micro Controller Unit -> Controller 성격이 강해서 CPU 이외의 것들이 모두 들어있어서 혼자 동작할 수 있음.
- 둘 다 CPU의 기능이 들어있어서 굳이 구분할 필요는 없음.
