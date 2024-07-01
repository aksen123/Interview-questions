# display 속성

CSS에서 display 속성은 HTML 요소가 페이지에 어떻게 표시될지를 결정한다. 다양한 값이 있으며, 각 값은 요소의 레이아웃과 동작을 변경한다.


<br />
<br />

## 1. display: none;
**none**을 설정하면 요소를 화면에서 보이지 않게 된다. 요소를 DOM에서 제거하지는 않지만 렌더링에서 제외되며, `visibility:hidden`과는 다르게 요소가 차지하는 공간조차 없애버린다.

<br />
<br />

## 2. display: block;
요소를 블록 레벨 요소로 만들어 준다. 항상 새로운 줄에서 시작되며 너비는 가능한 전체를 차지한다.( 부모 요소의 전체 너비, 세로 너비는 내용에 따라 결정 )
`block`요소는 `width`, `height`, `margin`, `padding`과 같은 속성을 모두 적용할 수 있으며,HTML 요소 중 `<div>`, `<p>`,`<h1>`등이 기본적으로 `block`요소이다.

<br />
<br />

## 3. display: inline;
요소를 인라인 레벨로 만들어 준다. 줄 바꿈 없이 요소 내부의 콘텐츠만큼의 너비를 가진다. 주로 텍스트 내에서 사용된다.
`width`, `height`, `margin` 속성은 적용되지 않으며  `padding`은 적용 되지만 레이아웃에 영향을 주지 않는다.
`<span>`, `<a>`, `<img>`등이 `inline`요소이다.


<br />
<br />

## 4. display: inline-block;
  `block`과 `inline`의 중간 형태로 줄 바꿈없이 다른 요소와 같은 줄에 배치 되지만, `block`처럼 `width`, `height`, `margin`, `padding`을 모두 적용할 수 있다.
  `inline-block`요소는 텍스트 기준선에 맞춰 정렬되며, 다른 `inline-block`와 정렬을 조정할 때는 `vertical-align` 속성을 사영해 조정할 수 있다.
  `<button>`, `<input>` 등이 `inline-block` 요소이다.

<br />
<br />

## 5. display: flex;
<details>
 <summary> 내용 보기</summary>
요소를 플렉스 컨테이너로 설정하여 내부 요소들을 그리드 아이템으로 표시한다. `flex` 컨테이너 내의 아이템들을 가로나 세로축을 기준으로 유연하게 배치할 수 있다.
즉, 자식요소들을 다양한 방향과 순서로 정렬할 수 있게 해주는것.

### flex 옵션
  
1. flex-direction: 플렉스 아이템들의 주축 행(row), 열(column)방향 설정 기본값은 row이다. **row, row-reverse, column, column-reverse**
    <details>
      
     ![flex-direction](https://www.heropy.dev/postAssets/Ha29GI/flex-direction.jpg)
    </details>
   
2. flex-wrap: 플렉스 아이템들이 컨터이너 내에서의 줄바꿈 여부 기본값은 nowrap이다. **nowrap, wrap, wrap-reverse**
    <details>
      
     ![flex-wrap](https://www.heropy.dev/postAssets/Ha29GI/flex-wrap.jpg)
    </details>
   
3. flex-flow: flex-direction과  flex-wrap을 단축 속성으로 설정 **flex-flow: row wrap**

4. justify-content: flex-direction으로 설정한 주 축을 따라 아이템을 정렬 **flex-start, flex-end, center, space-between, space-around, space-evenly**
    <details>
      
     ![flex-wrap](https://www.heropy.dev/postAssets/Ha29GI/flex-justify-content.jpg)
    </details>

5. align-items: 교차축을 따라 아이템을 정렬 기본값은 stretch이다. 주의할 점은 Items가 flex-wrap을 통해 여러 줄(2줄 이상)일 경우에는 `align-content` 속성이 우선이라 `align-items`를 사용하려면 align-content 속성을 기본값(stretch)으로 설정해야 한다. **stretch, flex-start, flex-end, center, baseline**
    <details>
      
     ![align-items](https://www.heropy.dev/postAssets/Ha29GI/flex-align-items.jpg)
    </details>

6. align-content: 여러 줄의 교차 축 정렬 기본값은 stretch이다. **stretch, flex-start, flex-end, center, space-between, space-around**
    <details>

      ![align-content](https://www.heropy.dev/postAssets/Ha29GI/flex-align-content.jpg)
    </details>



### 자식요소 옵션

1. order: 플렉스 아이템의 순서를 설정
2. flex-grow: item의 증가 너비 비율을 설정한다. 숫자가 크면 더많은 너비를 가진다.
   <details>
     ![flex-grow](https://www.heropy.dev/postAssets/Ha29GI/flex-grow.jpg)
   </details>
3. flex-shrink: item이 감소하는 너비의 비율을 설정한다. 숫자가 크면 더 많은 너비가 감소한다.
   <details>

     ![flex-shrink](https://www.heropy.dev/postAssets/Ha29GI/flex-shrink.jpg)
   </details>
4. flex-basis: item의 기본 크기를 설
   <details>

     ![flex-basis](https://www.heropy.dev/postAssets/Ha29GI/flex-basis.jpg)
   </details>

5. flex: `flex-grow`, `flex-shrink`, `flex-basis`의 단축 속성 `flex: 1 1 100px;`
6. align-self: 특정 item의 교차축 정렬을 설정 `align-items`속성보다 우선순위이다.
    <details>
    
      ![align-self](https://www.heropy.dev/postAssets/Ha29GI/flex-align-self.jpg)
    </details>



</details>

<br />
<br />

## 6. display: grid;
<details>
  `grid`는 2차원(행,열)형태로 요소를 배치할 수있다. 복잡한 레이아웃을 구현할때 유용하다.


### grid 옵션
1. 


</details>
  
