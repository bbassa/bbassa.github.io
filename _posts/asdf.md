# __GIT Command Line 명령어 정리__
#### __1. 환경설정__
> - git config --global user.name "사용자명"<br/>
> -사용자명을 등록합니다 (필수)
> 
> - git config --global user.email "이메일주소" <br/>
> -이메일 주소를 등록합니다. (필수)

#### __2. 기본명령어__
> -  git init<br/>
> -현재 디렉토리에 git 저장소를 생성합니다.
> 
> - git status<br/>
> -파일의 상태를 확인합니다.
>
> - git add 파일명<br/>
> -Untracked files을 Staging Area에 올립니다.
> 
> - git commit -m "커밋 메시지"<br/>
> -Staging Area에 있는 파일을 로컬저장소의 HEAD에 반영합니다.
> (아직 원격저장소에는 반영이 안된 상태)
>  ![Alt text](/uploads/git/gitFile.png)
>
> - git push<br />
> -로컬저장소의 HEAD안에 있는 파일을 원격저장소에 반영합니다.


#### __3. 원격저장소__
> - git clone 저장소주소<br/>
> -원격저장소를 복제하여 저장소를 생성합니다.
> 
> - git remote add 저장소이름 저장소주소<br/>
> -새로운 원격 저장소를 추가합니다.

> - git remote<br/>
> -추가한 원격저장소의 목록을 확인합니다.
> 
> - git remote -v <br />
> -원격저장소 이름과 주소를 함께 확인합니다.<br />
> ![Alt text](/uploads/git/remote2.png) 
> 
> - git remote rm 저장소이름<br />
> -원격저장소를 삭제합니다.<br />
> ![Alt text](/uploads/git/remote3.png)

#### __4. Branch & Merge__
> - git branch <br/>
> -브랜치의 종류와 현재 작업중인 브랜치를 확인 할수 있습니다.<br/>
>  ![Alt text](/uploads/git/branchFile.png)
>  
> - git branch 브랜치명<br/>
> -새로운 브랜치를 생성합니다.<br/>
> ![Alt text](/uploads/git/branchFile2.png) 
> 
> - git branch -d 브랜치명<br/>
> ![Alt text](/uploads/git/branchFile3.png) 
> 
> - git merge 브랜치명<br/>
> -현재 작업중인 브랜치에 다른 브랜치에서 작업한 내용을 추가합니다. 
> 
> - git checkout 브랜치명<br/>
> -과거의 작업 폴더로 되돌아간다. 
