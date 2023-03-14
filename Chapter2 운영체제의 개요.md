# Operating System
OS가 무엇이냐?
⇒ OS는 프로그램이다!

## OS는 Program이다.
1. OS는 Application의 실행을 control하는 프로그램이다.
→ OS는 Application을 최소로 방해해야한다.

2. Application과 Hardware를 연결하는 인터페이스 역할을 하는 프로그램이다.
→ Programmer가 hardware를 건드리지 않아도 돼야 한다.

### User/Computer Interface
1. Programmer(Application Program을 작성하는 사람)가 hardware의 detail을 몰라도 된다.
2. OS에 따라 다운로드 프로그램이 달라진다.

Application program의 실행은 OS 위에서 실행된다.

#### Library
1. 하드디스크에서 데이터를 가져올 때 단위가 있다.
정수 하나만을 가져오지 않는다.
→ 정수가 포함되어 있는 한 블럭이 온다.

2. **메모리에 버퍼를 하나 만들어 놓고 정수를 모아 놓고 하나씩 가져다준다.**
이 역할을 하는 것이 라이브러리이다.

3. **모든 입출력 문장들은 system call이 아니라 라이브러리 함수**이다.

4. 이 함수 안에서 **입출력을 편하게 할 수 있도록 버퍼 관리**를 한다.

5. System call에는 READ, WRITE 두 개만 존재한다.

(printf, scanf 입출력)


![](https://velog.velcdn.com/images/mini_mouse_/post/bf78e0ab-818d-4295-b483-44a0c93e153c/image.png)


### User/Computer Interface가 정확하게 해주는 일?
>모든 자원(I/O device, CPU, memory, ...)을 관리하며 프로그램들이 이를 효율적으로, 공평하게 사용할 수 있도록 시스템과 리소스를 관리한다.

1. 프로그램 development를 도와준다.
2. 프로그램 실행을 도와준다.
3. I/O devices에 접근한다.
4. file에 acsess 하는 것을 도와준다.
5. 시스템 access 하는 것을 도와준다.
6. 에러를 감지하고 응답하는 것을 도와준다.
7. 어떤 자원을 얼만큼 사용했는지 기록해준다.
→ 이걸 보고 프로그램 순서를 조정하며 메모리 제공량을 변경한다.

---
# Resource Manager
## OS가 다루는 컴퓨터 자원
- I/O
- Main Memory
- Secondary memory
- Processor execution time

## Kernel
>메인 메모리 안에 들어 있는 OS의 부분
꼭 필요한, 자주 사용되어지는 중요한 OS 부분이다.

시스템에 따라 OS == Kernel인 것도 있다.
![](https://velog.velcdn.com/images/mini_mouse_/post/0347bbec-ad4d-462d-8056-53d14437b126/image.png)

---
# Evolution of Operating Systems
![](https://velog.velcdn.com/images/mini_mouse_/post/ae5d9bfb-87ea-464f-9bba-95c1ed828d6d/image.png)

## Serial Processing
엄청 구식 프로그램 처리 과정

## Simple Batch Systems
A 프로그램이 종료된 후 B 프로그램이 자동으로 시작되어 Operator가 개입하지 않아도 되는 시스템

여기까지는 한 번에 한 프로그램만 실행할 수 있었다.

### UniProgramming
>CPU가 한 번에 하나의 프로그램만 실행 하는 것
CPU가 I/O 작업이 끝날 때까지 기다려야한다.

![](https://velog.velcdn.com/images/mini_mouse_/post/7d4c92e7-95b1-4e45-a331-e22fd44589da/image.png)

- Run: CPU 사용
- Wait: I/O 작업

→ CPU의 3.2%만 사용하는 낭비가 된다.

## MultiProgrammed Batch Systems
> Program을 중단시키고 다른 프로그램을 실행시키는 작업이 가능하게 되었다.
→ 중간에 Program을 바꿀 수 있게 되었다.

### MultiProgramming
#### multitasking
> 하나의 작업이 I/O 작업을 위해 기다려야 할 때 CPU가 다른 작업을 할 수 있는 것

#### MultiProgramming에서 중요한 조건
1. 실행하려는 프로그램 A, B, C가 모두 동시에 메모리에 있어야 한다.
⇒ 메모리가 나뉘어질 수 있어야 한다.
2. 중간중간 OS가 개입해 실행하는 프로그램을 다른 프로그램으로 바꿀 수 있어야 한다.
 (프로그램 상태를 save, restore)

A Program 실행
↓
A의 I/O 작업 → OS 개입
↓
B Program 실행
↓
B의 I/O 작업 → OS 개입
↓
C Program 실행 
↓
C의 I/O 작업 → OS 개입

![](https://velog.velcdn.com/images/mini_mouse_/post/56fd1ee0-2abf-4969-ab9a-7aa3fbe95a6b/image.png)

#### 아직 Interactive하지 않다. (상호작용 X)
→ I/O가 일어나지 않으면 프로그램이 변경되지 않는다.

User가 컴퓨터 앞에 앉아 있을 수 있을 때는 Time Sharing System이 실행되고 난 이후이다.


## Time Sharing Systems
>일단 time slice 단위로 시간을 나누고 timeout이 될 때까지 실행하다가 다른 프로그램을 실행시킨다.

1. 당연히 여러 프로그램들이 동시에 memory에 올라가 있어야 한다.

2. I/O 작업을 할 때도 프로그램이 변경된다. 

### Q. Multi Programming 시스템은 TimeSharing 시스템이다.
→ 맞을 수도 있고 아닐 수도 있다.

### Q. TimeSharing 시스템은 Multi Programming 시스템이다.
→ O
단, TimeSharing 시스템과 Multi Programming 시스템은 프로그램이 바뀌는 시점이 다르다.
- TimeSharing 시스템 = 시간에 의해서 프로그램이 바뀐다.
- Multi Programming 시스템 = I/O 입출력에 의해서 프로그램이 바뀐다.

||**Batxh MultiProgramming**|**TimeSharing**|
|------------------|-------------|------------------|
|**주된 목적**|CPU의 사용도를 최대화 하는 것|**Response time** 을 최소화 하는 것|
||I/O가 없으면 그냥 계속 기다려야한다.|- Time slice 조정이 매우 중요하다. <br>- 너무 짧아도 안되고 너무 길어도 안된다.<br>→ 너무 짧으면 OS가 너무 끊임없이 끼어들게 된다.|

# Major Achivements of OS
OS가 하는 주된 역할들
→ 정리된 것들이다. = 모든 OS들은 방법은 달라도 모두 밑의 기능들을 가지고 있다.

## 1. Process
>실행 중인 프로그램

1. 컴파일 → 이진코드로 하드디스크에 저장이 되어 있다.
이 프로그램을 실행시키면 메모리에 올라가서 실행이 되게 된다.

2. 실행하고 있는 프로그램을 OS가 Process라는 형태로 관리한다.

⇒ OS가 하는 일 중에 가장 중요한 일이 우리의 프로그램을 정확하고 효율적으로 실행시키는 것이다.

## 2. Memory Management
1. 메모리는 모든 프로그램을 실행할만큼 크지 않다.
→ 메모리를 여러개로 잘라서 프로그램 여러개를 동시에 집어 넣어야 한다.

2. 메모리 크기가 아무리 커도 그것보다 더 큰 프로그램이 존재할 수 있다.

### Virtual Memory 방식
>항상 프로그램의 일부만 갖다가 메모리에 넣고 실행을 하다가 다른 부분이 필요하면 그때 그때 메모리에 가져온다.

## 3. Information protection and Security
1. 프로그램은 자신에게 할당된 메모리 영역만 access해야 한다.
2. 프로그램은 자신에게 할당된 자원만 access해야 한다.
3. 다른 사람의 메모리 영역이나 다른 사람의 자원을 마음대로 가져다가 쓰면 안된다.

4. 당연히 이 시스템 안에는 이 시스템을 사용해도 좋은 User들외에 다른 User들은 들어 올 수 없다.

## 4. Scheduling and Resource management
### Scheduling
>CPU가 하나이든 여러개이든 시스템에서 동시에 여러개의 프로그램을 실행시키면, 당연히 이 프로그램을 실행시키는 순서가 존재한다.
각각의 프로그램을 얼만큼 실행할지도 정해 놓아야 한다.
이를 OS가 관리하는 것을 `Scheduling` 이라고 한다.

---
# Modern Oprating Systems
정리가 되어 가는 중인 시스템들이다.

## 1. Microkernel Architecture
옛날엔 OS가 작았기 때문에 `OS = Memory` 였지만,
요즘은 OS가 크기 때문에 OS 전체가 Memory에 들어올 수 없다.
⇒ 프로그램 `Module` 화

>**항상 메모리에 있어야 하는 부분**을 굉장히 작게 최소화 시켜서 `Microkernel` 이라고 부른다.
나머지 부분들은 **OS 작업별로 다 나누어서 여러개의 프로세스로 구현**한 것이 `Microkernel Architecture` 이다.

### Microkernel Architecture의 장점
OS가 계속 바뀔 때, `Module` 화가 되어 있기 때문에 `Update` 하고 `Debuging` 하기가 쉽다.

### Microkernel Architecture의 단점
OS를 실행하는데 걸리는 시간이 길어진다.

→ `kernel` 을 제외한 별도의 `program` 에 `access` 를 해야하는데 이 때마다 `OS` 가 **Switching(save&restore)** 작업을 해야한다.

## 2. Multithreading
### Thread
>동시에 실행가능한 함수들

프로그램을 작성할 때 A함수, B함수, C함수가 존재할 때, 이 세 함수가 동시에 실행할 수 있는 경우가 존재한다.

순차적 실행 X → 동시 실행 O ⇒ 실행 속도 증가

## 3. SMP Machine (Symmetric multiprocessing)
SMP Machine은 여러개의 CPU를 사용한다.

### Symmetric
>여러 CPU에서 동시에 OS를 실행시킬 수 있다.

여러 CPU에서 동시에 OS를 실행하면 당연히 충돌하는 경우가 존재한다.

예를 들면, 내가 메모리 1000~2000번지를 A프로그램에 할당하려는데, 다른 프로그램B에도 1000~2000번지를 할당하려고 하면 같은 공간에 두 개의 프로그램이 할당되려는 상황이 발생할 수 있다.

⇒ 이런 상황이 발생하면 안되기 때문에 `Symmetric` 하게 돌아가는 OS들은 당연히 제어가 필요하다. → **concurrency control**

### Concurrency control
>**동시에** 접근이 가능한 자원에 대해서 **순차적**으로 접근하도록 Control이 되어야 한다.

## 4. Distributed Operation System
SMP 머신은 컴퓨터 하단 안에 CPU 여러개(10개, 100개, ...)가 들어 있다.
→ 비쌈

>각각의 CPU하나와 OS를 가진 독립적인 컴퓨터들을 **네트워크에 연결**하여,
하나의 컴퓨터 처럼 사용하는 것을 **Distributed Operation System**이라고 한다.

각각의 OS에 Layer를 하나 더 씌운다.
⇒ 두 단계 OS를 가지게 한다.

---
## 5. Object-Oriented design
module화된 Program들을 사용할 수 있어서 update에 용이하다.

---
# Windows Architecture
1. 효율성을 중요시 한다.
2. Microkernel 사용

![](https://velog.velcdn.com/images/mini_mouse_/post/98b0a793-f95f-4233-a950-15a3ee7a1eeb/image.png)

---
# UNIX Architecture
1. 공정성을 중요시 한다.
2. Microkernel 사용 X, 전부가 OS
→ 엄청 오래된 기능들
→ 별도의 프로세스로 나누어 사용을 안함
⇒ 속도가 매우 빠르다.

![](https://velog.velcdn.com/images/mini_mouse_/post/da937874-6133-4238-814e-593adebf51db/image.png)

---
# Modern UNIX Architecture
Microkernel 사용 O

![](https://velog.velcdn.com/images/mini_mouse_/post/4fbcb9ad-2b2a-48e7-aae6-0b2ca08a5ca0/image.png)

---
# Linux Kernel Components
Microkernel 사용 X, 전부가 OS
→ 엄청 오래된 기능들
→ 별도의 프로세스로 나누어 사용을 안함
⇒ 속도가 매우 빠르다.

![](https://velog.velcdn.com/images/mini_mouse_/post/24c26c19-d3fa-4433-bb04-c25cb4368104/image.png)

---
# Android System Architecture
Microkernel 사용 O
![](https://velog.velcdn.com/images/mini_mouse_/post/36702058-bcbf-4aa3-9247-2adee286175c/image.png)
