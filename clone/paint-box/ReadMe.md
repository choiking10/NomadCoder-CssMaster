# Paint Box

- 코드가 전체적으로 흥미로운 것들은 없는 것 같음
- 상단에 고정되어있는 메뉴작성이 좀 힘들었고
- 흥미로웠던 점은 footer에 있는 vertical line을 background-color로 이용할 수 있다는거임.

몇개지 advanced 한 내용중 하나는

```scss
body {
  & > *:net(.fotter) {
    padding: 0px 140px;
  }
}
```

이런건데 body의 direct children(`>`) 중 .footer 클래스를 가지지 않는(`not(.footer)`) 모든(`*`) 애들에 대해서 `padding 0px 140px`를 먹여준다는거임.  
유용해보이는데 중요하게 볼 점은 `>` 은 바로 밑에 자식을 의미한다는걸 알았음.

이거 계속클로닝이야할수있지만 약간 시간낭비같아서 몇가지 폼만 시도해보고 다음으로 넘어가야겠음.

css의 clean code 에대해서 고민해봐야겠는데, 지금은 너무 주먹구구식으로 짜는거같음.

다음에는 재사용성에 대해서 좀더 생각해보도록 하자.

.footer에서 중간에 vertical line을 그리는 것이 있는데,
![](images/2021-01-08-23-23-19.png)
중간 라인에 대해서 나는 background-color를 black으로 주고 gap을 1px을 줘서 생성함.
그런데 nomadcoder를 보니까.

```scss
.footer__column {
  &:nth-child(2) {
    border-right: 1px solid black;
    border-left: 1px solid black;
  }
}
```

이렇게 짰떠라... 이게더 나은거같음
