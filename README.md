# 오픈소스SW개론 과제를 위한 파일
---
### 1. 리눅스 명령어 : top, ps, jobs, kill 명령어 조사하기
### 2. vim 에디터에서 매크로 사용방법에 대하여 조사하기 (q , @)
### 제출할 때는 github 페이지 링크와 pdf 파일을 같이 제시
---

### 1. 리눅스 명령어 : top, ps, jobs, kill 명령어 조사하기

#### 1-1 top 명령어
top 명령어 사용 사진
![top](https://user-images.githubusercontent.com/95165994/171168093-84c05081-f932-457c-aac6-cd7a64a1ca57.png)

시스템의 상태를 파악 가능하게 해주는 명령어로서 기본적으로 top 명령어만 사용할 경우 약 3초 간격으로 화면을 갱신하여 정보를 출력한다.
밑의 ps와는 차이점은 top 명령어는 proc에서 일정주기로 합산하여 정보를 출력한다.

top 명령어의 추가적인 명령어 
1) shift + p : CPU의 사용률이 가장 높은 USER 부터 내림차순으로 표시한다.
2) shift + m : 메모리의 사용률이 가장 높은 USER 부터 내림차순으로 표시한다.
3) shift + t : 프로세스가 돌아가고 있는 시간의 순서로 표시한다.
4) a : 메모리의 사용량에 따라서 정렬하는 명령어
5) k : USER 삭제 멍령어, k를 누르고 삭제하고 싶은 USER의 PID를 입력해서 해당 USER를 삭제할 수 있다.
6) 1 : CPU의 CORE의 사용량을 보여주는 명령어

#### 1-2 ps 명령어
ps 명령어 사용 사진
![top](https://user-images.githubusercontent.com/95165994/171170847-ae228acb-71f5-4b98-8c32-45be2d1f5719.png)

현재 실행중인 프로세스의 목록과 상태를 보여주는 명령어로서 추가하는 옵션에 따라 표시하는 결과와 종류가 달라진다. 기본적으로 단독으로 사용시 PID, TTY, TIME, CMD의 정보만 출력하고 옵션들을 덧붙어서 출력하는 정보의 종류를 변경할 수 있다.
위의 top 명령어와는 차이점은 ps 명령어를 실행한 시점에서 proc의 정보를 검색하여 정보를 출력한다.

ps 명령어의 추가적인 명령어
1) -A : 모든 프로세스를 출력한다.
2) -a : 터미널에 종속되지 않은 모든 프로세스를 출력한다.
3) -e : 커널 프로세스를 제외한 모든 프로세스를 출력한다.
4) -f : 풀포맷으로 출력한다.
5) -r : 현재 실행중인 프로세서를 출력한다.
그 외에도 grep이나 more, aux, ax, el, fp등 다양한 명령어를 입력하여 출력하는 정보를 다르게 할 수 있다.

#### 1-3 jobs 명령어
jobs 명령어 사용 사진
![jobs](https://user-images.githubusercontent.com/95165994/171172920-edeb1085-175d-4c27-8de1-4586ae20598a.png)

작업의 상태를 표시하는 명령어로서 현재 쉘의 셰션에서 실행한 백그라운드 작업의 목록이나 작업이 중지된 상태를  출력한다.
사진의 Stopped는 작업의 일시 중단을 뜻하며 진행 중은 Running, 작업 완료는 Done, Stopped의 뒤의 ()괄호가 들어간건 괄호안의 시그널이 작업을 일시 중단했음을 알려준다.

jobs 명령어의 추가적인 명령어
1) -l : 프로세스의 그룹 ID를 상태 필드 앞에 출력한다.
2) -n : 프로세스의 그룹 중에 대표 프로세스 ID를 출력한다.
3) -p : 프로세스의 각 ID에 관하여 한 행씩 출력한다.
4) kill : 프로세스에 종료 시그널 보내기, -9의 경우는 강제 종료이며 kill -PID로 해당 프로세스만 종료할 수 있다.

#### 1-4 kill 명령어
kill 명령어 사용 사진
![kill](https://user-images.githubusercontent.com/95165994/171177639-fd40388d-6468-473f-af52-77219e320349.png)

리눅스의 프로세스를 종료 및 강제종료 할 때 사용하는 명령어로서, 보통 ps로 종료시킬 프로세스의 PID를 얻은 후 kill [시그널] [PID] 형식으로 사용한다. 시그널의 경우 종료는 15, 강제종료는 9로 시킬수 있다.

위의 사진에서는 kill -15 135 으로 사용했다.(다만 실행중인 프로세스가 아니기에 kill 명령어를 사용한 후 ps -l로 확인해도 별 차이가 없었다.) 

시그널 15(종료)를 사용해도 프로세스가 종료되지 않을 경우 시그널 9(강제종료)를 사용하나 강제종료할 경우 즉시 프로세스가 종료되기에 데이터의 유실이나 리소스의 문제가 생길 수 있다.

---

### 2. vim 에디터에서 매크로 사용방법에 대하여 조사하기 (q , @)

#### 매크로란?
매크로는 특정한 움직임이나 입력을 키에 저장하여 같은 명령을 반복하는 기능이다.
q + [매크로 이름] 으로 매크로를 시작하여 q를 눌려서 매크로를 종료시킨다.
@[매크로 이름]를 입력하여 매크로를 실행시킬 수 있으며(매크로 1회 실행), [숫자]@[매크로 이름]으로 숫자에 원하는 숫자를 입력하여 원하는 만큼 반복 시킬 수 있고 @@으로 방금 실행된 매크로를 실행시킬 수도 있다. 
