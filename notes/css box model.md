# box model 이란 ?

CSS 박스 모델(Box Model)은 웹 페이지의 레이아웃을 정의하는 데 사용되는 기본적인 개념이다. 박스 모델은 HTML 요소를 사각형 박스로 표현하고,
이 박스는 콘텐츠(content), 패딩(padding), 보더(border), 마진(margin) 각각의 네 부분으로 구성된다. 각 부분은 CSS 속성으로 제어할 수 있다.

![image](https://github.com/user-attachments/assets/287121bf-6ea6-4d51-a86b-3e04b6eacd03)


<br />
<br />

## 콘텐츠(content)
콘텐츠 영역은 실제 텍스트나 이미지가 들어가는 부분으로 이 영역의 크기는 width와 height 속성으로 설정할 수 있다.

```css
.box {
  width: 300px;
  height: 200px;
}
```


<br />
<br />

## 패딩(padding)

패딩은 콘텐츠와 보더 사이의 공간으로 콘텐츠와 보더 사이에 여백을 제공하며,
padding-top, padding-right, padding-bottom, padding-left 속성으로 개별적으로 설정하거나 padding 속성으로 한꺼번에 설정할 수 있다.

```css
.box {
  padding: 20px; /* 모든 방향에 20px 패딩 */
  padding: 10px 15px; /* 상하 10px, 좌우 15px 패딩 */
}
```

<br />
<br />

## 보더(border)

보더는 콘텐츠와 패딩을 감싸는 테두리이다.
보더의 두께, 스타일, 색상은 각각 border-width, border-style, border-color 속성으로 설정할 수 있으며, border 속성으로 한꺼번에 설정할 수도 있다.

```css
.box {
  border: 1px solid black; /* 1px 두께의 실선 검은색 보더 */
}
```

<br />
<br />

## 마진(margin)

마진은 보더와 이웃한 요소 사이의 공간이다.
마진은 margin-top, margin-right, margin-bottom, margin-left 속성으로 개별적으로 설정하거나 margin 속성으로 한꺼번에 설정할 수 있다.

```css
.box {
  margin: 20px; /* 모든 방향에 20px 마진 */
  margin: 10px 15px; /* 상하 10px, 좌우 15px 마진 */
}
```

