# 3.0 CSS Preprocessors and Set up

SCSS는 preprocessor야. 어떤 scss code를 컴파일해서 일반적인 css code로만드는거지.

원래 사용되는거는 Sass였어. Sass는 SCSS와 같은 방식으로 사용할 수 있는데 다른 syntax를 가지고 있어서 ...
잘모르겠어 나중에 찾아봐야지.

## preprocessor

기존의 preprocessor로는 stylus가 있어.  
https://stylus-lang.com

또는 lesscss.org 가 있지.  
SCSS는 이제거의 업계표준이 되가고 있어.  
SCSS는 CSS를 programming language 처럼 만들어.

## 필요한 것들

### gulp

이건 compile하거나 transform 해주는 node js 패키지야.  
새로운 코드를 오래된 코드로 바꾸거나 SCSS, SASS를 일반적인 CSS로 바꿔야지.

다음을 실행해서 gulp를 설치하자.

보니까 따라하기 위해서는 이것저것 설치할게 많은 것같다.

package.json아래에 설치되어 있는 것들을 설치하고 gulpfile을 실행시키기 위해서는 아래와 같이 터미널을 실행시키면된다.

```console
npm i && npm dev run
```

대충해서 이렇게 한것까지는 좋은데 에러가좀나는듯? 나중에 gulp나 js를 다시한번 자세히 공부하는시간을 가져야할것같다. ㅠ

### trouble shooting - UnauthorizedAccess

power shell에서 execution policy가 restricted 로 설정되어 있어서 그럼.

powershell을 관리자 관한으로 연 뒤  
`executionpolicy`  
를 실행해보면 Restricted 라는 값이 나올 거임.  
`set-executionpolicy unrestricted`  
를 실행해서 권한을 풀어주면 된다.

참고 블로그 : https://cishome.tistory.com/138
