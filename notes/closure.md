# 클로저(Closure)

함수와 그 함수가 선언된 렉시컬 환경(lexical environment)의 조합이다. 자신이 `선언된 당시의 환경`을 기억 하고(외부 스코프의 변수들을 "기억"), 외부 함수의 실행이 끝난 후에도 이 변수들에 접근할 수 있게 해준다.

<br />
<br />

## 클로저 장점
- [상태 유지](#카운터-예시): 클로저는 함수가 호출된 이후에도 외부 함수의 변수 상태를 유지할 수 있다. 이를 통해 함수 호출 사이에 상태를 유지하고, 이를 기반으로 동작을 수행할 수 있다.
- [데이터 은닉](#데이터-은닉): 클로저를 사용해 함수 외부에서 직접 접근할 수 없는 변수를 만들 수 있다. 이를 통해 데이터 은닉을 구현하고, 변수의 값을 외부에서 변경할 수 없도록 보호할 수 있다.
- [전역 변수의 사용 억제/ 모튤 패턴](#모듈 패턴): 클로저는 모듈 패턴을 구현하는 데 유용하다. 모듈 패턴은 관련 기능들을 그룹화하여 코드의 구조를 개선할 수 있다.
- 
<br />
<br />

## 클로저의 구성
- 외부 함수: 내부 함수가 선언된 함수
- 내부 함수: 외부 함수 내에서 선언되고 반환되는 함수.

<br />
<br />

## 클로저 예시

<br />

### 기본 예시

```js
function 외부함수() {
  let 외부함수변수 = '가나다라마바사';

  function 내부함수() {  // <<<< 얘가 클로저!!!
    console.log(외부함수변수);
  }

  return 내부함수;
}

const closureFunction = 외부함수();
closureFunction(); // 가나다라마바사

```
위 예시에서 `내부함수`는 `외부함수`에 접근할 수 있다. `외부함수`가 실행되고 나면 `내부함수`는 외부변수인 `외부함수변수`를 기억하는 클로저가 됨

<br />
### 카운터 예시 

```js
function createCounter() {
  let count = 0;

  return function() {
    count += 1;
    return count;
  };
}

const counter = createCounter();
console.log(counter()); // 1
console.log(counter()); // 2
console.log(counter()); // 3
```
이 예제에서 `createCounter` 함수는 `count` 변수를 가지고 있으며, 내부 함수는 `count`를 증가시키고 반환한다. 내부 함수는 `count` 변수에 대한 클로저를 형성하여, `createCounter` 함수가 종료된 후에도 `count`에 접근하고 수정할 수 있다.

<br />

### 데이터 은닉

```js
function createSecretHolder(secret) {
  let mySecret = secret;

  return {
    getSecret: function() {
      return mySecret;
    },
    setSecret: function(newSecret) {
      mySecret = newSecret;
    }
  };
}

const secretHolder = createSecretHolder('비밀!!!');
console.log(secretHolder.getSecret()); // 비밀!!!
secretHolder.setSecret('비밀~');
console.log(secretHolder.getSecret()); // 비밀~
```

이 예제에서는 `mySecret` 변수가 클로저를 통해 은닉된다. 외부에서는 `getSecret`과 `setSecret` 메서드를 통해서만 `mySecret`에 접근할 수 있다.

<br />

### 모듈 패턴

```js
const counterModule = (function() {
  let count = 0; // 비공개 변수

  return {
    increment: function() {
      count++;
      return count;
    },
    decrement: function() {
      count--;
      return count;
    },
    getCount: function() {
      return count;
    }
  };
})();

console.log(counterModule.increment()); // 1
console.log(counterModule.getCount());  // 1
console.log(counterModule.decrement()); // 0
```


<br />

## 🙋‍♂️ 추가 / 용어

<br />

### ✔️ 렉시컬 스코프 

- 렉시컬 스코프는 함수를 어디서 호출하는지가 아니라 어디에 `선언하였는지에 따라 결정` 되며, 다른 말로는 정적 스코프 라고 부르기도 한다.
```js
let x = 10;

function 함수1(){
let x = 100;
함수2();
}

function 함수2(){
console.log(x)
}

함수1() // 10
함수2() // 10
```
`함수1`안에서 호출된 `함수2`는 `지역변수 x(100)`가 아닌 `전역 변수인 x(10)`를 호출 하게 되는데 그이유는 `함수2`가 전역에 선언 되었기 떄문에 `전역 변수 x(10)`를 참조 하는것!



