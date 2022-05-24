# JS 에센셜

# NPM


- `npm init -y` 프로젝트 시작하기

- `npm install xxx -D`
    - 개발용 의존성 패키지 설치
    - 개발할때만 사용하고, 웹에서 동작할 때는 필요 없음
- `npm install xxx`
    - 웹에서도 동작

- parcel
    - package.json의 script에 `“dev”: “parcel index.html”` 적기
        - `npm run dev` 하면 홈페이지 run
    - package.json의 script에`“build” : “parcel build index.html”`
        - 난독화 시켜서 불필요한 공간을 줄여서 개발자만 볼 수 있도록 용량 최적화.
    
- Lodash
    - `import _ from ‘lodash’`
    - _.throttle() 처럼 lodash 메소드 호출 가능
    
- .gitignore
    - .cache
    - dist
    
    → 이런식으로 파일명 넣어서 깃헙에 버전 관리 무시 가능
    

# JS


## Type 확인하기

- `console.log(typeof 123)`

```jsx
function getType(data){
	return Object.prototype.toString.call(data).slice(8, -1)
}
```

## 연산자

- 산술 연산자
    - 1 + 2 더하기
    - 1 - 2 빼기
    - 1 * 2 곱하기
    - 1 / 2 나누기
    - 1 % 2 나머지

- 할당 연산자
    - =
    - a += 1
    - a -= 1
    - a *= 1 등등

- 비교 연산자
    - === :  일치 연산자
    - !== : 불일치
    - <, >
    - >=, <=

- 논리 연산자
    - && : AND (하나라도 false면 false)
    - || : OR (하나라도 true면 true)
    - ! : NOT (특정 값의 반대)

- 삼항 연산자
    
    ```jsx
    const a = 1<2
    
    if (a) {
    	console.log("참")
    } else {
    	console.log("거짓")
    }
    
    //삼항연산자
    console.log(a? "참":"거짓")
    ```
    

## 조건문

- if / else

```jsx
if (a === 0) {
    console.log('a is 0')
} else if (a === 2) {
    console.log('a is 2')
} else {
    console.log('rest...')
}
```

- switch

```jsx
switch (a) {
    case 0:
        console.log('a is 0')
        break //break 사용해줘야함
    case 2:
        console.log('a is 2')
        break //break 사용해줘야함
    default:
        console.log('rest...')
        //break 안써도 됨
}
```

## 반복문

- for

```jsx
for (let i=0; i<3; i+=1){
    console.log(i)   
}

//예시
const ulEl = document.querySelector('ul')

for (let i=0; i<3; i+=1){
    const li = document.createElement('li') //메모리상의 li에 li 태그 할당
    li.textContent = `list-${i + 1}`// li에 텍스트 콘텐츠 삽입
    ulEl.appendChild(li) //ul의 자식으로 html에 삽입
}
```

## 변수 유효범위

- const, let 같은 경우는 동작할 수 있는 유효 범위가 있지만, var는 애매함 쓰지마 걍
- const, let → 블록 레벨의 유효범위
- var → 함수 범위의 유효 범위

## 형 변환

- == : 동등 연산자
    - 형변환으로 인해서 문자와 숫자도 비슷한 값이면 같다고 말한다.

- if(”false”)로 해도 동작할까?
    - 아니다 string 변수이기 때문에 true!
    - Truthy
        - trun, {}, [], 1, 2, “false”, …
    - Falsy
        - false, “”, null, undefined, 0, -0, NaN(not a number, 1+undefined와 같은 경우)
    

## 함수

### 기본

---

- 함수에 넣는 수
    - 인수
- 함수에 들어가는 변수
    - 매개 변수
- return 되면 함수는 종료됨

- `arguments`
    - 매개 변수가 선언 안되어도 argument를 함수 안에 넣으면 사용 가능
    - 하지만 일일이 다 매개변수 입력해주는 방법이 더 나음
        

### 화살표 함수

---

- function(){ → () ⇒ {
- 축약형도 가능

```jsx
const doubleArrow = (x) => {
    return x * 2
}

//축약형
const doubleArrow = x => x * 2 
//매개 변수 한개 일때 괄호 없애도 됨, return 한줄이면 중괄호와 return도 생략

const doubleArrow = x => ({
    name: 'Heropy'
})

//객체 데이터는 {} 때문에 축약하기 위해서는 () 사용
```

### 즉시 실행 함수

---

```jsx
const a = 7
function double() {
    console.log(a*2)
}
double(); //즉시 실행 함수는 괄호로 시작하기 때문에 꼭 ; 추가

(function(){
    console.log(a*2)
})() //즉시 실행 함수 (x)()

(function(){
    console.log(a*2)
}()) //즉시 실행 함수 (x())
```

### 호이스팅

---

```jsx
double()

function double(){
	console.log("Hi")
}

//함수 선언부가 유효범위 최상단으로 끌어올려지는 현상 const로 선언된거 말고 일단 호출함수.
```

### 타이머 함수

---

```jsx
setTimeOut(함수, 시간) //일정시간 후 함수 실행
setInterval(함수, 시간) //시간 간격마다 함수 실행
clearTimeout(함수) //설정된 Timeout 함수를 종료
clearInterval(함수) //설정된 Interval 함수를 종료
```

### 콜백

---

- 함수의 인수로 사용되는 함수

```jsx
function timeout(callback) {
    setTimeout(() => {
        console.log("hi")
        callback() //특정한 실행하는 위치를 보장하기 위해서도 사용
    }, 3000)
}

timeout(() => { //콜백 함수
    console.log('done')
})
```

## 클래스

### 생성자 함수

---

```jsx
const heropy = {
    firstName: "Heropy", //property
    lastName: "Park",
    getFullName: function () {
        //method
        return `${this.firstName} ${this.lastName}`; //heropy.firstName 이라고 해도됨.
    },
};

const minuk = {
    firstName: "Minuk", //property
    lastName: "Hwang",
    getFullName: function () {
        //method
        return `${this.firstName} ${this.lastName}`;
    },
};

const Seunghee = {
    firstName: "Seunghee", //property
    lastName: "Lee",
    getFullName: function () {
        //method
        return `${this.firstName} ${this.lastName}`;
    },
};
```

→ 이렇게 반복되는 객체를 정리 안될까?

```jsx
function user(first, last){
    this.firstName = first
    this.lastName = last
    this.getFullName = function () {
        return `${this.firstName} ${this.lastName}`;
    }
}

const heropy/*인스턴스*/ = new user('Heropy', 'Park') //생성자 함수 객체 데이터 생성
const heropy = new user('Heropy', 'Park') 
const minuk = new user('Minuk', 'Hwang') 
const seunghee = new user('Seunghee', 'Lee')

//const heropy = {} //리터럴 방식 특별한 방식 거치지 않고 바로 객체 생성
```

→ 일단 이렇게 복잡하게도 구현 가능

```jsx
function User(first, last){ //생성자 함수는 앞에 대문자로 표시, 구분을 위해서
    this.firstName = first
    this.lastName = last
}

user.prototype.getFullName = function() {
    return `${this.firstName} ${this.lastName}`; 
//이렇게 밖에다가 생성하면 겹치는 메모리를 줄일 수 있다. 
//한개 밖에 생성된거에 다들 참조하기 때문에
}

const heropy = new User('Heropy', 'Park') 
const minuk = new User('Minuk', 'Hwang') 
const seunghee = new User('Seunghee', 'Lee')

console.log(heropy.getFullName())
```

### this

---

```jsx
// 일반 함수는 호출 위치에서 따라 this 정의
// 화살표 함수는 자신이 선언된 함수 범위에서 this 정의

const heropy = {
    name: 'Heropy',
    normal: function () {
        console.log(this.name)
    },
    arrow: () => {
        console.log(this.name)
    }
}
heropy.normal() //'Heropy'
heropy.arrow() //undefined

const amy = {
    name: 'Amy',
    normal: heropy.normal, //그냥 객체안의 함수 내용 가져오기
    arrow: heropy.arrow,
}

amy.normal() //Amy
amy.arrow() //undefined
```

```jsx
const timer = {
    name: 'Heropy',
    timeOut: function () {
        setTimeout(()=>{ 
//화살표 함수는 자신이 선언된 위치가 timeOut 함수 위치기 때문에 그 범위 안에 name 존재
            console.log(this.name)
        }, 2000)
    }
}

timer.timeOut()
```

### ES6 Classes

---

- 함수 축약법

```jsx
const heropy = {
    name: 'Heropy',
    normal() { //이렇게 바로 줄일 수 있음 normal: function(){
        console.log(this.name)
    },
    arrow: () => {
        console.log(this.name)
    }
}
heropy.normal() 
heropy.arrow() 
```

- class 표기법!!!

```jsx
// function User(first, last){
//     this.firstName = first
//     this.lastName = last
// }

// user.prototype.getFullName = function() {
//     return `${this.firstName} ${this.lastName}`;
// }

class User {
    constructor(first, last) {
        //내부함수 constructor: function() 생략법
        this.firstName = first;
        this.lastName = last;
    }
    getFullName(){
        return `${this.firstName} ${this.lastName}`;
    }
}

const heropy = new User("Heropy", "Park");
const minuk = new User("Minuk", "Hwang");
const seunghee = new User("Seunghee", "Lee");

console.log(heropy.getFullName());
```

### 상속(확장)

---

```jsx
class Vehicle{
    constructor(name, wheel){
        this.name = name
        this.wheel = wheel
    }
}

class Car extends Vehicle{
    constructor(name, wheel, license){
        super(name,wheel) 
// super() 부모의 constructor()을 참조한다. 그냥 부모의 constructor() 대신 쓴다고 봐
// super.하면 부모 클래스의 속성값에 접근
        this.license = license
    }
}

const car = new Car('차', 4, true)
console.log(car)
```
