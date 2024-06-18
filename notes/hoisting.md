# 호이스팅(hoisting) 이란?
호이스팅(hosting)은 자바스크립트의 특성 중 하나로, 변수 선언과 함수 선언이 해당 범위의 최상단으로 끌어올려지는 것처럼 동작하는것을 말한다. 

<br />
<br />

## 변수 호이스팅 

### var
`var` 키워드로 선언된 변수는 호이스팅이 되는데, 변수가 선언된 위치와 상관없이 그 변수가 범위의 최상단으로 끌어올려진 것처럼 동작한다. 그러나 변수의 초기와는 호이스팅되지 않고, 변수가 실제 선언된 위치에서 이루어 진다.


```js
console.log(x); // undefined
var x = 5;
console.log(x); // 5
```

위 예제에서 x 변수는 console.log(x); 문이 실행될 때 아직 초기화되지 않았지만, 자바스크립트는 변수가 선언되었다는 사실을 알고 있기 때문에 undefined 값을 반환한다. 내부적으로 자바스크립트는 다음과 같이 처리함

```js
var x; // 변수 선언 (변수가 메모리에 할당되는 시점)
console.log(x); // undefined
x = 5; // 변수 초기화 (변수에 초기값이 할당 되는 시점)
console.log(x); // 5
```

### let, const
`let`과 `const` 키워드로 선언된 변수도 호이스팅되지만, `var`와는 달리 초기화 되기 전까지 해당 변수를 접근할 수 없으며, 이를 "일시적 사각지대(TDZ, Temporal Dead Zone)"라고 한다. 
**TDZ는 변수 선언 시점부터 초기화 시점까지의 구간을 의미 함!**

```js
console.log(a); // ReferenceError: Cannot access 'a' before initialization
let a = 10;
console.log(a); // 10

console.log(b); // ReferenceError: Cannot access 'b' before initialization
const b = 20;
console.log(b); // 20
```


<br />

## 함수 호이스팅

함수 선언은 변수 선언과는 달리 함수 정의 자체도 호이스팅이 된다. 따라서 함수 선언문은 코드 내 어느 위치에서든 호출될 수있다.

```js
console.log(add(2, 3)); // 5

function add(a, b) {
    return a + b;
}
```
위 예제에서 `add` 함수는 호출하고 나서 선언되었지만, 함수 선언이 호이스팅되기 때문에 정상적으로 동작한다.


### 함수 선언문, 함수 표현식

- 함수 선언문 : 선언과 동시에 초기화가 이루어지며, 호이스팅 된다. 코드 내 어느 위치에서든 호출 가능 ( 위 예제 코드 )
  

- 함수 표현식(변수에 할당된 함수) : 변수에 할당되는 시점에서 정의되며, 호이스팅 되지 않는다. 따라서 함수 표현식을 사용한 함수는 변수에 할당 되기전에는 호출할 수 없다.
```js
console.log(multiply(2, 3)); // TypeError: multiply is not a function

var multiply = function(a, b) {
    return a * b;
};

console.log(multiply(2, 3)); // 6
```
`multiply`함수는 변수에 함슈 표현식이 할당되기 전에 호출되었기 때문에 에러가 발생하는것. 이는 변수 `multiply`가 호이스팅 되어 undefined로 초기화 되었기 때문이다. 


<br />
<br />


## 📒 요약 
1. var : 변수 선언이 호이스팅 되지만, 초기화는 호이스팅 되지 않는다.
2. let, const : 변수 선언이 호이스팅 되지만, 초기화 전까지는 접근할 수 없다.
3. 함수 선언문 : 함수 선언 전체가 호이스팅되어 어느 위치에서든 호출이 가능하다.
4. 함수 표현식 : 변수에 할당되는 시점에 정이되며, 호이스팅 되지 않는다.

<br />
<br />

## 🙋‍♂️ 추가 / 용어

### ✔️ TDZ
-  변수의 선언 단계와 초기화 단계 사이의 사각지대이다. 이 영역에 있는 변수에 접근하면 `ReferenceError`가 발생한다.
- `var`는 변수의 선언과 초기화 단계가 동시에 실행되어 `TDZ`가 존재하지 않기 때문에 호이스팅이 일어나는 것!
- 반대로 `let`과 `const`는 선언단계와 초기화 단계가 따로 분리되어 실행 되기때문에 초기화 전에 호출하면 `ReferenceError`가 발생 한다!

```js
console.log(a); // ReferenceError: Cannot access 'a' before initialization
let a = 10;

console.log(b); // ReferenceError: Cannot access 'b' before initialization
const b = 20;
```

#### 1. 스코프 단계 설정
자바스크립트 엔진이 스코프를 설정하고 변수를 처리한다. `let`,`const`로 선언된 변수는 TDZ에 들어감
- `let a`는 TDZ에 들어감
- `const b`는 TDZ에 들어감
#### 2. 코드 실행 단계
코드가 순차적으로 실행 됨.
- `console.log(a)`를 실행하고 `a`는 아직 `TDZ`에 있기 때문에 `ReferenceError: Cannot access 'a' before initialization`가 발생
- `let a = 10`을 실행해 `a`를 `TDZ`에서 벗어나게하고 `a`에 10을 할당.
- `console.log(b)`를 실행하고 `b`는 아직 `TDZ`에 있기 때문에 `ReferenceError: Cannot access 'a' before initialization`가 발생
- `const b= 20`을 실행해 `b`를 `TDZ`에서 벗어나게하고 `a`에 10을 할당.




### ✔️ var와 let, const의 차이

| 특징 | `var` | `let` | `const` | 
| --- | --- | --- | --- | 
| **스코프** | 함수 스코프 | 블록 스코프 | 블록 스코프 |
| **호이스팅** | 선언 단계가 호이스팅됨 | 선언 단계가 호이스팅되며 TDZ 존재 | 선언 단계가 호이스팅되며 TDZ 존재 |
| **초기화 이전 접근** | `undefined` 반환 | `ReferenceError` 발생 | `ReferenceError` 발생 |
| **중복 선언** | 가능 | 불가능 | 불가능 | | **재할당** | 가능 | 가능 | 불가능 |



