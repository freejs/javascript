## 전역객체
전역객체(Global object)는 특수한 객체이다. 모든 객체는 이 전역 객체의 property다. 나니?  

```javascript
funcion func(){
  alert("나니?");  
}
```

사실상 실행 방법 두가지.

```javascript
func();
```

```javascript
window.func();
```

이것이 의미하는 바는 window 가 객체, 그리고 func()가 속성이라는 뜻이다. 즉, func()는 속성이자 함수이자 window 라는 객체의 메소드이다. 하지만 이 window 라는 객체를 생략해도 실제는 이것을 붙인 것과 같이 실행이 된다. 생략해도 암시적으로 window를 붙여서 실행되는 격.

```javascript
var o = {'func':function(){
  alert('Hello');
}}
o.func();
window.o.func(); //같은 결과 출력
```

여기서 o 는 window 객체의 property 인 것.
즉, javascript에서는 모든 객체가 기본적으로 전역객체의 property인 것이다.  

하지만 이것은 호스트 환경에 따라 달라진다. 만약 nodejs 와 같이 웹브라우저가 아닌 서버측 javascript 를 쓰고 있다면 window라는 것은 존재하지 않는다. 대신 global이라는 것이 존재. 글로벌객체의 이름은 호스트 환경에 따라 달라질 수는 있지만, ES에서 정의된 글로벌객체의 API 들을 모두 가지고 있다는 공통점이 있다.
