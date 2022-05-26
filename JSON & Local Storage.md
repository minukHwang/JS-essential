# JSON & Local Storage

## JSON

- JSON은 자바 스크립트의 데이터를 입력하는 객체 표기법
- JSON은 무조건 “”만 사용 가능
- JSON은 객체 속성 값에도 “”를 붙여줘야한다.
- string, number, boolean, null, object, array만 지정 가능
- 문자 데이터 입니다!!!
- `JSON.stringify(객체)` 만약 json으로 만들고 싶다면 스트링화 해야함
- `JSON.parse(객체)` 만약 스트링화된 부분을 분석해서 js에서 활용하고 싶다면 parse 사용

## Local Storage

### localStorage.setItem(’데이터이름’, JSON.stringify(객체))

---

- 로컬 저장소에 js 데이터 넣는 법
- 꼭 문자 데이터화 해서 넣어야한다.

### localStorage.getItem(’데이터이름’)

---

- 로컬 저장소에서 데이터 가져오는 법
- 데이터는 문자이기 때문에 `JSON.parse(객체)` 활용해서 변환 가능

### localStorage.removeItem(’데이터이름’)

---

- 로컬 저장소에서 데이터 지우는 법

[https://github.com/typicode/lowdb](https://github.com/typicode/lowdb)

→ lowdb 활용하면 (Lodash 사용) 로컬 데이터 활용이 좀 더 수월