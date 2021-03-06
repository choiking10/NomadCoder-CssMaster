# 1.0 Life Before Flexbox

기존에는 각 박스의 위치를 맞춰주기 위해서 margin 값을 직접조절해줘야했음.

그렇게 할경우 변하는 화면에 대응하기 힘들었다.

그래서  flexbox가 나타났고 이걸 이용해서 이쁘게 만들수 있게 되었다.

잘못된 예

```css
.box {
  background: blue;
  width: 300px;
  height: 300px;
  display: inline-block;
  color: white;
}

.box:nth-child(2) {
  margin-left: 35px;
}

.box:nth-child(3) {
  margin-left: 20px;
}
```

# 1.1 Flexbox에서는 children과 소통하지 않아!

box의 위치, box의 marigin, box의 공간을 조절하지않음!

만약 flexbox를 조절하고 싶다면, flexbox container를 만들어야함.

예를들자면 body를 flexbox container로 만들어보자.

```css
body {
  display: flex;
}

.box {
  width: 200px;
  height: 200px;
  background: peru;
  color: white;
}
```

이렇게 하면 바로 box를 inline box를 사용한 것과같은 효과를 볼 수 있음.

## 주의할 점

flex box는 붙어있는 부모의 자식 바로 아래에만 영향력을 발휘함! 따라서 style sheet가 똑같고 아래와 같이 wrapper를 껴놓는다면 flexbox가 작동하지 않을 거야.
```html
<body>
    <div class="wrapper">
      <div class="box">1</div>
      <div class="box">2</div>
      <div class="box">3</div>
    </div>
  </body>
```

따라서 아래와 같이 바꿔줘야 한다.

```css
.wrapper {
  display: flex;
}
...
```

# 1.2 Main Axis and Cross Axis

flexbox에는 방향이 있는데 flex-direction 속성으로 이를 조절할 수 있음. 

flex-direction의 속성은 기본 값이 row 로 설정되어 있어.

flex-direction: row; # 일 때는 horizontal axis가 main axis임.

main axis 에서 `justify-content`를 사용하면 content를 움직일 수 있음. 

```css
.wrapper {
  display: flex;
  justify-content: center;
}
```

이 때, cross axis는 vertical이 된다. cross axis 방향으로 item을 옮길 때는 `align-items`를 사용한다.

그런데 아래와같이 설정해보면 변함이 없는 것을 확인 할 수 있음.

```css
.wrapper {
  display: flex;
  justify-content: space-around;
  align-items: center;
}
```

그 이유는 fater인 wrapper class의 height를 확인해보면 알 수 있는데, 그 크기가 box크기와 정확히 동일하기 때문에 이미 center에 위치해 있는것이기 때문. `height` 값을 주면 변경되는것을 볼수 있을거임. 

### 참고

`space-around` 속성은 각 box의 주변 공간을 서로 같게 만들어줌. (Main Axis 방향으로)


# 1.3 Column and Row

그런데 flex-direction을 바꿔주고 싶다면? 값을 `column`으로 설정해주고 관찰해보자.

# 1.4 align-self and order

## align-self

align-self는 부모에 적용하는 것이 아니라 개별적인 자식에게 스타일을 먹이고 싶을 때 적용하는 속성이야.

align-self는 마치 align-items과 같이 cross axis 방향으로 움직이게 되어 있어.

아래 예제를 보자.

```css
.father {
  display: flex;
  justify-content: space-around;
  height: 100vh; # 이게 있음을 잊지마! height 가 없으면 모두 같은 위치에 있을 거야. 
}

.child {
  width: 200px;
  height: 200px;
  background: peru;
  color: white;
}

.child:nth-child(2) {
  align-self: flex-end;
}

.child:nth-child(3) {
  align-self: center;
}
```

## Order 
이거는 html을 변경할 필요가 없을 때 유용해. 기본적으로 html의 위치를 변경해주면 되지만, 만약 그것이 어렵다면 아래와 같이 order를 조절할 수 있어.

order는 크기가 높을 수록 뒤에 배치되고, 크기가 낮을 수록 앞에 배치 돼. 

또한 order의 기본값은 0이야!

만약 아래와 같이 style을 먹였다면? 어떻게 될까? 또한,

```
.father {
  display: flex;
  justify-content: space-around;
  height: 100vh;
}

.child {
  width: 200px;
  height: 200px;
  background: peru;
  color: white;
  font-size: 50px;
}

.child:nth-child(1) {
  order: 1;
}
```

정답은 `2, 3, 1` 이었습니다. 뀨 

이게 바로 flex box에서 유일하게 자식에게 줄 수 있는 속성들이었어.

# 1.5 wrap, nowrap, reverse, align-content

 flexbox는 item들이 모두 같은줄에 있도록 유지함.  
 width를 변경하는일이있더라도 한줄에 다 때려넣으려고자 함.  
 width가 설정되어있다고 한다고해도

 이는 flex-wrap이 기본값이 nowrap으로 설정되어있기 때문이야.  
 child들이 그들의 크기를 유지하기 위해서는 아래와 같이 설정해주면 된다. 

```css
.father {
  display: flex;
  justify-content: space-around;
  height: 100vh;
  flex-wrap: wrap;
}

.child {
  width: 200px;
  height: 200px;
  background: peru;
  color: white;
  font-size: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
}
```

## reverse
flex의 속성에 줄수 있는 값으로는 reverse라는 애들이 있는데  
flex-direction에는 row-reverse, column-reverse가 있고  
flex-wrap에는 wrap-reverse 가 있어 필요하면 알아서 찾아보자.

## align-content

algin-contnet는 cross axis의 모양 배치를 변경함 (wrap 상태일때는 여러 줄에 걸쳐서 나타날 수 있는데 이 때 입맛에 맞게 적용하려면 이게좋을거같다!)

# 1.6 flex-grow, flex-shrink

flex-grow, flex-shrink는 child에게 줄수 있는 property야

기억해야할 건! flex가 nowrap이면 width가 설정되어있어도 줄어들게 된다. 그렇기 때문에 flexbox에서는 찌그러질수가 있어.

## flex-shrink
이렇게 찌그러질때 어떤 박스가 얼마만큼 찌그러질지를 설정할수가있어.

flex-shrink의 기본 값은 1인 상태야.

flex-shrink가 만약 2라면 1인 것들보다 2배이상 찌그러지게 된다.

아래코드를 확인해보자.

```
.father {
  display: flex;
  justify-content: space-around;
  height: 100vh;
}
.child {
  width: 400px;
  height: 200px;
  background: peru;
  color: white;
  font-size: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.child:nth-child(2) {
  background: #000000;
  flex-shrink: 2;
}
```

## flex-grow

flex-grow는 flex-shrink와는 정 반대의 작용을 해. 

flew-grow의 기본값이 0이야. 설정하게되면 빈공간을 채우게 만들지. 만약 여유공간이 없다면 shrink에 영향을 받겠지만, 빈공간이 만들어지면 flex-grow의 영향을 받아!

```
.father {
  display: flex;
  justify-content: space-around;
  height: 100vh;
}

.child {
  width: 400px;
  height: 200px;
  background: peru;
  color: white;
  font-size: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.child:nth-child(2) {
  background: #000000;
  flex-grow: 2;
}

.child:nth-child(3) {
  flex-grow: 1;
}
```

flex-grow는 반응형 웹을 디자인할때 유용해!

이제 width는 잘 사용하지 않을 거야.

## 1.7 flex-basis

flex-basis는 child에 적용되는 property야.

그냥 봤을때는 width랑 비슷하게 작동하는 것 같지만 **그렇지 않아.**

flex-basis는 element에게 처음 크기를 주는거야.

찌그러지거나 늘어나기 전에 말이야. 

사실 flex-basis는 width와 같아. **flex-direction이 row**일때는 말이야. 

정확히 flex-basis는 ***main axis***에 작용해.

이건 잘안써.. 사실 width와 같아서 width나 height를 사용해.

```css
.father {
  display: flex;
  justify-content: space-around;
  height: 100vh;
  flex-direction: column;
}

.child {
  flex-basis: 300px;
  background: peru;
  color: white;
  font-size: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.child:nth-child(2) {
  background: #000000;
  flex-grow: 1;
}

```

# flexbox froggy
해보자.
 http://flexboxfroggy.com/
