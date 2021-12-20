jsjune  
avraskio@gmail.com  

clear : 터미널창 내용 지움  
exit : 터미널창을 종료  


pwd : 현재위치  
ls : 현재 디렉터리 파일 확인  
ls -la : 숨긴파일과 디렉터리의 상세 정보표시  
-l은 디렉터리의 상세 정보표시   
-a는  숨긴파일과 디렉터리 표시  
-r은 파일의 정렬 순서를 거꾸로 표시  
-t는 파일 작성 시간순으로 표시  


cd : 디렉터리 사이를 이동할 때 사용  
cd .. : 한 단계 위의 디렉터리로 이동   
cd '하위 디렉토리' : 하위 디렉터리로 이동   예) c/ -> c/Users  
cd ~ : 처음에 출발했던 디렉터리로 돌아감  
cd - : 최상위 디렉토리 이동  
~ : 현재 접속 중인 사용자의 홈 디렉터리를 가리킵니다.  
./ : 현재 사용자가 작업 중인 디렉터리  
../ : 현재 디렉터리의 상위 디렉터리  


mkdir test : 테스트 디렉터리 만들기  
rm -r test : 테스트 디렉터리 삭제하기  
mkdir 폴더명 : 폴더 만들기  
vim test.txt -> i 눌러서 입력 esc 눌러서 종료  
cat test.txt -> 텍스트 문서 내용 확인  
:w : 편집 중이던 문서를 저장  
:q : 편집기를 종료  
:wq : 편집 중이던 문서를 저장하고 종료  
:q! : 문서를 저장하지 않고 편집기를 종료  
cat 파일 : 파일의 내용을 화면에 표시  
cat 파일1,파일2 ... 파일n>새파일 : 파일 n개를 차례로 연결해서 새로운 파일을 만듦  
cat 파일1>>파일2 : 파일1의 내용을 파일2 끝에 연결  


git init : 이 디렉터리에 저장소를 만들기 위해 사용. 깃을 사용할 수 있도록 디렉터리를 초기화하는 것  
git status : 깃 상태를 확인  
git add 파일명 : 파일을 스테이징(스테이지에 올린다)  
git add . : 모든파일을 스테이징  
git commit -m "메시지내용" : 스테이지에 올라온 파일 커밋    
git log : 커밋 기록 자세히 살펴보기  
git commit -am "메시지내용" : 한 번 커밋한 파일이라면 git commit 명령에 -am옵션을 붙여서 스테이징과 커밋을 한꺼번에 처리할 수 있다.  
git diff : 최근 버전과 작업 폴더의 수정 파일 사이 차이를 보여준다  
git log --stat : 가장 최근의 커밋부터 순서대로 커밋 메시지와 관련 파일이 나열된다. (파일 3개를 동시 커밋할경우 파일 3개 확인 가능)  
git commit --amend : 방금 커밋한 메시지 수정하기  
git checkout -- 파일명 : 작업 트리에서 수정한 파일 되돌리기  
git reset HEAD 파일명 : 스테이징 되돌리기  
git reset HEAD^ : 최신 커밋 되돌리기  
git reset HEAD~'갯수' : 최근 '갯수' 만큼 커밋 취소  
git reset --soft HEAD^ : 최근 커밋을 하기 전 상태로 작업 트리를 되돌린다.  
git reset --mixed HEAD^ : 최근 커밋과 스테이징을 하기 전 상태로 작업 트리를 되돌린다. 옵션 없이 git reset 명령을 사용할 경우 이 옵션을 기본으로 작동한다.  
git reset --hard HEAD^ : 최근 커밋과 스테이징, 파일 수정을 하기 전 상태로 작업 트리를 되돌린다. 이 옵션으로 되돌린 내용은 복구할 수 없다.  
<특정 커밋으로 되돌리기>  
git reset --hard '커밋 해시' : HEAD가 복사한 커밋 해시 위치로 옮겨짐 (커밋 해시 위의 파일들은 커밋 삭제됨)  
git revert '커밋 해시' : 지정한 커밋 해시의 변경 이력을 취소함  


git branch : 브랜치가 뭐 있는지 확인  
git branch : 브랜치 만들기  
git branch "브랜치명" : 브랜치 사이 이동하기  
git log --oneline  
git log --oneline --branches  
git log --oneline --branches --graph  
git log "브랜치명".."브랜치명" : 브랜치 사이의 차이점 알아보기  
git merge "브랜치명" : 브랜치 병합  
git branch -d "브랜치명" : 브랜치 삭제  


1. Git bash 실행  
2. cd로 깃 허브에 올리고 싶은 폴더로 이동   
3. git init (폴더 깃으로 초기화)  
4. git add 파일명 (깃 허브에 올릴 파일 추가해주기)   
5. git commit -m 메세지    
6. git remote add origin 복사한주소 : 원격 저장소에 연결하기(처음 연동시킬 때 사용, 연동시킨 이후에는 생략)  
7. git push -u origin master(제일 처음 원격 연동이라면 이렇게 써줘야하고 아니라면 git push로 가능)  


git remote add origin 복사한주소 : 원격 저장소에 연결하기(처음 연동시킬 때 사용, 연동시킨 이후에는 생략)  
git remote -v : 원격 저장소에 제대로 연결됐는지 확인하기  
git pull origin master(git pull만 입력해도 된다) : 원격 저장소에서 소스 파일을 가져오기  
git clone "주소" : 원격저장소를 복제하여 내가 원하는 폴더로 가서 깃헙파일들 불러오기  
git remote remove origin : 기존 레파지토리 remote 제거  
  
