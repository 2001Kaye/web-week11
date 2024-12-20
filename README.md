# 목차

- [목차](#목차)
  - [11주차](#11주차)
    - [Node.js](#nodejs)
    - [React Song List](#react-song-list)
  - [12주차](#12주차)
    - [React Counter](#react-counter)
    - [React Song List 수정](#react-song-list-수정)

## 11주차

### Node.js

- [수업 자료](https://nano5.notion.site/Node-js-135daf211d4280d09c76c3439719794d)

`console.log("안녕")`

- 세미콜론 안 써도 됨
- terminal의 cmd 에서 node 파일명(또는 .js) 입력 하면 실행됨
- 서버 실행도 가능 -> 서버 중지 ctrl + c
  - http 모듈을 들고 와서 .createServer로 서버를 생성 후 반환된 서버에 .listen으로 서버를 실행함
  - createServer에서 request와 response를 파라미터로 받아서 response에 .wirteHead, .end를 입력해줌
  - wirteHead(status code, headers): 헤더 넘기기
  - end(body): 데이터 넘기기
    - JSON.stringify(data): javascript data값(object = 객체)을 JSON(JavaScript Object Notation) string으로 바꿔줌
  - server.listen(port, listeningListener): 비동기 실행이고 연결을 위해 서버 listening 이벤트를 발생하게 되고 후행 파라미터 콜백 함수가 listening 이벤트를 위해 리스너로 추가됨

### React Song List

- [수업 자료](https://nano5.notion.site/React-Song-List-135daf211d4280b0aa1cfb389f522110)

- component 사용
- 명령어
  - npx create-react-app 폴더명: 생성
  - npm start: 실행
  - powershell에서 오류 해결하는 법
    - 관리자 권한으로 실행
    - `executionpolicy`
    - `set-executionpolicy remotesigned`
- `index.html`

  - `html:5`: 이걸로 쉽게 만들 수 있음
  - `<div id=root />`: 여기가 index.js 에서 가져오는 지점

- 12주차 수업
  - Component
    - Header 함수(element 반환) 작성 -> `<Header/>` 컴포넌트로 사용 가능
  - CSS
    - className에 클래스명 넣기

## 12주차

### React Counter

- [수업 자료](https://nano5.notion.site/React-Counter-135daf211d42806e91cfcedceddf2066)

[목표]

- Counter 구현
- State로 상태 관리
- 비동기 처리(state)

1. Counter 구현

   - Stackblitz 사용 -> tsx 사용
   - <></>: wrap 역할 가상 element (div 사용 가능)
   - 하나의 element만을 return 해야 함
   - 자바스크립트의 지역변수로 값을 카운트 했지만 화면에는 변하지 않는 문제 발생 => 상태 관리가 필요하다.

2. State로 상태 관리

   - React 라이브러리에서 useState 임포트
   - `const [state, setState] = useState();`
   - 초깃값을 uesState 부를 때 넣어 줄 수 있음 ex) useState(0)
   - 상태 변경: setState(cnt + 1); // setState를 여러개 호출하면 이전 값이 업데이트 안되는 문제 발생

3. 비동기 처리

   - 상태 변경 시 비동기 방식으로 작동하기 때문에 최신값을 보장할 수 없음
     - 비동기: 순서대로 하는 게 아니고 이거 해~ ㅇㅋ 다음 줄 하고 있어 나중에 값 줄게
   - 상태 업데이트가 즉시 처리 되는 것이 아닌 배치로 묶어서 나중에 처리하기 때문에 이전 값을 즉시 업데이트 해주려면 함수형으로 넘겨줘야 한다.
   - 함수로 넘겨서 상태의 최신값을 사용하도록 하자. -> cnt + 1를 변경해야 함
     - (prev) => prev + 1;

4. 그 외
   - 파일 다운로드 후 -> npm install -> npm run dev
   - 또는 npm install && npm run dev

### React Song List 수정

[목표]

- 업데이트를 해봅시다.

1. 지난 시간에 복붙한 Container 함수를 props를 이용해서 중복을 제거한다.
   - properties 전달
   - JSX에서 JavaScript를 사용하려면 중괄호 사용
   - Template Literal 사용
     - {\` \`}: Back tick 사용 -> Tilde(물결표) 있는 곳
     - 변수는 ${}로 사용
2. Lambda Expression 사용
   - `function App() {}` -> `const App = () => {}`
   - 화살표 함수 사용
   - 인자 하나이면 화살표 함수에서 괄호 생략 가능
3. github.dev
   - `github.com/[아이디]/[repository이름]`
   - .com -> .dev
   - 웹 브라우저 주소창
4. Container Component 파일을 분리
   - 컴포넌트 불러오기 `import Container from "./Container";`
5. Song array 사용
   - props로 넘겨주는 편이 resuability측면에서 바람직하다(title)
   - 호이스팅: 끌어 올리는 것
   - map() 함수 안에 lambda expression 사용할 때 중괄호, 괄호를 유의하자
     - 중괄호: return 필수
     - 괄호: 바로 return
   - warning: Each child in a list should have a unique "key" prop.
     - key property 추가가 필요함. React DOM이 변경된 부분만 렌더링할 때 구분하기 위해 필요하기 때문임. 구분하지 않으면 전부 다 다 렌더링하기 때문에 성능면에서 좋지 않음
     - 그러나 props.key로 읽을 수 없음
   - &&: AND 기호 하나라도 0이면 그냥 0임을 이용해 하나가 참이면 뒤를 무조건 검사하려고 하는 속성으로 컴포넌트 출력 가능
6. 선호도 출력
   - 아이콘 설치시 npm install 대신 npm i로 써도 됨
   - spread 연산자 사용 권장
     - Array(숫자) : 배열에 아무것도 없어서 map 사용 불가
     - [...Array(숫자)]: undefined 값으로 채워줌
     - .map((\_, idx) => {}): idx로 사용해줌 된다!
