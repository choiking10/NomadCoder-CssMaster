
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