# Js 데이터

## 문자 (string)

### **.indexOf()**

---

- 문장내에서 해당하는 문자가 위치하는 처음 인덱스 값을 반환
- `Hi my name is minuk → “name”.indexOf()` 하면 6을 반환
- 만약 일치하는 값이 없으면 -1 반환

[String.prototype.indexOf() - JavaScript | MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/indexOf)

### **.length**

---

- 문자열의 길이

### **.slice(a,b) (a,b는 숫자)**

---

- a부터 b직전까지 잘라내서 보여주기

### **.replace(’a’, ‘b’) (a,b는 문자)**

---

- a 문자를 b 문자로 바꿔서 보여줌

### .match(정규식)

---

- 정규 표현식을 넣어서 사용 (괄호안 내용은 바뀔 수 있다)
- 문자열이 정규식과 일치하면, 일치하는 전체 문자열을 첫 번째 요소로 포함하는 `[Array](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array)`
를 반환한 다음 괄호 안에 캡처된 결과가 나온다.
- 따라서 첫번째 요소를 가져와야 함으로 [0]을 뒤에 붙인다.
- 정규식에 옵션 넣어주기
    - g: 대소문자 구분
    - gi : 대소문자 구분 X

### .trim()

---

- 특정한 문자 데이터의 앞뒤의 공백 문자열을 제거

## 숫자

### .toFixed(n)

---

- 소숫점 몇번째 자리까지 유지할건지 (버림)
- 문자 데이터로 반환!!!

### parseInt(문자)

---

- 문자를 정수로

### parseFloat(문자)

---

- 문자를 실수로

## 수학 Math함수

[Math - JavaScript | MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math)

### Math.abs(숫자)

---

- 절댓값

### Math.min(숫자, 숫자)

---

- 인수 중 작은 값

### Math.max(숫자, 숫자)

---

- 인수 중 큰 값

### Math.ceil(숫자)

---

- 올림

### Math.floor(숫자)

---

- 내림

### Math.round(숫자)

---

- 반올림

### Math.random()

---

- 랜덤 숫자
- 0-1 사이의 랜덤 소수

## 배열

### .length

---

- 배열의 길이
- 0은 배열안에 아무것도 없다

### .concat([배열])

---

- 두개의 배열을 합쳐서 반환
- 원본 데이터는 수정 안됨.

### .forEach((item, index, array)⇒{ 내용 })

---

- 어레이 하나하나 탐색해서 순차적으로 함수 내용 적용
- array는 원본 어레이 반환하는값 잘 필요 없음.

### .map((item, index)⇒{return 내용})

---

- 함수 내용을 적용시켜서 새로운 배열을 반환한다.

### .filter((item, index)⇒{return 내용})

---

- 함수 내용에 해당하는 어레이 요소들만 반환하여 새로운 배열 만듬

### .find((item, index)⇒{return 내용})

---

- 함수 내용에 맞는 요소 첫번째 값을 반환한다.

### .findIndex((item, index)⇒{return 내용})

---

- 함수 내용에 맞는 첫 요소의 인덱스 번호를 반환한다.

### .includes(내용)

---

- 함수 내용에 맞는 값이 리스트에 있는지 TRUE FALSE

### .push(내용)

---

- 내용에 해당하는 값을 리스트의 맨 뒤에 추가
- 원본 데이터 수정

### .unshift(내용)

---

- 내용에 해당하는 값을 리스트의 맨 앞에 추가
- 원본 데이터 수정

### .reverse()

---

- 리스트의 순서를 뒤집음
- 원본 데이터 수정

### .splice(인덱스 숫자, 갯수)

---

- 인데스 번호”부터” 갯수에 해당하는 아이템을 리스트에서 삭제

### .splice(인덱스 숫자, 0, 추가할 값)

---

- 인덱스 번호에 특정 값을 추가한다.

### .splice(인덱스 숫자, 숫자, 추가할 값)

---

- 인덱스 번호의 숫자를 지우고 해당 위치에 특정 값을 추가한다.

## 객체

### Object.assign(객체1, 객체2)

---

- `const 변수 = Object.assign(객체, 객체)`
- 객체 두개를 합친다.
- 겹치는 변수가 있으면 뒤의 객체가 덮음
- 객체 데이터를 새롭게 복사한다.

### Object.keys(객체)

---

- `const 변수 = Object.keys(객체)`
- 객체의 속성의 이름 (속성값 아님)을 추출해서 배열로 만듬

### 객체[속성] = 속성값

---

객체에서 인덱싱 하는 방법

## 구조 분해 할당

```jsx
const user = {
	name: "minuk",
	age: 85,
	email: "damin2003@yonsei.ac.kr"
}
const {name, age, email} = user
//name이라는 변수에 name 값이, age라는 변수에 age 값이...

const {name, age, email, address="Korea"} = user
//없는 값을 추가 할당 할 수도 있음

const {name, age = 15, email} = user
//하지만 있는 값은 할당해도 무시

const {name:minuk, age, email} = user
//name 값을 가져오지만 변수명은 수정
```

```jsx
const fruits = ['Apple', 'Banana', 'Cherry']
//*객체 데이터는 특정 속성이 있지만 배열은 순서대로!! 분해 할당
const [,b] = fruits
//일부분만 가져올 수도 있음 쉼표 주의!
```

## 전개 연산자

```jsx
const fruits = ['Apple', 'Banana', 'Cherry']
console.log(...fruits)
//console.log('Apple', 'Banana', 'Cherry')와 같음
```

## 불변성

- 원시 데이터: String, Number, Boolean, undefined, null
- 참조형 데이터: Objext, Array, Function

---

- 원시 데이터에서 똑같은 값이 할당된다면 추가되는 것이 아닌 이미 있는 메모리 영역에서 가져온다.

---

- 하지만 참초형 데이터는 불변성이 없다. (같은 값을 지정하더라도 다른 메모리 주소에 할당)
- 객체의 값을 수정하면 새로운 메모리 영역에 할당하는 것이 아닌 원래 있던 메모리 주소에 값을 수정한다.

## 얕은 복사와 깊은 복사

### 얕은 복사

---

- `const copyUser = Object.assign({}, user)`
- `const copyUser = {…user}`

→ 얕은 복사 같은 경우 값이 바뀌지 않는다면 속성값은 같은 메모리를 바라보고 있다.

### 깊은 복사

---

- lodash의 `_.cloneDeep(참조형 데이터)` 와 같은 방식을 활용

→ 깊은 복사는 모든 값이 다른 메모리를 바라보고 있다.