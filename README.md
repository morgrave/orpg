# 로그저장소

## 준비물

- github 회원가입
- git 설치 https://git-scm.com/download/
- Visual Studio Code 설치 https://code.visualstudio.com/
- node 설치 https://nodejs.org/ko/download/

---
## 이 저장소를 복사한다

https://github.com/morgrave/orpg 에 들어간 뒤 위에서 만든 github 아이디로 로그인한다.

![짤](https://raw.githubusercontent.com/morgrave/orpg/master/src/docs/0.jpg)

오른쪽 위에 이렇게 생긴 Fork 버튼이 있으니 누른다. 이어서 나오는 초록색 확인 버튼도 누른다.

![짤](https://raw.githubusercontent.com/morgrave/orpg/master/src/docs/1.jpg)

위 순서대로 눌러서 너만의 저장소에 들어간다.

---

## 복사한 뒤 저장소 설정

![짤](https://raw.githubusercontent.com/morgrave/orpg/master/src/docs/2.jpg)

복사한 저장소 페이지에서 Settings 찾아서 누르고 왼쪽 바에서 Pages를 찾는다.

오른쪽 Source가 None로 되어있으면 gh-pages로 바꾸고 Save한다.

---

## 다운로드

![짤](https://raw.githubusercontent.com/morgrave/orpg/master/src/docs/3.jpg)

복사된 저장소의 초록색 Code 버튼을 눌러서 주소를 복사한다.

![짤](https://raw.githubusercontent.com/morgrave/orpg/master/src/docs/4.jpg)

로그 저장용 폴더에 들어가서 우클릭 하고 Git Bash Here 누른다.

새 창이 뜨는데 당황하지 말고 `git clone https://github.com/(깃헙회원가입한아이디)/orpg.git` 입력

(깃헙회원가입한아이디) 그대로 적지 말고 깃헙 아이디를 적자. 깃헙 아이디가 trpggallery이면 `git clone https://github.com/trpggallery/orpg.git` 이 되겠지?

이러면 로그저장소 폴더가 다운받아진다.

---

## 잘했다! 한 70%는 여기서 떨어져나갔을 것 같다 남은 30%는 힘내자

이제 위에서 다운받은 Visual Studio Code를 실행한다.

![짤](https://raw.githubusercontent.com/morgrave/orpg/master/src/docs/5.jpg)

폴더 열기로 다운받은 orpg 폴더를 선택한다.

![짤](https://raw.githubusercontent.com/morgrave/orpg/master/src/docs/6.jpg)

폴더가 열렸으면 짤에 있는 걸 그대로 누르고

화면 아래에 창이 열리면 토씨 하나 안 틀려쓰고 아래대로

`npm i`

쓰고 엔터

기다렸다가

`npm i -g @angular/cli`

쓰고 엔터

다 끝나면

`ng serve`

을 한 뒤 뭔가 열심히 돌아가는 게 완료되기까지 기다려주자.

완료된 뒤 http://localhost:4200/ 에 들어가면

![짤](https://raw.githubusercontent.com/morgrave/orpg/master/src/docs/7.jpg)

이렇게 샘플 로그가 셋 튀어나온다.

봤으면 명령어들을 입력했던 창에서 Ctrl + C 를 눌러서 끄자.

---

## 로그 업로드 준비

바꿔야 할 설정 파일이 3개 있다.

![짤](https://raw.githubusercontent.com/morgrave/orpg/master/src/docs/8.jpg)

`orpg\.github\workflows\main.yml` 경로에 있는 파일을 Visual Studio Code로 연다.

맨 아래에 보이는 `npm run ng -- deploy --name="waldo" --email="dwaldo@naver.com" --no-silent` 에서 name과 email 뒤에 있는 문자들을 github에 가입할 때 쓴 아이디와 이메일로 바꿔준다.

만약 아이디가 trpggallery이고 이메일이 trpg@naver.com 이라면

`npm run ng -- deploy --name="trpggallery" --email="trpg@naver.com" --no-silent` 으로 바꾸고 저장한다.

다음은 이 둘 `orpg\src\environments\environment.prod.ts` 와 `orpg\src\environments\environment.ts` 

![짤](https://raw.githubusercontent.com/morgrave/orpg/master/src/docs/9.jpg)

`user: "morgrave",` 라고 된 부분을 github 아이디로 갈아준다.

위 예시대로라면 `user: "trpggallery",` 으로 바꾸고 저장하면 된다.

**파일 하나만 바꾸지 말고 둘 다 바꾸자.**

---

## 로그 업로드 준비

다시 아까 열었던 터미널에서 `ng serve` 를 돌리고 비교하면서 보자.

`orpg\src\app\shared\models\campaigns.model.ts` 를 Visual Studio Code로 연다.

앞으로 모든 로그를 업로드할 때는 이 파일만 손대면 된다.

---

## 롤20 로그 집어넣기

(https://raw.githubusercontent.com/morgrave/orpg/master/src/docs/10.jpg)

크롬으로 롤20 들어가서 채팅창 맨위에 보이는 "이 게임의 모든 채팅 내용 보기"

들어가서 "한 페이지로 보기"

(https://raw.githubusercontent.com/morgrave/orpg/master/src/docs/11.jpg)

이 다음이 좀 어려운데 크롬에서 F12를 누르면 나오는 창에서 Element 를 누르고

빨간 원 친 화살표를 누른 다음 로그의 가장 윗부분을 훑으면 오른쪽 창에 `<div class="content">` 라고 적힌 부분이 나온다.

이걸 좌클릭 하고 Ctrl + C로 복사한 뒤

`orpg\src\campaigns\TEST\logs` 에 있는 `1.html`을 열고 Ctrl + A로 전체 선택해서 내용을 지워버린 뒤 방금 복사한 걸 Ctrl + V 로 붙여넣고 저장한다.

저장하고 ng serve가 돌아가는 동안 `http://localhost:4200/` 에 접속했을 때 새로 집어넣은 로그가 나온다면? 잘했다...

---

## 이제 github에 올리기만 하면 됨

github에 들어가서 토큰이란 놈을 발급받는다. https://hoohaha.tistory.com/37 참고

저걸 그대로 따라해서 이상한 영어들로 된 토큰을 발급받고 나면

터미널에서 ng serve가 돌아가는 중이라면 Ctrl + C로 꺼주고 아래에 있는 걸 순서대로 실행한다.


`git remote remove origin`

`git remote add origin https://(너의깃헙아이디):ghp_(아주복잡한ghp뒤에있는토큰들)@github.com/(너의깃헙아이디)/orpg.git`

`git add .`

`git commit -m "test"`

`git push origin master`

두번째 줄에서 좀 바꿔줘야 할 게 많은데 github 아이디가 trpggallery였으면 새로 발급받은 토큰이랑 해서 대충 아래같은 모양이 나올거임.

`https://trpggallery:ghp_dsagfasdfsdafsadasdfsdfdasfsadff@github.com/trpggallery/orpg.git`

이렇게 맨 아랫줄 `git push origin master` 까지 하고 20분 정도 여유롭게 기다린 뒤

팀원들한테 `https://(너의깃헙아이디).github.io/orpg/` 보여주고 잘 나온다고 하면 성공이다.

저렇게 설정해서 성공했으면 다음부터 새로운 로그 넣을 때

`git add .`

`git commit -m "deploy"`

`git push origin master`

이 세 줄만 해주면 된다.

---

## 가이드 쓰긴 했는데 

절대 똑바로 안 될 거야... 한번에 그대로 될 리가 없지...

막히는 부분 있으면 턀갤에 댓글 남겨줘

여기까지 성공한 사람이 있으면 다음은 로그를 여러 개 집어넣거나 로그에 이미지나 음악을 집어넣거나 해보자

`orpg\src\app\shared\models\campaigns.model.ts` 를 열어서 대충 어떻게 돌아가는지 보고 만지작거려도 됨
