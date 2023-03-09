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