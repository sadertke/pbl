# git 예제 
---

1. git 로컬저장소 만들기 
 * git init   
'''bash
	git init

'''
 디렉토리에 .git 디렉토리가 생긴다 
 * git status
'''bash
	git add [파일이름]
	git status
'''
 tracked,untracked  로컬에서 스테이징이 되었으면 전자  아니면 후자이다
 git add 명령어를 이용해  tracked 로 바꾸고 로컬저장소에 스테이징한다
 git remove --cached [파일이름] 을 통해 로컬저장소에서 untracked 시킬수있다
