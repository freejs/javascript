## 클로저

클로저(Closure)는 내부함수가 외부함수의 맥락에 접근할 수 있는 것.  
자바스크립트를 이용한 고난이도의 테크닉을 구사하는데 필수적인 개념으로 활용된다.  

<br>

#### 내부함수
함수 안에 있는 함수.

<br>

#### 외부함수
함수를 포함하고 있는 함수. 함수를 감싸고 있는 함수.  

```javascript
function inner(){

}
```

```javascript
var inner = function(){

}
```

두 코드는 같다.  

어떠한 함수 안에서만 사용하는 함수가 있을 수 있다. 그럴 때 보통 내부함수, 외부함수 사용.  
내부함수에서 외부함수의 지역변수에 접근할 수 있는 것을 클로저라고 한다.  

클로저는 어렵다.
