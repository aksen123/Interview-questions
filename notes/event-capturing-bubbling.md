# 이벤트 전파(캡쳐링, 버블링)란?

이벤트 전파 방향에 따라 캡쳐링, 버블링 이라 부름!

<br />
<br />

## 버블링(기본값) 
한 요소에 이벤트가 발생되면, 그 요소의 부모 요소의 이벤트도 같이 발생되는 이벤트 전파를 말한다. 이벤트가 제일 깊은 곳에 있는 요소에서 시작해 부모 요소를 거슬러 올라가며 발생하는 모양이 마치 물속 거품(bubble)과 닮았기 때문에 명명 지어졌다.

<br />
<br />

## 캡쳐링  
한 요소에 이벤트가 발생되면, 그 요소의 자손 요소의 이벤트도 같이 발생되는 이벤트 전파를 말한다. 한마디로 버블링 반대라고 볼 수 있다. 다만, 실무에서 자주 쓰이지는 않지만 가끔 유용한 경우가 있어 알아볼 필요가 있다.

<br />
<br />

### 캡쳐링을 적용 하려면 ?

```html
<form onclick="alert('form')">FORM
  <div onclick="alert('div')">DIV
    <p onclick="alert('p')">P</p>
  </div>
</form>
```

위 구조에서 p태그를 클릭하면 `alert`창이 p > div > from 순으로 뜨게 된다. ( 버블링이 기본이기 때문에 ) 여기서 캡쳐링을 적용하려면 `addEventListener()`함수의 세번째 매개변수로 `true`를 주면 캡쳐링을 줄 수 있디.
캡쳐링이 적용 된다면 form > div > p 순으로 `alert`창이 뜨게 됨
<br />

![image](https://github.com/user-attachments/assets/75d4e7ed-a77d-4b14-b9d5-6be87a57177b)
[이미지 출처- Inpa Dev 👨‍💻:티스토리](https://inpa.tistory.com/entry/JS-%F0%9F%93%9A-%EB%B2%84%EB%B8%94%EB%A7%81-%EC%BA%A1%EC%B3%90%EB%A7%81)

<br />
<br />

## 이벤트 전파를 막으려면 ?

- stopPropagation: 이벤트의 버블링과 캡처링을 모두 중지
  
    ```js
    element.addEventListener('click', function(event) {
    event.stopPropagation();
  });
  ```

- stopImmediatePropagation: 이벤트의 버블링과 캡처링을 모두 중지하고, 현재 이벤트에 대해 같은 요소에 등록된 다른 이벤트 리스너의 실행도 중지한다.
    ```js
    element.addEventListener('click', function(event) {
    event.stopImmediatePropagation();
      });
    ```

- preventDefault: 이벤트의 기본 동작(예: 링크 클릭 시 페이지 이동)을 중지한다.
    ```js
    element.addEventListener('click', function(event) {
    event.preventDefault();
    // 추가 코드
  });

    ```
  
