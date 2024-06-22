## CSS 에서 margin과 papdding이란?

- margin : 박스의 바깥쪽 여백
- padding : 박스의 안쪽 여백
  
|화면|개발자도구|
|:----:|:----:|
|![image](https://github.com/aksen123/Interview-questions/assets/126546293/00d40a67-3d89-47be-8ea1-a582fbf2beb6)|![image](https://github.com/aksen123/Interview-questions/assets/126546293/cdf6050a-6b1c-494b-bf0b-0ceb09dc6a05)|



## CSS에서 position 속성

- static: 요소를 일반적인 문서 흐름에 따라 배치 ( 기본값)
- relative: 요소의 원래 위치를 기준으로 top, bottom, left, right 값을 이용해 이동할 수 있다.
   ![image](https://github.com/aksen123/Interview-questions/assets/126546293/07a59da7-6aa2-4e90-b6f8-f4b929827b9f)
- absolute: 요소를 일반적인 문서 흐름에서 제거하고, 상위 요소들 중 position 속성이 static이 아닌 첫 번째 상위 요소를 배치 기준으로 설정한다. 만약 static이 아닌 요소가 없다면 DOM트리 최상위에 있는 body요소가 배치 기준이 된다.
  - absolute인 요소는 HTML문서 상에서 독립되어 앞뒤에 나온 요소와 더이상 상호작용을 하지 않는다.
   ![image](https://github.com/aksen123/Interview-questions/assets/126546293/87a01821-a46a-4cc8-9d1e-6e3b30851858)
- fixed : 요소를 일반적인 문서 흐름에서 제거하고, 뷰포트(브라우저 전체화면)를 기준으로 삼아 배치 한다. ( 스크롤을 내리거나 해도 화면에 보이는 위치는 그대로 )
  |초기화면|스크롤 내렸을때|
  |:----:|:----:|
  |![image](https://github.com/aksen123/Interview-questions/assets/126546293/dc8de437-6655-4d9f-bd16-e549342c5d71)|![image](https://github.com/aksen123/Interview-questions/assets/126546293/5d3c1d92-ae2c-4941-ae0b-563fcbf2718a)|
- sticky :  static와 fixed의 특징을 동시에 갖는다. 문서의 흐름에 따라 배치 되고 top, bottom, left, right을 주면 스크롤이 sticky요소를 지나가면 fixed처럼 지정해둔 위치에 계속 보이게 됨.
  |요소를 지나기전|지난 후|
  |:----:|:----:|
  |![image](https://github.com/aksen123/Interview-questions/assets/126546293/7cddaec2-bfcf-4b37-9c2e-5d65c20af472)|![image](https://github.com/aksen123/Interview-questions/assets/126546293/6c06e272-8608-4dd5-93b2-ff2577157b09)|



## 🙋‍♂️ 추가 / 용어

 ### ✔️ 뷰포트 
  - 뷰포트(viewport)는 화면에서 실제 내용이 표시되는 영역으로, 데스크톱은 사용자가 설정한 해상도가 뷰포트 영역이 되고, 스마트 기기는 기본으로 설정되어 있는 값이 뷰포트 영역
