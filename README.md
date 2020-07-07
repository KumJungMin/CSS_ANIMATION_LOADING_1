# 로딩 화면(1), 세 개의 원이 차례로 로딩되는 화면

## 1. preview

<img src="https://j.gifs.com/K1NWVr.gif" />


## 2. 코드 분석

### 1) html
- `<div>`안에 세 개의 `<span>` 요소를 자식으로 둔다.
- `<span>`은 이제 로딩할 때의 원이 된다.
- `<span>` 대신 `<div>`를 써도 된다. 대신 `class` 이름을 지정해야한다.

<br/>

#### (1) 하나의 div에 원 요소를 자식으로 둔다.
```html
<body>
    <div class="loading">
      <span></span>   <!--1. span은 하나의 원이다. -->
      <span></span>
      <span></span>
    </div>
</body>
```

<br/><br/>

### 2) css

#### (1) body안의 요소들을 상하좌우 중앙 배치한다.

```css

body {
    margin: 0; 
    display: flex;            /*내부 요소들이 차례로 배치 */
    justify-content: center;  /*내부 요소의 좌우 정렬 상태를 가운데로 설정*/
    align-items: center;      /*요소는 세로 중앙 배치*/
    height: 100vh;            /*웹 크기 변화에 따라 변경되는 반응형 수치*/
  }

```

<br/>

#### (2) `animation-delay`를 이용하여 순차적으로 동작한다.

```css

 .loading span {
    display: inline-block; /* span 내부요소들을 한줄로 세우기 */
    width: 10px;
    height: 10px;
    background-color: gray;
    border-radius: 50%;    /* span을 동그랗게 */
    animation: loading 1s 0s linear infinite;
    /* 이벤트명  반복시간  딜레이시간  이벤트처리부드럽게  이벤트무한반복*/
  }
  
  .loading span:nth-child(1) {  /*loading의 자식 중 첫번째 span*/
    /*nth-child : 형제 사이에서의 순서*/
    animation-delay: 0s;
    background-color: red;
  }
  
  .loading span:nth-child(2) {
    animation-delay: 0.2s;
    background-color: orange;
  }
  
  .loading span:nth-child(3) {
    animation-delay: 0.4s;
    background-color: yellowgreen;
  }

```

<br/>
<br/>

#### (3) `keyframe`을 사용하여 이벤트를 만든다.

- CSS 애니메이션에서 구간을 정하고 각 구간별로 다른 스타일을 적용시킬 수 있다.

- `animation-name`은 사용자가 직접 지정한 이름으로, @keyframes 가 적용될 애니메이션의 이름이다.

- `스테이지`는 0~100% 의 구간
 
- `CSS 스타일`은 각 스테이지(구간)에 적용시킬 스타일


```css

 @keyframes loading {        /*loading이라는 keyframe 애니메이션*/
    0%,                      /* 0, 50, 100은 구간*/
    100% {
      opacity: 0;            /* 안보였다가 */
      transform: scale(0.5); /*transform의 scale로 요소를 확대 또는 축소할 수 있음*/   
    }
    50% {
      opacity: 1;             /* 보였다가 */
      transform: scale(1.2); /* 1.2배 */
    }
  }

```

















