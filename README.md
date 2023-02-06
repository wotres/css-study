# CSS Study

### 화면
https://wotres.github.io/css-study/

## image
### 비트맵 (Bitmap) 방식
* 픽셀이 모여 만들어짐
* jpeg, gif, png
* 정교하고 다양한 색상이 자연스러움
* 확대/축소시 계단형식으로 품질이 저하됨
#### jpeg (Joint Photographic coding Experts Group) 
* 압축률이 좋음 => 용량이 적음
* 24 bit

#### png (Portable Network Graphics)
* 비손실압축 => 용량이 큼
* 투명한 영역(Alpha Channel) 이 지원가능 => 배경없이 원하는 이미지만 출력가능
* 24 bit / 8 bit(256 개 색상) 

#### GIF
* 비손실압축
* 여러장의 이미지를 하나의 파일로
* 8 비트

#### WEBP
* 손실/비손실 압축 가능
* GIF 가능
* 구글에서 개발

### 벡터 (Vector) 방식
* 좌표 방식, 색상등 수학적 정보의 형태
* svg
* 확대 축소시 품질저하없음
* 정교한 이미지(풍경)는 표현이 어려움 => 점선면의 수학적 정보
* 로고 등에 사용

#### SVG (Saclable Vector Graphics)
* 해상도의 영향에서 자유로움
* CSS / JS 로 제어 가능
* 파일 및 코드 삽입 가능


## inline vs block
### inline (인라인 요소)
* 글자를 만들기 위한 요소
* 요소가 수평으로 쌓임
* 콘텐츠 크기만큼 자동으로 줄어듬
  * width/height 지정 안됨
  * margin 과 padding 은 좌우만 사용가능하고 위아래는 안됨
* 인라인 요소 내부에 블록 요소 불가
  * ex) <span><div></div></span>
* span / img / a / br / label

### block 요소 
* 레이아웃을 만들기 위한 요소
* 요소가 수직으로 쌓임
* 콘텐츠 가로 크기는 부모요소의 크기만큼 자동을 늘어남
* 콘텐츠 세로 크기는 콘텐츠 크기만큼 자동으로 줄어듬
* div / h1 / p / ul / li


### inline-block
* 수평으로 쌓임
* 가로세로 크기 지정 가능
* 여백 지정 가능
* input

## css
* 선택자 { 속성: 값; }
* 주석 /* */
* class 속성 .className
* id 속성 #id
### 일치 선택자
* 두개 모두 만족
```css
div.className {
  color: red;
}
```

### 자식 선택자
* 선택자의 자식 >
```css
div > .className {
  color: red;
}
```

### 후손 선택자
* 띄워쓰기
```css
div  .className {
  color: red;
}
```

### 인접 형제 선택자
* 선택자의 다음 형제 요소 하나 선택 +
```css
.className + div {
  color: red;
}
```

### 일반 형제 선택자
* 선택자의 형제 요소 모두 선택
```css
.className ~ div {
  color: red;
}
```

### 가상 클래스 선택자 (Pseudo-classes)
```css
.btn:hover {
  color: red
}
.btn:focus {
  color: red
}
.btn:active {
  color: red
}
.btn:first-child {
  color: red;
}
.btn:last-child {
  color: red;
}
.btn:nth-child(1) {
  color: red;
}
.btn:nth-child(2n) {
  color: red;
}
/* 부정 선택자 */
.btn:not(span) {
  color: red;
}
```

### 가상 요소 선택자 (Pseudo-Elements)
* 인라인 요소
```css
/* 요소의 내부 앞에 내용을 삽입 */
.btn::before {
  content: '앞';
}
/* 요소의 내부 뒤에 내용을 삽입 */
.btn::after {
  content: '뒤';
}

/* 크기 지정 해주고 싶다면 */
.btn::before {
  display: block;
  width: 30px;
  height: 30px;
  content: '앞';
}
```
### 속성 선택자 (Attribute)
* 속성을 포함한 요소 선택
```html
<input type="text" disabled>
```
```css
[disabled] {
  color: red;
} 
```

### 상속 되는 css 속성
* font-style / font-weight / font-size
* line-height / font-family / color / text-align
* inherit 속성으로 상속 가능

### css 선언 방식
* 우선순위
  * 인라인 방식 > 내장 방식
* 내장 방식 <style></style> 안에 내용으로 삽입
```css
div {
  color: red;
}
```
* 인라인 방식 요소의 style 속성에 직접 작성 ( 우선순위 높아서 인라인은 권장 X)
```html
<div style="color: red;"></div>
```
* 링크 방식(link 로 외부 css 문서 가져옴) (병렬 연결 => 한번에 link들 불러옴)
```html
<link rel="stylesheet" href="./css/main.css">
```
* import 방식: 다른 문서를 불러옴 (직렬 연결)
```css
/*@import url("./temp.css");*/
div {
  color: red;
}
```

### 선택자 우선순위
* 아래 예시의 글자 색상은 red
* 인라인 선언은 1000점
* id 선택은 100점
* class 선택자는 10점
* 태그 선택자는 1점
* 전체 선택자 0점
* !important 99999점
```html
<div id="testId" class="testClass" style="color: orange;">
  color
</div>
```
```css
div { color: red !important; }
#testId { color: yellow; }
.testClass { color: green; }
div { color: blue; }
* { color: darkblue; }
body { color: purple }

```

## css 속성
* html 은 Attributes / css와 js 는 properties
* width/height
  * auto(default 값 => 브라우저가 자동으로 너비 계산)
* border
  * border-width border-style border-color
    * style 은 solid/dashed 등이 있음
* box-sizing
  * border-box => 요소의 내용 + padding + border 크기로 계산
* overflow
  * hidden : 넘친 내용 잘라냄
* display
  * block / inline / inline-block / flex
* opacity
  * 0 ~ 1
* font-weight
  * normal, 400
  * bold, 700
* line-height
  * 한줄의 높이
  * 숫자: 요소의 글꼴크기의 배수
  * px, em, rem
  * height 와 동일하게 지정하면 문자 세로 가운데
* text-align
  * center : 글자 중앙
* text-decoration
  * none : 선 장식 없음
* text-indent
  * 들여쓰기 가능
    * px
* background-position 으로 위치 지정(x축, y축)
  * top left / 100px 100px
* background-repeat 하나의 이미지만
  * no-repeat
* background-size
  * cover 는 이미지가 넓은 부분에 맞춰짐
  * contain 은 짧은 부분에 맞춰짐
* position
  * absolute 는 부모 요소를 기준
    * relative or fixed 를 기준으로 배치
    * 사용시 display 는 block 으로 변경
  * relative 는 자신을 기준
    * 요소가 원래위치해야하는 곳에서의 이동
  * fixed
    * 뷰포트 기준
    * 사용시 display 는 block 으로 변경
* z-index
  * 숫자가 클수록 높게 쌓임
* transition
  * 전환 시간
  * 속성명 지속시간 타이밍함수 대기시간
  * transition-property
    * 적용할 속성
    * width 1s => width 에만 영향
  * transition-duration
    * 지속 시간
  * transition-timing-function
    * 타이밍
    * ease / linear 와 같이 속도차이
    * easing functions
  * transition-delay
    * 대기시
* transform
  * translate(x, y) : 이동
  * scale(x, y) : 크기
  * rotate(degree) : 각도
  * skewX(x) : 기울임
  * skeyY(y) : 기울임
  * perspective(n : 원근법) / 항상 앞에 작성
    * transform: perspective() 를 넣으면 자식요소에서 원근법(자식 중앙)
    * perspective: 는 부모 속성에서 원근법(부모 중앙)
* backface-visibility
  * 3D 변환 뒷면 숨김여부

### flex vs grid
* 레이아웃 => 웹요소를 올바른 장소에 배치하는 기술
#### flex
* 행 / 열 을 주축으로 웹 요소를 배치 및 정렬하는 1차원 레이아웃
* flex
  * 수평정렬
  * flex-direction 으로 방향
  * flex-wrap 으로 넘침 요소 줄바꿈
  * justify-content 으로 주축 정렬
  * align-content 으로 교차축 정렬
  * flex-grow: 증가 너비 비율
    * 남은 부분을 나눈다.
    * 내용물에 상관없이 너비를 할당하려면 flex-basis를 0으로 주고 할당한다.
  * flex-basis: 내부 너비를 어느정도로 가져갈것인가
  * flex-shrink: 축소 비율
    * 화면 줄어들때 더 줄어든다.
  * align-content
    * space-around 등 사용가능
    * flex-wrap: wrap 일때 사용
  * align-item
    * flex-wrap: unwrap 일떄 사용
#### grid
* 격자 형태의 레이아웃을 만드는 2차원 레이아웃 
* grid
  * 행(row)과 열(column)이다
  * grid-template-columns
    * 열 트랙의 아이템 크기 결정
    * auto-fill
      * 컨텐츠의 최소값보다 크면 그자리는 비워둠
    * auto-fit
      * 컨텐츠의 최소값보다 크면 그자리에 컴텐츠 늘어남
  * grid-template-rows
  * grid-gap
    * 간격을 지정하는 속성
  * grid-row
    * 1/3 => 1번부터 3번까지 row 차지하게함
    * grid-row-start / grid-row-end 와 같음
  * grid-template-areas
    * 이름을 이용한 형태 정의
  * align-items
    * 트랙안에서의 배치
  * align-self
    * 아이템 스스로의 배치
  * justify-items
    * 트랙에서의 배치
  * justify-self
    * 아이템 스스로의 배치
  * align-content
    * 컨테이너에서의 배치
  * justify-content
    * 컨테이너에서의 배치

## 단위
* px: 픽셀
* %: 상대적 백분율
* em: 요소의 글꼴크기
* rem: 루트 요소(html)의 글꼴 크기
* vw: 뷰포트 가로 너비의 백분율
* vh: 뷰포트 세로 너비의 백분율

## 색상
* 이름 지정: red
* Hex(16진수) 색상 코드: #FFF
* 빛의 삼원색(RGB): rgb(255, 255, 255)
* 빛의 삼원색(RGB) + 투명도: rgb(255, 255, 255, 0.5)


## CSS 전처리기(CSS Preprocessor)
* Css 를 좀 더 쉽게 개발 할 수 있게 해줌
* 웹서버가 인지할 수 있게 각 CSS 전처리기에 맞는 Compiler 를 사용
* SASS, SCSS


## etc
* label 로 input 을 감싸면 글자를 클릭해도 체크박스 클릭됨
```html
<label>
  <input type="checkbox"/> A
</label>
```

* radio type 은 하나만 선택되게 하기 위해 name 으로 그룹 지정해줘야함
```html
<label>
  <input type="radio" name="group"/> A
</label>
<label>
  <input type="radio" name="group"/> B
</label>
```

