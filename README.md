# CSS Study


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
<link rel="stylesheet" href="./css/main.css>
```
* import 방식: 다른 문서를 불러옴 (직렬 연결)
```css
@import url("./temp.css");
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

