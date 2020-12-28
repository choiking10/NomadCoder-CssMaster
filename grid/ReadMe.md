
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




