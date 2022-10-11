## [Git] Pull Request 날리기

### ⚡️ 코드 기여 원리 (Fork와 Pull Request)

만약 **A**와 **B**라는 깃헙 리포지토리가 있다고 하자.
이때 **A**가 **B**개발자의 프로젝트가 마음에 들어 같이 프로젝트에 참여해 기여자로서의 공헌을 하고싶어한다.
하지만 내가 다른 사람의 저장소에 있는 코드를 수정하거나, 다른 사람의 저장소의 코드를 내가 수정하려면 `관리자가 직접 나를 기여자(Contribute)로 등록`해야한다.

근데 모든 사람들을 다 기여자로 등록할 수는 없으니,,,

이때 사용하는 것이 `Fork`다 !!

### 🍴 Fork

포크로 쿡 찔러 가져오듯 **다른 사람의 저장소에 있는 레포지토리를 내 원격 저장소, 깃허브로 가져오는 것**이다.

즉, A가 B의 레포지토리 중 하나를 Fork하였다면, A의 github에 아까 fork한 레포지토리가 그대로 가져와지게 됨..!!

그 후, Fork 해 온 원격 레포지토리를 내 로컬에 **Clone** 한 후 코드를 수정하면 된다 !



> **Fork** : 레포지토리를 `원격 저장소`에 복사

> **Clone** : 레포지토리를 `로컬 저장소`에 복사



이제 A 개발자가 코드를 수정하고, 아까 fork 했던 A의 원격 저장소에 commit 한 뒤, B의 레포지토리에도 반영이 됐으면 좋겠다는 생각이 들면 `Pull Request`를 보내는 것이다.

그러면 B가 코드 리뷰를 하고 문제가 없으면 자신의 메인 브랜치에 **merge**를 하는 식으로 프로젝트를 기여하게 되는 것이다.

### 🪢 Pull Request(PR)

쉽게 얘기하자면, 내가 수정한 코드가 있으니 내 **branch**를 가져가서 확인 후, `병합해달라고 요청을 하는 것`이라고 생각하면 된다! PR을 통해 코드 충돌을 최소화할 수 있고 push 권한이 없는 `오픈 소스 프로젝트에 기여할 때` 많이 사용한다.

> ⭐️ **pull request 사용 단계 !**
> 
1. 내 원격 레포지토리에 Fork
2. clone 설정
3. remote 설정
4. branch 생성
5. 수정 작업 후 add, commit, push (나 뿐만 아니라 다른 기여자(팀원)이 소스를 수정했다면 fetch로 코드를 가져와 충돌을 해결)
6. Pull Request 생성
7. Merge Pull Request
8. Merge 이후 동기화 및 branch 삭제

### 1. 원본 저장소를 Fork 하기

자신이 기여하고 싶은 팀원(혹은 다른 사람)의 리포지토리의 우측 상단에 `Fork` 버튼을 누르고 `Create fork` 누르기!

<img width="674" alt="스크린샷 2022-10-11 오후 9 37 09" src="https://user-images.githubusercontent.com/94473725/195108769-1304b655-b640-4f65-b5db-ea544101e078.png">


Fork가 완료되면 **내 원격 저장소**에 해당 레포지토리가 **복제**된다.

### 2. Fork한 저장소를 로컬로 Clone 하기

이제 제대로 작업하기 위해 포크한 원격 저장소 소스를 그대로 내 로컬 컴퓨터에 복사해 추가!

<img width="577" alt="스크린샷 2022-10-11 오후 9 41 51" src="https://user-images.githubusercontent.com/94473725/195108960-0ae82e0a-a509-44ff-817a-640271315c7b.png">


Code 버튼을 눌러 URL을 복사하고 아래의 명령어를 실행!

```
$ cd <file>   // 파일 이동
$ git clone <복사한 레포지토리 URL>
```

**📝  ex)**

```
$ cd pull_request
$ git clone https://github.com/aaa/bbb.git
```

### 3. 원본 저장소 Remote 설정

레포지토리를 clone하면 `origin` 이라는 이름으로 remote url이 **내 원격 저장소**로 기본 설정되어있다.

하지만 내 원격 저장소 뿐만 아니라, `포크했던 원본 저장소`도 remote로 등록해주는 게 좋다. 나중에 원본 저장소 내용과 동기화 하기 위해 사용할 것이기 때문이다.

```
// 원본 저장소 remote 등록
$ git remote add <별명> <원본 저장소 url>
// 원격 저장소 확인
$ git remote -v
```

📝 **ex)**

```
$ git remote add foo https://github.com/aaa/bbb.git
$ git remote -v
```

 `$ git remote -v`를 하면 대게 origin 2줄(fetch, push)과 방금 본인이 별명으로 칭한 저장소(위의 예시에서는 foo) 2줄(fetch, push)이 뜬다.

### 4. Branch 생성

현업에서 팀으로 일할 때 브랜치 분기는 필수이다.

예를 들어, 버그를 고치는 작업을 한다고 하면 `bug-fix`라는 branch를 만들어 코드를 고친 후, `push` 하면 `master` 브랜치의 코드는 그대로 유지된 채로 **bug-fix 브랜치만 최신 코드가 되게 된다.**

그래서 만약 bug-fix 브랜치에서 수정된 코드가 사이드 이펙트를 발생한다고 해도 master에 코드가 남아있어서 이전 코드로 되돌리기 쉽다!

👉 현업에서는 branch를 만들어 작업한 뒤, 다시 작업이 완료되면 삭제하는 식으로 진행하는 경우가 많음!

다음과 같이 개발용 branch를 만들어 진행한다.

```
// 브랜치 생성
$ git branch <branch 이름>
 
// 브랜치 이동
$ git checkout <branch 이름>
 
// 브랜치 생성후 이동 (단축 명령어)
$ git checkout -b <branch 이름>
 
// 브랜치 리스트
$ git branch
```

**📝  ex)**

```
$ git branch LEEDH
$ git checkout LEEDH
$ git checkout -b LEEDH
$ git branch
```

`$ git branch` 를 하게 되면 아래와 같이 현재 브랜치 좌측에 *가 붙어서 띄워진다.

<img width="577" alt="스크린샷 2022-10-11 오후 9 41 51" src="https://user-images.githubusercontent.com/94473725/195109026-fa800720-62a5-40d9-8b88-5a1ae89d0cc0.png">


### 5. 코드 작업 후 Add / Commit / Push

코드를 수정하거나 기능 추가 작업이 완료되면, 자신의 깃헙 레포지토리(origin)에 add, commit, push 하여 반영한다.

```
// 현재 위치에서 새 파일 및 수정사항 적용
$ git add .
// 변화 기록하기 (commit : history의 한 단위)
$ git commit -m "본인이 수정한 작업에 대한 멘트 작성"
// 현재까지의 commit 내용을 github에 넣기
$ git push origin <브랜치명>
```

📝 **ex)**

```
$ git add
$ git commit -m "test입니다."
$ git push origin LEEDH
```

이렇게 `push` 한 후, 본인 깃헙 레포지토리에 접속해보면 내가 변경한 사항이 반영되어있음.

### 6. Pull Request 생성

이제 github 저장소 상단을 보면 초록색으로 **`Compare & pull request`** 버튼이 활성화 되어있는 것을 볼 수 있다!

이 버튼을 누르고, PR 메시지를 작성한 후 **`Create pull request`** 버튼을 누르면 풀 리퀘스트를 생성하게 된다.

### 7. Merge Pull Request

Pull Request를 받은 원본 저장소 관리자는 코드 변경 내용을 확인하고 `Merge` 여부를 결정하게 된다.

원작자가 승인하면 Merge Confirm으로 원본 저장소에 변경된 사항이 반영되고, pull request의 상태는 `closed`로 변경된다. 만일 마음에 들지 않으면 `Reject` 된다,,

### 8. Merge 이후 동기화 및 Branch 삭제

원본 저장소에 Merge가 완료되면 로컬 코드와 원본 저장소의 코드를 동기화 한다.

그리고 작업하던 로컬의 branch는 더 이상 사용을 안하기 때문에 삭제한다.

```
// 코드 동기화
// 원본 remote 와 동기화
$ git pull foo
 
// branch 삭제 (용무가 끝난 브랜치 삭제)
$ git branch -d foo
```

이렇게 나중에 추가로 작업할 일이 있으면 `git pull` 명령을 통해 원본 저장소와 동기화를 진행하고 위의 과정을 반복하면 된다 !

---

끝
