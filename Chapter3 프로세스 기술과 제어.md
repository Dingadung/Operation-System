OS는 프로그램을 정확하게, 효율적으로 관리해야한다.
`Application Program` 을 관리하는 것이 첫 번째 일이다.

OS는 시스템 안에서 실행되는 모든 프로그램을 관리할 때 어떤 형태의 자료구조 안에 넣고 관리를 하는가를 알아보도록 하자.

# Process
>실행중인 프로그램

프로그램이 실행되면 OS가 이를 관리해야한다.

OS 입장에서는 프로그램이 어디까지 실행했는지가 중요하다.

프로그램이 실행을 시작하면 OS가 얘를 관리를 해야한다. 
프로그램들을 어떠한 형태로 관리를 할 것이다. 
그럼 OS 입장에서 프로그램을 어떠한 형태로 관리하느냐?

## 1. sequence of instructions
한 줄 한 줄 프로그램을 실행하다보면 OS에게 중요한 것은 지금 어디까지 실행시켰는지가 매우 중요하다. 프로그램을 항상 save하고 restore하는 작업을 진행해야한다.

## 2. Current state
OS 시스템 안에 있는 Process를 상태에 따라서 다른 곳에다 보관을 한다.

- 이런 상태 → 저쪽 Queue에 넣기
- 저런 상채 → 다른 Queue에 넣기

## 3. Associsted set of system resources 
1. 프로그램 실행 
2. 메모리 요청
(메모리 x번지 ~ y번지까지 사용할 수 있도록)
3. 실행을 하며 여러가지 시스템 안에 있는 자원을 이용할 것이다.
(OS는 누가, 어떤 자원을 사용하는지 관리한다.)

OS는 저런 내용들을 자료구조에 잘 적어 놓아야 한다.

---
# Process Elements
프로세스는 다음의 것들로 구성되어 있다.

1. Program code
2. A set of Data
3. Stack
4. Process control block(PCB)

## 1. Program code
프로세스는 당연히 코드로 이루어져 있다.

## 2. A set of Data
여기서의 `Data` 는 전역변수나 `static` 변수를 저장하는 공간이다.

`local` 변수는 `Stack` 에 저장한다.

## 3. Stack
`stack` 에서는 함수가 호출될 때마다 그 함수에서 사용할 변수들을 저장할 공간이 쌓였다가, 
`return` 하면 다시 사라지게 된다.
또한 저장 공간뿐만 아니라 어디로 리턴할지까지 적혀있다.

![](https://velog.velcdn.com/images/mini_mouse_/post/3f130173-a224-4c15-94c3-92f2b96b7294/image.png)


`main` 함수 변수 공간이 `stack` 에 생성된다.
변수 5개를 위한 공간이 생성된다.

![](https://velog.velcdn.com/images/mini_mouse_/post/a818784e-1a42-422b-bb15-1aafd18536c8/image.png)

## 4. Process control block(PCB)
>우리의 프로세스가 실행을 시작해서 끝날때까지,
OS가 관리해야하는 다양한 정보들을 저장해놓은 것이다.

1. PCB가 저장하는 다양한 정보들:
identifier(id), state, priority, pc, memory pointer, context data, I/O status information, accounting information, ... 

2. 프로그램은 실행하다 멈췄다를 반복할 것이다. 
이 과정에서 필요한 모든 정보를 `OS` 가 잘 저장을 해 놓아야하고 이러한 정보들이 `PCB` 이다.

3. `PCB` 는 `OS` 가 만들고, `OS` 가 관리한다.

우리의 프로그램이 컴파일되어 바이너리 형태의 실행형태로 하드디스크에 저장이 되어 있는데, 실행을 시작하면 이 프로그램이 메모리로 올라오게 된다.


### Q. 메모리에 있는 프로세스와 실행파일이 같냐?
→ X

메모리에 있는 프로세스 != 실행파일

- 실행파일
코드와 데이터만 존재한다. 
즉, 전역변수와 스태틱변수를 저장하는 데이터 영역은 원래 컴파일 할 때부터 실행파일 안에 존재한다. 
- 프로세스
실행파일이 메모리로 올라오며 원래 있던 값들에 stack영역과 PCB영역이 추가된다.

실행파일의 크기 < 프로세스의 크기

|실행파일|프로세스|
|-------|-------|
|프로그램 코드, 데이터 영역(전역변수와 스태틱 변수를 저장)만 존재한다.|원래의 값 + stack영역과 PCB영역|

### 용어 정리 중요!
>1. **Process**: 실행 중인 프로그램이다.
2. **Processor**: CPU
3. **Program**: 실행중일 수도, 실행중이 아닐수도 있는 프로그램 파일이다.

---
# Dispatcher
![](https://velog.velcdn.com/images/mini_mouse_/post/2632d9b1-0515-4cdd-ab44-dcea5c029684/image.png)

위의 그림은 Main Memory 안에 A, B, C 세 Process가 들어 있는 상황이다.
PC가 8000이므로 B 프로그램이 시작되기 직전인 상황이라는 것을 알 수 있다.

## Dispatcher program
1. OS의 일부이다.

2. 프로세스 하나를 실행하고 다른 프로세스로 바꿔주는 역할을 한다.
`Switching` → save&restore 는 당연히 한다.

### Dispatcher의 주 업무
>다음에 어떤 프로그램을 실행할지 결정하는 것이다.
현재 실행하는 프로그램을 얼만큼 실행시킬지를 결정한다.

### Dispatcher program의 목적
>한 프로그램이 CPU를 독점하지 못하게 하는 것이다.
가급적 여러 프로세스들이 CPU를 사용할 수 있게 하는 역할을 한다.
실행하는 프로그램을 계속 바꾸려고 한다.

```
ex) 
A 프로그램 진행 → 
             → B 프로그램 진행?
             → C 프로그램 진행?
             → D 프로그램 진행
             → ? 프로그램 진행?
```

![](https://velog.velcdn.com/images/mini_mouse_/post/fec63ab2-e682-484d-a1fb-ae1472d519a0/image.png)

A program → Timeout ⇒ Dispatcher 작업(OS)
→ B program → I/O Request ⇒ Dispatcher 작업
→ C program → Timeout ⇒ Dispatcher 작업

→ A program → Timeout ⇒ Dispatcher 작업
(B의 I/O 작업이 끝나지 않음)
→ C program → Timeout ⇒ Dispatcher 작업

Timeout은 누구에게나 공평하다.

## 전체적인 View
![](https://velog.velcdn.com/images/mini_mouse_/post/7ced1f03-db08-4b95-83a0-bcd71aaaaef8/image.png)

### Running
파란색 부분은 CPU를 잡고 실행하고 있는 부분이다.

### Ready
연한 회색 부분은 CPU를 주면 실행 가능한 상태이지만,
나 혼자 CPU를 사용할 수 있는 상황이 아니기 때문에 Dispatcher가 CPU를 줄 때까지 기다리는 상태이다.

### Blocked
짙은 회색 부분은 CPU를 줘도 실행이 불가능한 상태이다.
ex) I/O 작업이 끝나지 않은 상태

---
# A Five-State Model
하나의 프로세스의 입장에서 바라본 상태 모델이다.

## New
1. 프로세스가 새로 만들어지는 상태이다. 
(프로세스가 만들어지는 과정에 있는 상태)

2. 오래 걸린다.
	(1) OS가 ID를 부여하고 PCB를 만들고 메모리를 할당하고 프로그램을 불러와야 한다. 
    (2) 프로그램은 보통 하드디스크에 들어있으므로 불러오는데 시간이 걸린다.
(3) 필요한 초기 자원들을 모두 할당해주어야 한다.
⇒ 이 모든것이 할당되어야 이제 실행가능한 `Ready` 상태가 된다.

(ex: 바탕 화면 → Icon 클릭하여 프로그램 실행)

## Running
실행하는 상태

## Not Running
### Ready
1. CPU만 주면 언제든지 실행할 수 있는 상태이다.

2. 실행하다 TimeOut이 되면 다시 Ready 상태로 돌아오게 된다.

### Blocked/Waiting
1. CPU를 줘도 실행할 수 없는 상태

2. 실행하다 I/O작업을 하게되면 I/O 작업이 끝날 때까지 Blocked 상태로 오게 된다.

## Exit
1. 마지막까지 다 실행을 하고 모든 자원을 다 반납하고 기다리다 사라질 때까지 놓여있는 상태이다.

2. 오래걸린다.

---
# 다섯가지의 상태를 갖는 프로세스 모델 그림
## → 그릴 수 있어야 한다. 화살표 방향까지!
![](https://velog.velcdn.com/images/mini_mouse_/post/a15eec5f-cdd8-41c0-a882-a8a181cee3c1/image.png)

1. Ready와 Blocked Queue는 Dispatcer의 확인의 용이성을 위하여 같은 공간에서 대기하지 않는다.
→ 같은 공간에 있으면 다음에 실행할 프로그램을 선택할 때 하나하나 Blocked 상태인지 Ready 상태인지 확인해야 한다.

2. 화살표 방향 중요
    - Blocked → Running X 
    (Blocked는 I/O 작업이 끝나지 않은 상태이다. 즉, 실행할 수 없다.)
    - Blocked → Ready O
    
---
# Single Blocked Queue
![](https://velog.velcdn.com/images/mini_mouse_/post/ee98d323-f691-4966-bd07-7eabfb46e5d6/image.png)

## Ready Queue
1. Ready Queue에는 Ready 상태들의 process들이 줄을 서 있다.

2. Process 전체가 모두 Ready Queue에 들어갈 수 없다.
⇒ Ready Queue에는 ID, Pointer, ...(필요한 최소한의 정보)만 들어가 있다.

3. Dispatcher는 Ready Queue만 확인하면 된다.

## Blocked Queue
1. Blocked 상태의 프로세스들이 줄을 서 있다.

2. I/O 작업을 하고 있는 프로세스들이 들어오게 된다.

---
# Multiple Blocked Queue
![](https://velog.velcdn.com/images/mini_mouse_/post/cfaec159-a8d3-4aa2-beda-edf56e9e85db/image.png)

Single Blocked Queue의 문제점
어떤 프로세스는 printf 작업을 하고 어떤 프로세스는 scanf 작업을 하고
어떤 프로세스는 파일에서 입력이 들어오길 기다리며 모두 blocked queue에서 기다리고 있다.
입출력 작업은 인터럽트로 끝나게 된다.
인터럽트가 오면 어떤 인터럽트가 걸렸는지 확인하고 그것을 처리할 인터럽트 핸들러를 호출한다.
Single Bloced Queue일때는 누가 파일 입력을 요청한 프로세스인지, 프린트를 요청한 프로세스인지 확인하기가 어렵다.
⇒ Device마다 Queue를 가진다.

프로세스가 전부 Blocked Queue로 가게 되면 더 이상 실행중인 Process가 존재하지 않기 때문에 CPU가 쉬어도 되는데,
실제로는 그게 아닌데, 그 프로세스들이 메모리에 올라오지 못하고 있다.

## MultiProgramming level
>여러 프로그램이 메모리에 올라와 있는 상태

우리 시스템의 메모리는 여러 프로그램이 나눠서 사용하는 것이다.

그런데, 만약 동시에 실행하고 싶은 프로세스가 10개이면 메모리를 10개로 나누면 되지만,
만약 동시에 실행하고 싶은 프로세스가 1000개라면 메모리를 1000개로 나누었을 때 너무 작게 나누어져 더 이상 프로세스가 진행이 안되게 된다.

1. 시스템마다 **메모리를 페이지 크기**로 나누어서 사용한다.
→ 실행 파일의 한 페이지(일단 실행할 수 있는 크기)를 메모리에 올린다.

2. 시스템 안에 페이지수가 제한이 되어 있다.
⇒ 즉, **동시에 실행시킬 수 있는 프로그램이 제한**되어 있는 것이다.

ex) 1000개의 프로그램을 실행하고 싶은데 10개의 페이지수 제한이 있으면 10개씩 순차적으로 돌아가며 메모리에 올리며 실행해야 한다.
→ 이 때, **바꾸는 타이밍이 Ready Queue가 비었을 때** 이다.

3. Ready Queue가 비면, 대기하고 있던 그 다음 프로세스들을 메모리로 가져오고 현재 메모리에 있던 프로세스들은 **하드디스크** 로 쫓겨나게 된다.

## Swapping Area
하드디스크에는 Swapping area라고 해서 실행을 하다가 하드디스크로 쫓겨난 프로세스들이 저장이 되어 있다.
![](https://velog.velcdn.com/images/mini_mouse_/post/c041047c-b165-4d3d-bf87-c84bbfe954b0/image.png)

---
# Need for Swapping
I/O작업이 굉장히 느리기 때문에 내가 많은 프로그램을 실행시킨다고 하더라도 굉장히 짧게 짧게 Running을 하다가 전부 I/O를 하러 간다.
따라서 Ready Queue가 비는 상황이 발생하게 된다.

## 정확히 알아둬야할 것
### 1. Swapping Area는 File이 아니다. **Process** 이다.

만약 내가 A, B, C를 하드디스크로 저장하면, PCB, Stack은 모두 사라지게 된다. 
즉, 실행파일에는 프로그램 코드와 데이터는 존재하지만 PCB와 Stack이 존재하지 않는다.
⇒ 따라서 우리는 이 프로그램들을 파일 형태가 아닌, 프로세스 형태로 저장해야 한다.

그래서 하드디스크의 일정한 영역을 파일이 저장되는 영역이 아니라 다른 영역을 `Swapping Area` 라고 해서 **프로세스들을 저장하는 용도**로 사용한다.

Swapping Area에 있는 것들은 파일이 아니라 하드디스크에 저장된 프로세스들이다.

### 2. Blocked Suspend State
`Swapping Area` 로 넘어가기 전의 프로세스들은 모두 `Blocked State` 였지만 하드디스크로 쫓겨나면 더 이상 `Blocked` 라고 불러서는 안된다.
`Blocked` 는 메모리에 올라와 있는데 `I/O` 작업 때문에 실행할 수 없는 상태를 말한다.
하지만 `Swapping Area` 로 넘어가면 하드디스크로 넘어간다.

#### Blocked Suspend State
>`Blocked` 에 있다가 `Suspend` 까지 되어서 하드디스크로 쫓겨났다는 의미이다.

`Blocked Suspend` 로 하드디스크에 한참 있다가 내 I/O작업이 끝나면,
더 이상 `Blocked` 상태가 아니기 때문에 **Ready Suspend State** 로 변경되게 된다.
한참 기다리다 보면, 
`Blocked Suspend` 에서 `Ready Suspend` 로 바뀌게 되고 
나중에 현재 실행 중인 프로그램들이 전부 `Blocked` 가 되어 `Swapping` 할 때가 오면 
`Ready Suspend` 상태에 있던 프로세스는 다시 **하드디스크에서 메모리**로 올라오게 되고 `Ready` 상태가되게 된다.

---
# Process State Transition Diagram with Two Suspend States
## 7개의 상태도(표준 상태도)
![](https://velog.velcdn.com/images/mini_mouse_/post/b439952f-2f31-4d25-bb5a-6d022efecc1a/image.png)

실제로 시스템에서 사용하는 것과는 또 다르다.
실제 시스템은 자신의 시스템에 맞게 조금씩 변경을 시킨다.

### New


---
# 프로그램을 Suspend 시키는 5가지 이유
## 1. Swapping
swapping이 발생하는 경우

process가 `Ready` 상태에 있다가 `Dispatch` 가 되어 `Running` 을 하고 `scanf` 문장을 만나 `Blocked` 가 되었다.

`Blocked` 상태에서 한참을 있었는데,
I/O가 안 끝났는데 OS가 판단했을 때 메모리 공간이 부족하고 `Ready` 상태에 아무 프로세스가 없으면 현재 메모리에 올라와 있는 프로세스들을 하드디스크로 쫓아내 `Blocked Suspend` 상태로 만든다.

`Suspend` 가 되어서 하드디스크에 와서 한 참 기다리다가 I/O 작업이 다 끝나서 `Ready Suspend` 가 된다.
`Ready` 상태로 `Swapping Area` 에서 한참 기다리다가 다시 `Swapping` 을 해서 다시 메모리로 올라가 `Ready` 상태가 된다.

- `Swapping` 에 의한 `Suspension` 에 따라서 `Process` 상태는 다음과 같이 변한다.
>`Blocked` → `Blocked Suspend` → `Ready Suspend` → `Ready`

![](https://velog.velcdn.com/images/mini_mouse_/post/3cdf15da-b070-4d44-b34a-96b915e57642/image.png)


표시된 화살표는 Swapping에 의해서 발생하는 상태변화를 나타낸다.

## 2. Other OS reason
### Ready → Blocked Suspend
우리들이 컴퓨터를 키고 프로그램을 하나 실행시킬 때 작업관리자를 보면
여러 다른 프로세스들이 실행 중인 것을 확인할 수 있다.
이런 프로세스들을 `background/utility` 프로세스라고 한다.

OS가 이 프로세스들을 실행하다가 메모리가 부족해지면, `background` 프로세스들 중 일부를 `Suspend` 시킨다.
그럼 이 프로세스들은 하드디스크의 `Swapping Area` 로 이동하게 된다.

이 프로세스들은 `Ready` 상태에 있다가 `Ready Suspend` 상태로 갈 수 있다.
`Ready` 상태였기 때문에 `Blocked Suspend` 상태로 이동하지 않는다.

![](https://velog.velcdn.com/images/mini_mouse_/post/08e15056-b58c-462e-aad6-4999f9d47924/image.png)

### Running → Ready/Suspend
프로그램을 실행하는데 프로그램이 이상한 행동을 한다.
다른 사람의 메모리 영역을 읽으려고 하거나 다른 사람에게 준 자원을 이용하려고 하는 경우,
이 경우 OS는 이 프로그램을 중지시키고 검사를 해야한다.
검사를 하는 동안 하드디스크의 `Swapping Area` 로 이동시킨다.

이 경우 또한 프로세스가 `Running` 을 하다가 `Ready Suspend` 로 가는 경우이다.

>Process Running → 이상한 행동 → Ready/Suspend 

![](https://velog.velcdn.com/images/mini_mouse_/post/35de1429-ab08-4118-856e-45acc2a17445/image.png)

### New → Ready/Suspend
1. 프로그램 실행
2. `OS` 는 프로그램의 `PCB` 부터 생성한다.
3. 메모리에 공간이 없으면 바로 `Ready/Suspend` 로 들어가서 `Swapping Area` 에서 메모리에 공간이 생길 때까지 대기하게 된다.

![](https://velog.velcdn.com/images/mini_mouse_/post/7b9eb547-d8c2-47a3-a562-aaaed5502b86/image.png)


## 3. Interactive user request
`User` 가 `Suspend` 를 `Request` 한 게 아니라, 
`User` 가 무언가를 `Request` 했는데 그 `Request` 의 결과로 `Suspend` 가 된 상황이다.

## Debugging
실행을 쭉 하다가 `break point` 에서 멈추어서 여러가지 프로그램의 변수의 값들을 확인할 수 있는데, 
`OS` 의 입장에서는 `break point` 에 걸리면 시간이 오래 걸릴 것이라고 예측하여 바로 `Swapping Area` 로 보내버린다.

## 자원 요청
자원을 달라고 프로그램이 요청했는데 그 프로그램을 다른 프로세스가 사용하고 있어서 이 자원을 다른 프로세스가 사용하고 다시 돌려줄 때까지 시간이 걸리기 때문에 `OS` 가 해당 요청을 한 프로그램을 `Swapping Area` 로 보내버린다.


## 4. Timing
시스템을 관리하는 프로그램 중에는 주기적으로 관리를 하는 프로그램이 존재한다.
이러한 프로그램들은 한 번 작업하고 나면 `Swapping Area` 로 보내지게 된다.


## 5. Parent process request
지금까지는 한 프로그램이 하나의 프로세스로 실행되는 프로그램이었다.

프로그램이 실행되면 프로세스 하나가 만들어진다.
한 프로그램 안에서 여러개의 프로세스를 만들 수 있다.

A Process → B Process 생성 
- A Process: Parent Process
- B Process: Child Process

### 동기화
>**여러개의 프로세스**를 만들 때는 **같이 작업**을 하기 위해서인데, 
이 때 동시에 작업이 되는 것이 아니라 대부분의 경우 작업 순서가 존재한다.
우리가 이것을 동기화라고 한다.

즉, A, B Process가 작업하는 동안 C, D, F Process들은 대기해야 한다.
즉, OS가 C, D, F Process들을 `Swapping Area` 로 보내게 된다.

## Suspend의 의미
>메모리에는 동시에 들어갈 수 있는 `Process` 에 제한이 존재하므로
메모리에는 지금 당장 실행할 수 있는 `Process` 만 들어오고,
나머지 프로그램들은 하드디스크의 `Swapping Area` 로 가있으라는 의미이다.

`Ready Queue` 가 완전히 비었을 때가 아니라 널널할 때 `Swapping` 작업을 진행하게 된다.
시스템을 효율적으로 관리하기 위해서 항상 `Ready Queue` 에 일정한 수의 `Process` 들이 있을 수 있도록 작업을 한다.

---
# OS가 관리하는 Queue는 모두 Memory에 존재한다. <br>중요해용
`Ready Queue` 에는 프로세스들이 들어 있는데,
진짜 전체 프로세스들이 들어 있는 것이 아니라, `ID` , `Process Pointer` 만 들어 있고 진짜 프로세스들은 다른 곳에 저장이 되어 있다.

`Ready Queue` , `Blocked Queue` 는 `Memory` 에 들어 있다.
`Ready Suspend Queue` , `Blocked Suspend Queue` 도 `Memory` 에 존재한다.

>즉, **Queue는 모두 OS가 관리하는 Queue들이라 모두 Memory에 존재**한다!
Swapping일 때 쫓겨나는 애는 Process가 쫓겨나는 것이다.

`Queue` 는 `OS` 가 관리하는 자료 구조의 일종이므로 당연히 `Memory` 에 존재하여야 한다.

---
# Blocked Suspend → Blocked
이 화살표가 반드시 있어야 하는 것은 아니다.

`Blocked Suspend` 에 프로세스가 존재하는 상태에서 아직 `I/O` 가 안끝났는데
`I/O` 가 곧 끝날 것 같고 우선순위가 높아서 바로 실행을 시켜야할 때
메모리 공간이 허용이 된다면,
`Blocked Suspend` 에 있는 `Process` 를 `Blocked` 로 메모리로 일단 가져올 수 있다.

![](https://velog.velcdn.com/images/mini_mouse_/post/94810583-5c60-4c5e-9e08-dbf2a25fa094/image.png)
