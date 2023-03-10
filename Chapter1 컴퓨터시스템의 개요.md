# operating system(운영체제)
> 컴퓨터 하드웨어 바로 윗단에 설치되는 소프트웨어

1. 운영체제는 사용자 및 다른 모든 소프트웨어와 하드웨어를 연결하는 소프트웨어 계층이다.
2. 소프트웨어가 컴퓨터 시스템에서 실행되기 위해서는 메모리에 그 프로그램이 올라가 있어야 한다.
⇒ 운영체제 자체도 하나의 소프트웨어로서 전원이 켜짐과 동시에 메모리에 올라간다.

## kernel(커널)
> 메모리에 상주하는 운영체제의 부분으로,
운영체제 코드 중에서도 핵심적인 부분을 뜻한다.

## 운영체제의 기능
1. 하드웨어를 위한 역할
사용자가 직접 다루기 힘든 각종 하드웨어 관리
(컴퓨터 시스템 내의 자원을 효율적으로 관리하는 것)
2. 사용자를 위한 역할
편리한 인터페이스를 제공하는 역할
(컴퓨터 시스템을 편리하게 사용할 수 있는 환경을 제공)


---
# Basic Elements
## Processor(CPU)
> 하드웨어적인 측면에서 "컴퓨터 내에서 프로그램을 수행하는 하드웨어 유닛"이다.

1. 이는 **중앙처리장치(Central Processing Unit, CPU)** 를 뜻하며,
폰노이만 아키텍쳐에 의해 만들어졌다면 적어도 하나 이상의 ALU (Arithmetic Logic Unit)와 처리 레지스터(Register)를 내장하고 있어야 한다.
2. CPU는 **메인 메모리** 와 프로세서 자체에 내장된 **레지스터** 에만 직접 접근할 수 있다.

### Process 
> 메모리에 적재되어 프로세서에 의해 실행중인 프로그램

### 컴퓨터가 프로그램을 실행하는 과정
1. 사용자가 단축 아이콘 혹은 명령행에서 프로그램을 실행한다.
2. 파일로 저장되어 있던 프로그램은 메모리(램)에 로더(Loader)에 의해 적재(load)되고 처음으로 실행해야 할 기계어 코드가 저장된 메모리의 주소를 CPU의 명령주소(IP : Instruction Pointer) 레지스터에 저장한다.
3. 프로세서(CPU)는 IP 레지스터가 가리키는 메모리의 주소에서 (처음으로) 실행할 명령어를 인출(메모리에서 CPU로 가져오는)하여 명령 레지스터(IR : Instruction Register)에 저장한다.
4. IR에 저장된 명령을 실행하고 IP에 다음번에 실행할 명령어가 있는 주소를 저장한다.
5. 3~4를 프로그램의 끝까지 반복한다.

## Main Memory(RAM)
1. 주기억장치(Random Access Memory)
2. volatile
컴퓨터의 CPU가 현재 처리중인 데이터나 명령어만을 일시적으로 저장하는 휘발성 메모리이다.
⇒ 전원이 꺼지면 메인 메모리에 저장되어 있던 모든 내용들은 사라지게 된다.
⇒ 따라서 전원이 꺼지더라도 데이터를 유지하고 싶다면, 
데이터를 하드 디스크에 저장해야한다.
3. **프로그램**은 실행되기 전까지 단지 디스크에 저장되어있는 **이진 실행파일**에 불과하다.
→ 실행을 위해 **메인 메모리**에 올라가는 순간 비로소 **프로세스**가 된다.

![](https://velog.velcdn.com/images/mini_mouse_/post/7fdf062e-7eab-468d-95d8-ad62be96d7e7/image.png)


## Register
> 레지스터는 CPU(Central Processing Unit)가 요청을 처리하는 데 필요한 데이터를 **일시적으로 저장**하는 **기억장치**이다.

![](https://velog.velcdn.com/images/mini_mouse_/post/2840f189-9d6d-4f0c-a9a0-8bd9e98b8b78/image.png)

1. 레지스터는 공간은 작지만,
CPU와 직접 연결되어 있으므로 연산 속도가 메모리보다 실제 수십 배에서 수백 배까지 빠르다.

2. 실제로 컴퓨터에서 데이터를 영구적으로 저장하기 위해서는 하드디스크를 이용해야 하고, 임시적으로 저장하는 장소를 메모리(RAM)라고 한다.

3. 레지스터 크기?
32bit or 64bit (더 정확히 system bus의 크기)
⇒ 크기가 클 수록 한 번에 데이터가 많이 움직여서 속도가 빨라진다.

하지만, 메모리로 연산의 결과를 보내고 영구적으로 저장할 데이터를 하드디스크에 저장해야 하는 등의 **명령을 처리** 하기 위해서는
이들에 대한 **주소와 명령의 종류를 저장할 수 있는 기억 공간**
이 하나 더 필요하다.
그리고 이 공간은 무리 없이 명령을 수행하기 위해 **메모리보다 빨라**야 한다.
바로 이런 역할들을 하는 것이 CPU옆에 붙어있는 레지스터이다.
그리고 **CPU는 자체적으로 데이터를 저장할 방법이 없기** 때문에 메모리로 직접 데이터를 전송할 수 없다.
때문에 **연산을 위해서는 반드시 레지스터를 거쳐야 하며**, 
이를 위해서 레지스터는 특정 주소를 가리키거나 값을 읽어올 수 있다.

## I/O modules
- secondary memory devices (disks)
- communications equipment
- terminals

## System bus
- communication among processors, memory , and I/O moduels

---
# Computer Component:<br>Top-Level View
![](https://velog.velcdn.com/images/mini_mouse_/post/7b542a6c-80c3-4ea1-ae99-4f7588463fca/image.png)

- Program = Instruction + Data

## CPU 전용 레지스터 (중요)
### AC(Accumulator, 누산기)
> 데이터를 일시 저장하는 레지스터

1. 데이터를 AC에 집어 넣으면 특별한 레지스터 mbr을 통해 데이터를 보내게 된다.
2. 기억장치로부터의 읽어온 데이터와 누산기에 적재되어 있던 데이터가 지정된 연산을 수행한 후, 
그 결과 값을 다시 누산기에 적재한다. 
3. 누산기 내용을 전부 지워 0으로 만들 수 있다. 
4. 왼쪽이나 오른쪽으로 몇 자리씩 움직일 수도 있다. 
5. 누산기의 비트 수는 CPU가 한 번에 처리할 수 있는 데이터 비트 수인 word의 길이와 같다.
5. 가지고 있는 값
   - 데이터 일시저장
   - AC = AC의 현재 값 + 메모리로부터 읽어온 값

### PC(Program counter)
> 다음에 실행할 명령어의 주소를 저장하는 레지스터


### IR(Instruction Register)
> 현재 실행중인 명령어를 기억하는 레지스터

### MAR(Memory Address Register, 기억장치주소 레지스터)
> 다음에 수행될 명령어를 인출하기 위해 현재 PC에 들어 있는 내용(주소)이 
시스템 주소버스로 출력되기 전에 일시적으로 저장되는 주소 레지스터

1. PC → MAR
2. instruction
프로그램 카운터에서 가져오는 거 X,
PC → MAR 옮겨서 가져오는 거 O

### MBR(Memory Buffer Register, 기억장치버퍼 레지스터)
> 레지스터와 외부에 연결되는 장치사이에서 전송되는 데이터의 전송통로이다.
기억장치로 쓰일 데이터나 기억장치로부터 읽어온 데이터를 임시로 저장하는 레지스터

**CPU 안에 있는 모든 레지스터가 메모리에 연결되는게 아니라,
CPU 안으로 들어오는 모든 명령어들과 데이터들은 MBR을 거친다.**

MAR의 실제 콘텐츠(데이터, 명령어)가 들어있다.

![](https://velog.velcdn.com/images/mini_mouse_/post/374ce7b7-35b8-4f57-93ed-37324512c29b/image.png)



### I/O AR(Input/Output Address Register)
입출력에 이용됨

### I/O BR(Input/Output Address Buffer Register)
입출력에 이용됨

---
# Instructions
## Program
> 일반적으로 하드 디스크 등에 저장되어 있는 실행 코드
program = instructions + data

## Instruction의 종류
1. Processor-memory data transfer
메모리 몇번지에 있는 데이터를 cpu로 옮겨라
2. Processor-I/O data transfer
cpu ↔ IO
3. Data processing 
더하기 뺴기, and, or
4. Control
jump 명령어

## Instruction Execution
### Two Steps
1. Processor가 memory로부터 명령어들을 읽어 온다.
2. Processor가 각각의 명령어를 실행한다.
### Basic Instruction Cycle (중요)
Fetch Stage: 메모리에서 instruction을 가져오기
Execute Stage: 명령어 분석 후 실행
![](https://velog.velcdn.com/images/mini_mouse_/post/7addcb1e-742c-43e6-b725-a85ed16c70cf/image.png)

시작 → 다음 명령어 가져오기 → 명령어 실행 → 정지(오류 X)

## Example of Program Execution
![](https://velog.velcdn.com/images/mini_mouse_/post/4b9a0096-5922-4eef-9c72-66a64ed23a3b/image.png)

---
# Control and Status Registers (중요)
## PC
다음에 실행할 명령어의 주소 저장
## IR
현재 실행할 명령어의 주소 저장
## PSW(Progam Status Word)
> 
**CPU의 현재 상태 정보 저장**
시스템 내부의 순간순간의 상태를 기록하고 있는 정보

- 시스템을 관리하는데 필요한 여러가지 상황을 이 레지스터에 저장해둔것이다.
**에러를 최소화**하고 시스템 전체에 영향을 안미치게 하기 위해 저장해두는 것이다.
- 비트마다 목적을 다르게 해서 여러가지 정보를 저장해둔다.
- **CPU의 연산 결과**에 따라 상태가 PSW에 저장되며, 
이 중에 인터럽트를 알리는 비트 5bit가 있고, 
5가지 ISR(인터럽트 서비스 루틴)이 운영체제 일부에 존재
- 인터럽트 처리 중 다른 인터럽트 발생 시, 운선순위에 의해 인터럽트 처리
- 세가지 정보를 갖는다.
   1. Condition codes
   (상태 코드, 점프를 할지 말지 결정하는데 사용하는 코드)
   2. Interrupt enable/disable
   (인터럽트 활성화 여부)
   3. Supervisor/user mode

   # Computer Component: <br>Top-Level View
![](https://velog.velcdn.com/images/mini_mouse_/post/950ec01a-b690-4ace-9099-021540e2da33/image.png)

# Program Execution
![](https://velog.velcdn.com/images/mini_mouse_/post/7d8745d0-2e53-4942-8684-c4d25d8ef40e/image.png)

## Fetch Stage
PC에 들어있는 300은 Step1 이전에 들어 있었던 것이다.

PC에 300이 들어 있다고 해서 우리가 메모리 300번지에 있는 명령어를 읽어올 수 없다.
→ 내가 메모리에서 무언가를 읽어 오려면 내가 읽어오려고 하는 명령 또는 데이터의 주소가 MAR에 들어 있어야 한다.

### Fetch Stage의 과정
![](https://velog.velcdn.com/images/mini_mouse_/post/e4bae2ae-8e78-4d4e-b7c5-3821893d84e7/image.png)

⇒ 메모리에서 300번지에 들어있는 명령어 읽어 오는 과정

fetch stage가 시작하기 전에,
PC: 300, IR: 이전 실행 명령어가 들어 있다.

>1. PC에 들어 있는 300 번지 주소를 MAR로 옮긴다.
2. 메모리 읽기
3. 메모리 300번지에 있는 명령어가 MBR로 온다.
그러나 명령어가 MBR로 왔다고 해서 내가 이 명령어를 실행시킬 수 있는 것은 아니다.
왜냐하면 명령어를 분석하려면 명령어가 IR로 들어가야 하기 때문이다.
4. MBR로 들어온 명령어를 IR로 옮긴다.

중요한 것은 위의 과정에서 PC의 값은 다음 명령어의 주소를 가르키도록 변경되어야 한다는 것이다.
다음 명령이 무엇인지는 알 수 없기 때문에 우선은 바로 다음 명령은 다음줄에 있는 명령이라고 가정하여 PC의 값에 +1을 한다.

> **Fetch Stage**
1. PC → MAR (읽어오려는 메모리 주소 옮기기)
2. PC++
3. memory read 명령 실행
4. 명령어 → MBR
5. MBR → IR

⇒ Fetch Stage가 끝나면 PC는 1이 증가되어 있다.

---
# Execution Stage
## Read
1. IR의 Operation code 확인
어떤 명령을 시작하든간에 우선 명령을 분석해야한다.
→ 명령어에 따라 Execution Stage의 단계가 달라진다.
2. IR → MAR
Fetch Stage에서는 PC에 저장된 번지가 MAR로 이동을 했다면,
Execution Stage에서는 IR에 저장된 번지가 MAR로 이동한다.
3. MBR → AC(read) or AC → MBR(write)
**데이터를 읽어올 때는 Fetch Stage와 다르게 IR이 아니라 AC에 데이터를 저장한다.**


## 명령어(instructions)
1. 0001(1) = **Load** AC from memory(읽어오기)
메모리 → AC
2. 0010(2) = **Stroe** AC to memory(저장하기)
AC → 메모리
3. 0101(5) = **Add** to AC from memory(더하기)

위의 세 명령어는 모두 데이터가 이동하는 명령어이다.

### 데이터가 이동하는 명령어
1. Processor-memory data transfer
2. Processor-I/O data transfer
3. Data processing 
산술논리연산 명령어(+, -, and, or)

### 데이터가 이동하지 않는 명령어
1. Control
jump 명령어, 조건을 확인한 후 주소 번지 이동시키는 명령어
데이터가 필요 없는 명령어이다.
⇒ 모든 명령어가 데이터가 필요한 것은 아니다.

명령어는 위의 4가지만 존재한다.

### IR
![](https://velog.velcdn.com/images/mini_mouse_/post/5d42619c-818a-4bc2-8d60-566dac8be16d/image.png)


IR의 첫번째 숫자는 명령어를 나타낸다.

#### Read IR 예시
![](https://velog.velcdn.com/images/mini_mouse_/post/226e3466-e24f-48bd-862b-d92afa478cd3/image.png)

![](https://velog.velcdn.com/images/mini_mouse_/post/2a256233-6e12-451e-a549-154d60421bb3/image.png)

= 메모리 940번지에 있는 수를 읽어와서 AC에 넣어라 (Load)

1. IR의 Operation code 확인 = 1
어떤 명령을 시작하든간에 우선 명령을 분석해야한다.
2. IR → MAR
Fetch Stage에서는 PC에 저장된 번지가 MAR로 이동을 했다면,
Execution Stage에서는 IR에 저장된 번지가 MAR로 이동한다.
3. memory load
4. memory → MBR
5. MBR → AC
데이터를 읽어올 때는 Fetch Stage와 다르게 IR이 아니라 AC에 데이터를 저장한다.

#### Add IR 예시
![](https://velog.velcdn.com/images/mini_mouse_/post/ddf75b79-8f1f-41af-b239-cf11fe09701d/image.png)

![](https://velog.velcdn.com/images/mini_mouse_/post/07bd6383-fcfe-41de-a5ba-e9f346a51747/image.png)

= 메모리 941번지에 있는 수와 AC에 있던 수를 더해 AC에 다시 넣어라 (Add)

1. IR의 Operation code 확인 = 5
어떤 명령을 시작하든간에 우선 명령을 분석해야한다.
2. IR → MAR
Fetch Stage에서는 PC에 저장된 번지가 MAR로 이동을 했다면,
Execution Stage에서는 IR에 저장된 번지가 MAR로 이동한다.
3. memory read
4. memory → MBR
5. MBR → AC + MBR → AC
실제로는 레지스터가 무지하게 많기 때문에 이런식으로 계산 안한다.

#### Store IR 예시
![](https://velog.velcdn.com/images/mini_mouse_/post/0117e5cd-b6e1-4e90-bc1c-76acb4c7170d/image.png)

![](https://velog.velcdn.com/images/mini_mouse_/post/ae9cc419-c04f-4c69-9bdb-940283140f31/image.png)

= 메모리 941번지에 AC에 있는 수를 저장해라 (Store)

1. IR의 Operation code 확인 = 2
어떤 명령을 시작하든간에 우선 명령을 분석해야한다.
2. IR → MAR
Fetch Stage에서는 PC에 저장된 번지가 MAR로 이동을 했다면,
Execution Stage에서는 IR에 저장된 번지가 MAR로 이동한다.
3. AC → MBR
4. memory write
5. MBR → memory

---
# Interrupts
🌟 제일 중요해용 🌟

>CPU가 명령어를 한줄 한줄 실행하고 있을 때 중단하는 것

→ **3가지 관점**에서 Interrupts(중단)를 바라봐야 한다.

## 1. 내가 프로그램일 때
A라는 어플리케이션 프로그램일 때, 10번째 명령어까지 실행하고 갑자기 중단 됨
→ **나는 무슨 일이 생겼는지 모름**
→ 이후 시간이 흐르고 11번째 명령어부터 다시 실행
→ 중단
→ 재개
...
## 2. 내가 OS일 때
(전체 시스템 관점에서)
A를 실행하다가 A를 중단
→ OS 실행 (중단, OS가 프로그램을 바꾸는 역할을 한다.)
→ B 실행
→ OS 실행 (중단)
→ A 실행
...
## 3. 내가 CPU일 때
CPU는 프로그램 A가 실행되고 있는지, B가 실행되고 있는지, C가 실행되고 있는지 모른다.
→ 그저 한줄 한줄 명령어를 실행할 뿐, 이 한줄 한줄의 어떤 프로그램의 명령어인지는 모른다.

그러나, **App이 실행되고 있는지 OS가 실행되고 있는지는 알아야한다.**
- **OS**가 실행되고 있을 경우에는 컴퓨터의 **많은 자원에 access**할 수 있지만,
- 다른 **기본 App**들은 매우 **한정적으로 access**할 수 있기 때문이다.

>⇒ OS가 프로그램을 CPU(프로세서)에게 뺏고 주고 하는 것이다.

## Interrupt가 걸리는 이유
4가지 이유가 있다.
### 1. Program Interrupt
잘못 이해하는 부분: 프로그램에서 인터럽트를 다룬다. → X
프로그램에서는 인터럽트를 다룰 수 없다.

프로그램의 명령어가 한줄한줄 실행되다가,
이 명령어 한줄의 실행결과와 관련된 다양한 하드웨어가 Interrupt를 거는 것이다.

#### 어떻게 명령을 실행했길래 Interrupt가 발생?
1. Overflow
Condition 명령어에서 발생할 수 있다.
2. division by zero
잘못된 연산
3. Illegal mechine instruction
CPU의 IR OP code 분석
4. reference outside a user's allowed memory space
CPU는 access 가능한 메모리 영역을 표시해두어서 그 영역을 넘어가는 번지수를 요청할 때 Interrupt를 걸 수 있다.

### 2. Timer Interrupt
시스템 안의 CPU는 한 개이기 때문에 App 하나만 실행할 수는 없다.
⇒ **각 프로그램마다 실행할 수 있는 시간이 정해져 있다.** : `Time Slice`
동시에 여러 프로그램들이 실행되는 것처럼 보이게 된다.

OS가 나타나서 프로그램을 다른 것으로 바꾼다.

### 3. I/O Interrupt
I/O Controller가 발생시키는 Interrupt이다.
젤 어려워용!

### 4. Hardware failure Interrupt
하드웨어에 문제가 발생해서 프로그램 다 멈추고 OS가 문제를 해결하는 것


>대부분의 I/O Devices은 프로세서(CPU)보다 속도가 느리다!
⇒ 프로세서 입장에서는 입력과 출력을 기다리는 것이 거의 천년만년이다..
장치를 위해서 멈추고 있으면 너무 CPU라는 장비가 아깝게 되는 것이다..

---
# Program Flow of Control with or Without Interrupts- 1
![](https://velog.velcdn.com/images/mini_mouse_/post/486f1c22-88f2-4d2f-b069-01b93a3e7cef/image.png)

## 메모리 ↔ CPU ↔ buffer ↔ I/O modules

WRITE = print
외부에서 입력을 받으면 입출력 모듈은 buffer에 입력 받은 값을 저장한다.
이 내용물을 CPU를 통해서 Main Memory로 이동시키는 것
Write는 CPU가 하는 것이 아니다.

CPU는 I/O Device에게 입출력을 하라고 지시만 한다. (I/O Command)

4. 입력을 하든, 출력을 하든 I/O buffer를 사용해야한다.

I/O Command 실행 → 입력 받기

5. 입출력이 끝나면 끝이 아니라 return등을 통해 입출력이 성공적으로 이루어 졌는지 확인을 해서 user 프로그램에게 알려준다. 
(성공여부 확인 작업까지 해야 입출력 작업이 완전히 끝나게 된다.)

1 - 4 ----- 5 - 2 - 4 ----- 5 - 3 - 4 ----- 5
→ 줄이 긴 것은 CPU가 노는 시간이다.
⇒ 시간이 너무 아깝기 때문에 인터럽트를 사용하게 된다.

(b) 4번 내내, I/O가 입력을 받는 시간 내내 기다리지 않고 바로 돌아와서 다른 프로그램을 실행하는 것 
⇒ 더 빠르다.
## I/O Interrupt
>다른 프로그램을 하다가 I/O 작업이 끝나면 작업이 끝났다고 인터럽트를 보내는데, 이것이 I/O 인터럽트이다.
이는 Interrupt Handler가 제어한다.

## Timing Diagram : Short I/O Wait

![](https://velog.velcdn.com/images/mini_mouse_/post/025355cc-e971-4328-b44a-a7b33af3b722/image.png)

# Interrupt Handler
![](https://velog.velcdn.com/images/mini_mouse_/post/8dbab494-235a-4fcc-9d22-c79a6956310b/image.png)

왼쪽 그림이 user program, 오른쪽 그림이 Interrupt Handler이다.

1. Interrupt Handler는 OS의 한 부분이다.

2. Interrupt Handler는 Interrupt가 발생하면 Interrupt를 처리하는 역할을 한다.
3. 모든 항목마다 적절한 Interrupt Handler가 따로 존재한다.

## Interrupt Handler가 실행되는 과정
1. user program이 i번째 명령어까지 실행
2. interrupt
3. 실행하던 프로그램 종료
4. Interrupt Handler 프로그램 실행
5. Interrupt Handler가 아까의 5번(입출력 성공여부 확인)까지 실행
6. 다시 i+1 코드 실행

## Q. Interrupt가 걸려도 왜 바로 처리를 하지 않을까?
Fetch Stage → Execute Stage → Interrupt Stage

왜 Fetch, Execute 이후에서야 Interrupt가 처리될까?

Interrupt가 처리된 이후에는 PC가 복귀가 되어 PC에 저장된 다음 명령어가 실행되기 때문에 이전 명령어는 처리가 완료되어야 있어야 한다.
Instruction cycle Fetch-Execute이 진행되면 PC가 증가되어 버리기 때문에 완료되지 않은 상태에서 인터럽트가 진행되고, PC가 복구되면 이전 명령어는 진행되지 못하게 된다.

### Instruction Cycle with Interrupts
![](https://velog.velcdn.com/images/mini_mouse_/post/ca05e125-9961-416b-925b-8bf2d430f6b8/image.png)

하나의 프로그램의 사이클의 아니다.

Execute Stage가 끝날 때마다 Interrupt가 걸렸는지 확인한다.
Interrupt가 왜 걸렸는지 누가 걸었는지를 확인해야한다.
해당하는 Interrupt Handler를 실행한다.

Initiate Interrupt Handler

## Q. Interrupt Stage에서는 Interrupt가 걸린 이유를 파악하고 이 Interrupt Handling 하기 위한 적절한 프로그램을 실행시킨다. <br> → X
Interrupt Stage에서는 프로그램을 실행시킬 수 없다.

명령 하나를 실행시키는 사이클이다.
따라서 인터럽트 핸들러라는 새로운 프로그램을 시작해야하기 때문에
결국 Interrupt Stage에서는 **OS**를 실행시킨다.

⇒ OS 실행

## Q. OS의 실행 순서?
PC 값 OS 명령어로 변경하기



---
# Program Flow of Control With or Without Interrupts (2)

![](https://velog.velcdn.com/images/mini_mouse_/post/4841faaf-f3fd-46f3-be06-2fea8dc4b398/image.png)

![](https://velog.velcdn.com/images/mini_mouse_/post/1c2c9660-ec53-49d3-ba6f-924023e1cad9/image.png)


c에서 2에서 인터럽트가 걸리지 안하 5번 작업이 끝날 때까지 기다린다.
1 4 2(2가 끝날 때까지 I/O가 안끝남) 5 4 3(3이 끝날때까지 I/O가 안끝남) 5

---
# 프로그램 바꾸기
## OS실행 방법?
OS도 프로그램이기 때문에 
A 프로그램 실행하다 → Interrupt → OS → B 프로그램 실행

>PC에 OS 실행 명령어 주소 번지를 저장한다.

>PC의 값을 바꾸면 프로그램이 변경될 수 있다.

인터럽트 이후 이어서 실행을 해야하기 때문에 OS로 프로그램을 변경하기 전에

메모리는 안전하기 때문에 중단된 명령어들(CPU 값들)을 모두 레지스터에 저장해준다.

---
# Simple Interrupt Processing<br>인터럽트 처리 과정
![](https://velog.velcdn.com/images/mini_mouse_/post/13ea6f87-1634-4551-b9ee-8a01762ada45/image.png)

## HardWare
1. CPU가 처리
2. Device Controller가 인터럽트 발생(I/O)
3. 지금 실행하고 있는 명령어는 끝까지 처리한다.
Fetch과정에서 PC가 증가하게되는데 Execute처리가 되지 않고 Interrupt가 실행되고 PC가 복구되면 이전 명령어는 실행되지 않는다.
4. CPU가 인터럽트 인지
5. CPU가 PSW와 PC값 control stack(안전한 메모리, 하드웨어)에 저장
6. PC에 OS 실행 주소 번지 저장


## SoftWare
OS 또는 Interrupt Handler가 처리
OS는 어마어마하게 큰 프로그램, 시스템을 관리하는 프로그램이다.

Hardware와 Software가 만나는 부분이 굉장히 많은데 그걸 OS가 처리한다.

1. 나머지 중요한 CPU 정보들, process state를 저장
2. 인터럽트가 왜 발생했는지 확인 후 적절한 처리
3. process state CPU 복구
4. PC, PSW 복구

## Q. PC, PSW 따로 저장하는 이유?
마지막에 process state 먼저하는 이유?
새로 실행을 시작할 PC 값을 저장하는 순간 인터럽트 핸들러의 작업이 끝나기 때문이다.
새로운 프로그램이 바로 시작되어 버린다.
이전의 중요한 정보들이 모두 저장되지 못한채로 새로운 프로그램이 시작된다.
OS가 해야할 것을 먼저 끝내고 다른 프로그램이 시작되어야한다.

따라서 Hardware에서도 5번 이후 6번이 실행되어야 한다.
6번에선 이미 PC 가 OS 주소로 바뀌기 때문이다.

# Interrupts: short I/O wait
![](https://velog.velcdn.com/images/mini_mouse_/post/17c4bc5f-efa2-4183-8953-094b95c8f7fd/image.png)

## System call
>`System call` : User Program에서 OS에게 I/O같은 것을 요청하는 것

1. User Program이 WRITE라는 System call을 호출한다.
2. WRITE는 함수 호출이지 명령문이 아니다.
→ print, scanf는 명령문이 아니라 함수 호출문이다.

3. 4번 코드는 User Program의 일부가 아니라 OS 코드의 일부이다.
→ 입출력은 OS가 한다.

4. 4번 코드는 Interrupt가 아니다. 그저 System call을 호출한 것이다.

## I/O Interrupt
1. OS입장에서 생각해보니, 입출력을 받을 때까지 다른 프로그램을 실행시켜도 될 것 같아서 프로그램A → 프로그램B로 실행하는 프로그램을 변경한다.

2. 프로그램B가 실행하는 도중 프로그램 A의 입출력이 끝났을 때 프로그램B에 인터럽트를 걸어서 프로그램을 강제 종료한다.

>⇒ 즉, **I/O 인터럽트**는 B 프로그램에게 A 프로그램의 입출력 작업이 끝났음을 알려 B 프로그램의 진행을 방해하는 것을 말한다.

5번 코드는 `Interrupt Handler` 가 다루며, 4번 코드가 아닌 5번 코드를 진행하기 위해 하는 것이 `I/O Interrupt` 이다

### Q. I/O Interrupt는 입출력을 하기 위해서 OS를 호출하는 것이다<br>→ X
4번코드의 입출력하기 위함이 아니다. 
### Q. I/O Interrupt는 내 프로그램의 입출력 때문에 발생한다.<br>→X
다른 프로그램의 I/O 때문에 발생한다.
### Q. I/O Interrupt는 I/O 작업이 시작할 때 발생한다.<br>→X
끝날 때 발생한다.

---
# Changes in Memory and Registers<br>→ Interrupt 처리과정
![](https://velog.velcdn.com/images/mini_mouse_/post/72c98e4c-f816-4fd3-9ff8-246cd41fd3b7/image.png)

왼편에 있는 그림
- 컴퓨터의 CPU의 상태를 저장하는 과정
- 번지수 N에 있는 명령어 이후 인터럽트 발생

오른편에 있는 그림
- OS가 작업을 다 마치고 이전에 실행하던 또는 다른 프로그램의 CPU 상태를 restore하는 과정
- 인터럽트 처리후 복구하는 과정

![](https://velog.velcdn.com/images/mini_mouse_/post/0eef72f0-700a-4556-aa0d-02a5beee8604/image.png)
## User's Program
PC를 보면 N + 1이 저장되어 있으므로 현재는 UserProgram의 N 명령어를 실행 중이다.

## Interrupt Service Routine
인터럽트 핸들러 코드이다.
인터럽트 핸들러 코드는 OS의 코드이다.

## Control Stack
중단된 프로그램들의 CPU 상태가 stack처럼 쌓여 있는 곳이다.

## Stack Pointer
Stack의 Top이 어딘지 가르킨다.

## General Register
CPU 안에 있는 Register의 상태들을 다 저장해야한다.

사실 CPU 안의 모든 값들을 저장할 필요는 없다. (IR, MBR, MAR → 데이터가 이동할 때만 사용한다.)
하지만 그냥 다 저장하는게 편하기 때문에 다 저장하는 것이다.

## 순서
1. PC의 N+1 값을 Control Stack에 저장
PC → Control Stack
(flow chart 4번 코드)
2. Interrupt Handler가 Y번째부터 시작되므로 Y를 PC에 저장한다.
Interrupt Service Routine → PC
3. Y ~ Y + L까지 Interrupt Service Routine 처리
4. 남은 나머지 General Register의 값들을 모두 Control Stack에 저장
5. Stack Pointer의 값 업데이트


![](https://velog.velcdn.com/images/mini_mouse_/post/9e7f612b-8a73-4a5c-9846-03e6afb4b882/image.png)

## 순서
1. 인터럽트 처리 끝
2. 현재 PC에 Y+L+1이 저장되어 있으므로 Y+L의 return 명령어를 처리하는 중이다.
3. General Registers 값들을 모두 restore한다.
4. PSW와 PC를 restore한다.
5. pop()이 되었으므로 Stack Pointer를 바꾸어준다.
6. 그 뒤 PC를 N+1로 바꿔준다.

---
# Memory Hierachy
컴퓨터에 저장된 모든 실행 파일들은 HDD(HarD Disk)에 저장되어 있는데,
실행을 하기 위해서는 Main Memory에 올라가야 한다.

![](https://velog.velcdn.com/images/mini_mouse_/post/a05af6a7-e980-41ea-9f4a-f42b617a3199/image.png)

Magnetic Disk = HDD

>Memory Hierach은 프로그램이 이동하는 경로이다.

## 이동순서
Disk → Main Memory → Cache → Register 순으로 이동하게 된다.

### Q. 왜 이런 복잡한 이동순서를 가지고 있을까?
→ Main Memory부터 휘발성이기 때문에 전원을 끄는 순간 저장되어 있던 데이터가 모두 사라지게 된다.

→ 저장용량이 문제가 된다.
HDD는 용량이 크기 때문에 모든 파일을 저장할 수 있지만 Memory에는 모든 것을 저장할 수 없다.

- 메모리는 나누어져 있다.
- 실행되는 프로그램도 나누어져 있다.

## 주된 메모리의 제한들
1. 용량 제한
→ 기술적 문제로 인하여 캐시나 레지스터의 용량을 키우고 싶어도 키울 수 없다.
2. 속도 문제
3. 비용 문제

## Going Down the Hierachy<br>(계층이 내려갈 수록)
1. 싸다
2. 용량이 커진다.
3. 접근 속도가 빨라진다.
4. 시스템이 효율적으로 이루어질 수 있도록 최대한 하드디스크에 접근하는 일을 줄인다.
→ 속도가 느린 애들은 가끔씩 접근해서 속도를 높인다.

### 효율적으로 프로그램을 실행시키기 위해
1. 한 페이지 단위로,
HDD → Main Memory로 명령어 읽어오기
2. 한 블럭 단위로, 
HDD → 캐시로 명령어 읽어오기
3. 한 word(문장) 단위로,
캐시 → 레지스터로 명령어 읽어오기

### Reference locality
>내가 사용하는, CPU에 의하여 참조되는 메모리의 함수들(Instruction, Data)은 뭉쳐있어야 한다.

⇒ 즉, 변수 선언 위치가 중요하다!

---
# Cache Memory
1. CPU는 메모리의 속도보다 빠르다.
2. CPU 처리 속도만큼 빠르다
→ 따라서 PC에서는 Cache에 먼저 실행하려는 번지의 명령어가 있나 확인하고,
캐시에 해당 번지의 명령어가 없으면 main memory로 가서 확인하고 해당 번지 주변의 명령어 한 블럭을 가져오고,
main memory의 속도를 빨라보이게 한다.
(별 일 없으면 다음 명령어 실행 순서는 순차적으로 진행된다는 가정하에 캐시를 사용하여 진행된다.)
3. 캐시는 메인 메모리의 일부분을 복사하여 포함한다.
4. 메인 메모리의 속도를 증가시킨다.
5. Operating System이 관리하지 않는다.

## Q. why is cache memory invisible to the operating system?<br>
(OS에서 Cache를 관리하지 않고 Hardware에서 관리하는 이유?)
컴퓨터의 성능향상을 위해서이다.
속도 향상 → 더 빠르고 빈번하게 명령어와 데이터에 접근할 수 있다.
OS로 인한 overhead나 delay를 없애기 위함이다.

캐시는 빠른 액세스가 가능한 하드웨어에서 데이터를 가져오면서 속도 향상을 노리며, 동시에 동일 데이터에 대한 접근 시 미리 구성된 데이터를 응답하여 불필요한 검색 작업을 방지할 수 있다.

![](https://velog.velcdn.com/images/mini_mouse_/post/f1eec376-6667-4746-98b3-04cdac80ef65/image.png)

- word는 Instruction 하나를 의미하는 단위이다.
- cache가 CPU에 가까울수록 빠르고 Main Memory에 가까울수록 느리다.

---
# I/O Techniques
세 개의 기술들이 I/O operations에서 가능하다.

## 1. Programmed I/O
>I/O 프로그램을 OS가 실행을 하고 I/O device가 작업을 하는 동안 그냥 서있는 것

![](https://velog.velcdn.com/images/mini_mouse_/post/e3dda5f0-dd50-4d6d-a9e1-8ac54e6f69a9/image.png)


## 2. Interrupt-Driven I/O
>I/O Device가 작업을 하는 동안에  CPU는 User Program을 계속 실행하다가 나중에 I/O 작업이 다 끝나면 인터럽트가 걸리면 OS가 5번 코드를 처리하는 것을 말한다.

- 표준 입출력시 사용한다.

- data의 이동 경로
⇒ Main Memory ↔ CPU ↔ I/O

![](https://velog.velcdn.com/images/mini_mouse_/post/4c928e09-e232-42a6-af9b-2f9618f5a7e9/image.png)

## 3. Direct Memory Access (DMA)
>data의 이동경로
⇒ Main Memory ↔ I/O 

1. 굉장히 많은 양의 데이터가 이동할 때, 즉 **파일 입출력**시 사용한다.

2. 메인 메모리와 I/O 모듈도 연결되어 있으므로 효율적인 데이터 처리를 위해 이 두 장치 사이에서 데이터와 명령어들이 CPU를 거치지 않고 바로 이동하는 것

3. CPU는 오직 **전송의 처음과 끝에만 개입**한다.
- 입력인지 출력인지 확인 (read or write)
- 어느 I/O device인지
- 메모리와 I/O buffer 시작 주소
- 정보의 길이 (끝 주소가 아닌 시작 주소와 길이가 들어가 있다.)

4. DMA도 Interrupt는 존재한다.
I/O device controller가 인터럽트를 걸어서 성공여부를 확인한다.

5. Interrupt-driven이나 programmed I/O보다 효율적이다.
즉 DMA는 다른 I/O 작업보다 빠르게 작동할 수 있다.

6. CPU 접근에서 bus가 요구될 때 전송 동안 CPU는 더 천천히 작동된다.
![](https://velog.velcdn.com/images/mini_mouse_/post/de18d364-d260-4f53-8bd3-a5a73acaf243/image.png)

대용량 프로그램인 것을 확인한 CPU는 메인 메모리와 I/O 모듈들에게 서로 직접적으로 소통하라고 한 다음 다른 프로그램을 실행한다.

그런데 메인메모리에서 명령어를 가져올 때 메인메모리와 I/O가 소통중이면 System Bus를 사용할 수 없다.

⇒ 따라서 충돌이 일어나지 않도록 조절을 해주어야 한다.
그렇기에 CPU가 기다려야해서 느려질 수 있다.

---
# Symmetric Multiprocessors(SMP)
![](https://velog.velcdn.com/images/mini_mouse_/post/de18d364-d260-4f53-8bd3-a5a73acaf243/image.png)
## Multi Processor
> 하나의 시스템에 CPU가 하나인게 아니라 여러 개가 존재하는 것

1. 메모리랑 I/O System은 공유한다.
CPU가 100개라고 키보드를 100개 달아 놓는 것이 아니다.
→ CPU가 1개일 때 보다 속도가 빨라진다.

2. CPU가 10개 있더라도 1개일 때 보다 10배가 빨라지는 것은 아니다.
→ OS 때문이다.
Symmetric OS 때문
CPU가 100개이든 200개이든 시스템을 관리하는 것은 OS이다.
OS가 시스템을 잘 못 관리하면 CPU가 아무리 많아도 소용이 없다.

## Symmetric의 뜻
>대칭형 다중 처리(symmetric multiprocessing, SMP)는 두 개 또는 그 이상의 프로세서가 **한 개의 공유된 메모리**를 사용하는 다중 프로세서 컴퓨터 아키텍처이다. 

1. 각각의 CPU에 OS를 실행시킬 수 있다는 뜻이다.
→ OS가 동시에 실행된다는 것은 공유된 자원을 동시에 사용할 수 있게 된다는 의미이다.

2. 현재 사용되는 대부분의 다중 프로세서 시스템은 SMP 아키텍처를 따르고 있다.

3. SMP 시스템은, 작업을 위한 데이터가 메모리의 어느 위치에 있는지 상관없이 작업할 수 있도록 프로세서에게 허용한다. 
운영체제의 지원이 있다면, SMP 시스템은 부하의 효율적 분배를 위해 프로세서간 작업 스케줄링을 쉽게 조절할 수 있다. 

4. 그러나 메모리는 프로세서보다 느리다. 단일 프로세서라도 메모리로부터 읽는 작업에 상당한 시간을 소비한다. SMP는 이를 더욱 악화시키는데, 
한 번에 한 개의 프로세서만이 동일한 메모리에 접근 가능하기 때문이다. 이는 다른 프로세서들을 대기하도록 만든다.

5. OS가 시스템 안에 있는 중요한 자원에 access할 때는 마음대로 access하지 않고, rule을 정해서 순차적으로 작업을 해야한다.
→ 이 때 사용하는 여러 가지 도구들이 있다.

6. 중요한 것은 **둘 중 하나는 기다려야 한다**는 것이다.
즉, CPU가 10개이더라도 소용이 없다.
어차피 순차적으로 하나씩 처리되기 때문이다.

---
# Multicore Computer
>여러개의 CPU가 하나의 시스템 안에 있는 것을 말한다.
하나의 시스템이 아니라 하나의 칩 안에 굉장히 많은 칩들이 들어가 있다.

![](https://velog.velcdn.com/images/mini_mouse_/post/c80b4f3d-76a0-4eb4-87fd-a2bf23c8c92d/image.png)

CPU들이 캐시들을 가지고 있다.
위에서는 캐시가 두 단계 캐시였는데, 여기서는 세 단계 캐시를 가진다.

두 단계 캐시까지는 각자 자기 캐시를 가지고 있는데 세 번째 단계 캐시는 공유 캐시이다. 
→ 같은 칩이기 때문에 캐시도 공유할 수 있다.