# git 예제 
---
e
1. git 로컬저장소 만들기 
 * git init   
```bash
	git init

```
 디렉토리에 .git 디렉토리가 생긴다 
2. git 명령어
 * 상태보기
```bash
	git add [파일이름]
	git status
```
 tracked,untracked  로컬에서 스테이징이 되었으면 전자  아니면 후자이다
 git add 명령어를 이용해  tracked 로 바꾸고 로컬저장소에 스테이징한다
 git remove --cached [파일이름] 을 통해 로컬저장소에서 untracked 시킬수있다
 이미 커밋된 파일을 수정하면 modified로 바뀌는데 add 하면 다시추적된다 
  * commit
```bash
	git commit -m "내용"
``` 
  * push 
```bash
	git push origin [브랜치이름]
```
 3. branch 
	* 메인에 병합하기 전에 구현할 코드다발을 따로 빼놓은 버젼 후에 메인에 병합
	* branch 생성
	 ```bash
	  git branch [브랜치 이름]
	  %git branch -d [브랜치 이름] 로컬 브랜치 삭제 
	 ```
	 브렌치에 add commit 한 파일은 메인에 영향을 주지 않는다
	 * branch checkout
	 ```bash
	  git branch checkout [브랜치이름]
	 ```
 	 해당 브렌치를  이용하기 위해선 checkout 을 해주고 사용하면 된다
4. merge
	* 브렌치를 메인에 병합하는 명령어
	* 병합해도 원격저장소에 푸쉬된것은 아니다
