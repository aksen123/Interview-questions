# 리액트 메모리 누수!

React에서 메모리 누수는 주로 컴포넌트가 언마운트된 후에도 이벤트 리스너나 타이머 등이 정리되지 않아서 발생한다. 이를 방지하기 위해서는 useEffect 훅의 클린업 함수, 비동기 작업의 취소, Ref의 적절한 관리 등이 중요한데,
이러한 메모리 관리 작업을 통해 애플리케이션의 성능을 최적화할 수 있다.

<br />
<br />

## 1. 비동기 작업 취소
- 컴포넌트가 언마운트될 때 비동기 작업을 취소하면 메모리 누수를 방지할 수 있다.

```jsx
import React, { useEffect, useState } from 'react';

const MyComponent = () => {
  const [data, setData] = useState(null);

  useEffect(() => {
    let isMounted = true; // 컴포넌트가 마운트되어 있는지 확인

    const fetchData = async () => {
      const response = await fetch('https://api.example.com/data');
      const result = await response.json();
      if (isMounted) {
        setData(result);
      }
    };

    fetchData();

    return () => {
      isMounted = false; // 컴포넌트 언마운트 시 true를 false로 설정
    };
  }, []); // 빈 배열은 컴포넌트가 마운트될 때만 실행됨

  return <div>{data ? JSON.stringify(data) : 'Loading...'}</div>;
};

```

<br />
<br />


## 2. 타이머 해제
- 타이머를 설정 후, 컴포넌트가 언마운트 될 때 타이머를 해제 해줘야 누수를 방지할 수 있다.

```jsx
import React, { useEffect } from 'react';

const MyComponent = () => {
  useEffect(() => {
    const timer = setInterval(() => {
      console.log('Timer running');
    }, 1000);

    return () => clearInterval(timer); // 컴포넌트 언마운트 시 타이머 해제
  }, []); // 빈 배열은 컴포넌트가 마운트될 때만 실행됨

  return <div>Check the console for timer logs.</div>;
};

```

<br />
<br />

## 3. 이벤트 리스너 해제
- 이벤트 리스너 추가후, 컴포넌트가 언마운트 될때 이벤트를 제거 해줘야 한다.

```jsx
import React, { useEffect } from 'react';

const MyComponent = () => {
  useEffect(() => {
    const handleResize = () => {
      console.log('Window resized');
    };
    window.addEventListener('resize', handleResize);

    return () => window.removeEventListener('resize', handleResize); // 컴포넌트 언마운트 시 이벤트 리스너 제거
  }, []); // 빈 배열은 컴포넌트가 마운트될 때만 실행됨

  return <div>Resize the window!</div>;
};

```
