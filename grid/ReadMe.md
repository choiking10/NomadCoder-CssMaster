
# 2.1 Life Before Grid

flexbox로는 grid 형태를 만들기 어려움.

아래처럼 코드를 짰을 때, 5가 중앙에오지 않고 양쪽으로 흩어짐. 중앙으로 보내기가 어렵다.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="grid-styles.css" />
    <title>(S)CSS flexbox</title>
  </head>
  <body>
    <div class="father">
      <div class="child">1</div>
      <div class="child">2</div>
      <div class="child">3</div>
      <div class="child">4</div>
      <div class="child">5</div>
    </div>
  </body>
</html>
```

```css
.father {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}

.child {
  flex-basis: 30%;
  background: peru;
  font-size: 50px;
  color: white;
  display: flex;
  justify-content: center;
  align-content: center;
  margin-top: 10px;
}

```

# 2.2 CSS Grid Basic Concepts

grid은 대부분 flex랑 비슷한데, 항상 father에 적용됨. 

여기서 각 column 크기를 grid-template-columns로 설정할 수 있어.
그리고 각 column과 row 사이의 간격을 

 - row-gap
 - column-gap
 - gap

으로 설정할 수 있어.
```css
.father {
  display: grid;
}
.father {
  display: grid;
  grid-template-columns: 250px 250px 250px;
  grid-template-rows: 100px 100px 100px;
  gap: 10px;
  /* same as row-gap: 10px; column-gap: 10px; */
}
```

테스트를 위해서 emmet 으로 child를 많이 생성해보자! `div.child{$}*9` 유용하니 기억해두자구


# 2.3 Grid Template Areas

## repeat
그런데 위에 썹놓은거보면 grid의 column과 row만큼 반복되는거 너무거슬리지않니?

이걸 반복해줄 수 있는데 다음과 같이 쓰면 된당.

```css
.father {
  display: grid;
  grid-template-columns: repeat(4, 200px);
  /*same as grid-template-columns: 200px 200px 200px 200px;*/
  grid-template-rows: repeat(4, 300px);
  /*same as grid-template-rows: 300px 300px 300px 300px;*/
}
```

## grid template area

grid template area로는 손쉽게 layout을 디자인할 수 있어. 

예를들어보자. 

주로사용하는 layout을 그리기 위해서 

```css
.father {
  display: grid;
  grid-template-columns: repeat(4, 200px);
  /*same as grid-template-columns: 200px 200px 200px 200px;*/
  grid-template-rows: repeat(4, 200px);
  /*same as grid-template-rows: 300px 300px 300px 300px;*/
  grid-template-areas:
    "header header header header"
    "content content content nav"
    "content content content nav"
    "footer footer footer footer";
}
```
다음과 같이 네이밍을 써주면 그 모양으로 레이아웃을 디자인해줘. 개꿀이지.

주의할 점은 아래와 같이 각 클래스의 layout naming을 디자인해줘야한다는거야. 

grid-area의 속성값으로들어가는건 ***string이 아니라는 점*** 체크해 둬!
```css

.header {
  background-color: #2ecc71;
  grid-area: header;
}
.content {
  background-color: #3498db;
  grid-area: content;
}
.nav {
  background-color: #8e44ad;
  grid-area: nav;
}
.footer {
  background-color: #f39c12;
  grid-area: footer;
}
```

## auto
grid-template-columns 의 속성값으로 auto를 사용할 수 있는데 이 강의로는 잘 이해가안가고 아래의 참고하면 좋을 것 같은 블로그 껄 활용하자.
https://studiomeal.com/archives/533
