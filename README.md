# CSS
* html(구조), css(디자인), js(동적)
* html 작성 : `<body><tag 속성="값" 속성="값"></body>`
* css 작성 : `<head><style>tag {디자인속성:값; 속성:값;}</style></head>`
## CSS 선택자
* 태그 선택자 : `태그 {속성:값;}`
* 아이디 선택자 : `#아이디명 {속성:값;}`
* 클래스 선택자 : `.클래스명 {속성:값;}`
* 부모-자식 선택자 : `부모 > 자식 {속성:값;}`
* 부모-자손 선택자 : `부모 자손 {속성:값;}`
* 형제 선택자 : `기준형제+선택형제 {속성:값;}`
* 다중 형제 선택자 : `기준형제~선택형제들 {속성:값;}`
* 모든 선택자 : `* {속성:값;}`
* 수열(nth) 선택자
    * 형제가 2개 이상일 때 원하는 형제를 선택하는 선택자
    * `형제선택자:nth-child(n)` : n번째 형제
    * `형제선택자:nth-child(odd)` : 홀수
    * `형제선택자:nth-child(even)` : 짝수
## CSS 선택자 우선순위
* `<style>` > `#` > `.` > `tag`
1. `<tag style="">` 우선순위 높음
2. `#id {}`
3. `.class {}`
4. `tag {}` 우선순위 낮음
## CSS 본인 적용과 상속 적용 차이
* 자식이 2개 이상일 때 부모에 속성을 적용하는 것으로 자식에게 공통 값을 적용할 수 있다.
    * `ul-li*5` 관계 시 `ul {color:red}` 부모 ul의 color를 li 자식에게 상속시킨다.
    * 꾸미려는 css 속성이 글자에 관련된 속성(글꼴, 글자크기, 글자색상 등) 본인에게 직접 적용하는 것을 권장함.(우선순위가 꼬여서)
## 글꼴 사용 시 주의사항
* 모든 컴퓨터 기본글꼴(고딕, 궁서, 바탕 등)이 아니라면 반드시 웹글꼴을 사용하여 웹접근성을 높여줘야함.
* 웹글꼴 연결 순서는 작성한 CSS보다 반드시 위에 작성하기!
* 글꼴명이 한글이거나 공백이 포함된 경우 따옴표 붙여서 작성하기!
## 자주 사용하는 CSS 속성 모음
* `width:0px;` : 가로크기(vw, % 상대크기단위가능)
* `height:0px;` : 세로크기(vh, % 상대크기단위가능)
* `padding:0px;` : 안쪽여백(피그마 AutoLayout 패딩)
* `display:;` : 요소의 형태유형 변경속성
    * `block`, `inline`, `inline-block`
    * inline 변경가능요소 : h1, p, address 등 블록
        * `h1 {display:inline;}`
        * 내용만큼만 크기 인식
        * 옆으로 나열
    * block 변경가능요소 : a, span, em, del 등 인라인
        * `a {display:block;}`
        * 크기(w100%, h(Hug))와 여백값을 인식
        * 옆으로 정렬이 아닌 새로운 행으로 나열
    * inline-block 값은 모두 적용 가능
        * `h1 {display:inline-block;}`
        * `a {display:inline-block;}`
        * 크기와 여백값을 인식
        * 옆으로 나열(Hug), 넘치면 자동 줄바꿈됨.
* `margin` : 바깥쪽(형제 사이) 여백(피그마 기준 **간격**)
    * `margin:10px;` 모든 방향 10 통일
    * `margin:10px 20px;` 상하/좌우
    * `margin:10px 20px 30px;` 상/좌우/하
    * `margin:10px 20px 30px 40px;` 상/우/하/좌(시계방향)
    * **위 4개 속성 방향은 padding 동일**
    * `margin:0 auto;` : 레이아웃 가운데배치(너비가 화면보다 작아야함)
#  table HTML+CSS
* `table > tr > th or td`
* `table {width:300px}` 열이 3개일 경우 100씩 자동 분배
    * `th:nth-child(1) {width:50px;}`
    * 전체 너비 300 중 첫번째 열만 50을 가지고 나머지 값은 나머지 열들에게 자동 분배
    * (열 안 내용 크기에 따라 달라짐)
* `width, height, padding` 속성은 같은 수평/수직 방향에 해당하는 열에 함께 적용됨.
    * 위 특징 때문에 공통 여백 및 크기는 1행 라인에 작성
## 행 그룹 포함 table 작성 순서
* `table` -> `thead` -> `tr` -> `th`
* `table` -> `tbody` -> `tr` -> `th`
* `table` -> `tbody` -> `tr` -> `td`
* `table` -> `tfoot` -> `tr` -> `th`
* `table` -> `tfoot` -> `tr` -> `td`
## 수평/수직 열 합치기 
* 합치기 속성은 무조건 `th` 또는 `td` 태그에 입력가능!
* 수평 열 합치기
    * `<th colspan="합치는 열 개수">내용</th>`
    * 위 속성은 합치는 열 중 첫번째 시작태그에 작성하기
    * 그 외 나머지 칸은 지우거나 주석걸기
* 수직 열 합치기
    * `<td rowspan="합치는 열 개수">내용</td>`
## form 요소들의 동적인 편의 HTML + CSS
### input 입력요소
* `<input autofocus placeholder="">`
    * autofocus : 페이지 접속 시 바로 커서 위치 활성화
    * placeholder : 안내메세지 표시
        * `input::placeholder {}` 안내메세지 디자인
    * `input:focus {}` 입력칸 활성화 표시 디자인
### button
* `<button type="button" 이벤트="자바스크립트명령어작성">`
    * 버튼에 이벤트 작성 시 반드시 type은 button(범용기능)
    * `onclick=""` : 클릭 시 "명령어" 실행 이벤트
    * `window.location.href='실행주소'`
        * (위)`a href='실행주소'`와 동일한 js 명령어
    `button:hover {}` : 버튼에 마우스 올렸을 시 디자인 변경
# 웹글꼴 `<link>` , `@font-face`
##  `<link>` 사용법과 특징
* `head`태그 안 `reset.css` 연결보다 위에 작성
* `@font-face`에 비해 사용이 간편함.
* 작성한 html에서만 사용할 수 있다는 단점있음.
## `@font-face` 사용법과 특징
* `reset.css` 파일 내 가장 위쪽 라인에 작성
* `@font-face {`
    * `font-family:'사용할 글꼴 이름 임의작성';`
    * `src:url(글꼴주소);`
    * `font-weight:글꼴굵기(200~700 글꼴에 따라 다름);`
    * `font-style:기울기(nomal, italic 등);`
    * `font-display:swap;`
    `}`
* rest에 한번 연결해주면 모든 html에서 사용 가능
* `font-face {font-famliy:'사용할글꼴명'}` (예)컴퓨터 글꼴 설치
* `선택자 {font-famliy:'웹글꼴로 불러온 글꼴명'}` (예)포토샵 글꼴 사용
## CSS 레이아웃 정렬 속성
### dislpay
* `display:block` : 인라인을 수직으로 나열
* `display:inline-block` : 블록을 수평으로 나열
    * 기본 여백 3px발생 -> 해결법 `margin-right:-3px`
### margin
* `margin:상하여백 auto` : 크기가 설정된 블록 또는 인라인을 화면 가운데 배치
### float
* `float:left` : 형제 요소들을 왼쪽으로 순차정렬
* `float:rignt` : 형제 요소들을 오른쪽으로 정렬
    * 2개 이상 작성 시 역순으로 정렬됨.
* `float:none` : float 제거
* `clear:both` : 이전 형제에 작성된 float 정렬해제
### position
* `position:relative`
    * 태그의 기존 위치에서 상/하/좌/우로 약간의 이동이 필요할 때
    * 자식 또는 자손요소애 absolute가 있어서 부모 기준이 필요할 때
* `position:absolute`
    * 부모, 형제요소와 겹치는 디자인 특징이 필요할 때
    block요소에 absolute 설정시 inline-block처럼 너비를 내용만큼 인식함->너비 재입력
    * 부모 후보(dl, dt)들에게 추가 position 설정 안할 시 body 기준으로 움직임
    * `dl dt p {position:absolute;}`
* `a-index`
    * absolute로 인해 겹쳐진 형제 요소들 사이의 중첩순서가 필요할때
    * 0-999 작성가능 (단위 작성없이 숫자만 작성)
    * position 속성이 없으면 z-index 적용 불가
## 가상 CSS 선택자 ::after, ::before
* 시각적인 목적으로 디자인 배경, 선 등의 요소가 필요할 때 HTML태그 없이 CSS만으로 디자인을 만드는 선택자 
* `부모선택자::after {}` -> 부모의 마지막 자식에 디자인 생성
* `부모선택자::before {}` -> 부모의 첫번째 자식에 디자인 생성
### after, before 사용 시 필수속성
* `content:'';`-> 내용인식속성, 글자 필요한 디자인이 아닐 경우 '' 빈따옴표
* `display, background-color, width, height`
## 계산기 함수 `calc()`
* +,-,*,/,% 다양한 사칙연산 사용 가능
* 추가 괄호를 통한 복잡한 계산 가능
**연산자 앞뒤 여백 필수** `1+1(x)` `1 + 1(o)`
* `width, height, margin, padding` 등 숫자 입력 속성 활용가능
### calc 활용 예시
* `li {width:calc(100% / 4);}`
    4개의 li를 같은 크기로 나누기
* `li {width:calc((100% - 30px) / 4);}`
    4개의 li에 각 10px씩 사이여백을 주기 위해 전체 부모 100%너비 중 10*3 총 30px를 빼고 나머지 값을 4로 나누기
    `li {width:calc((100% - (10px * 30)) / 4);}`
* `a {display:block; height:calc(100% - 50px);}`
    * a의 크기를 인식하게 만들고 50px을 뺀 나머지 부모크기 주기