## 유효범위

유효범위 = Scope = 변수의 수명  

지역 변수(local)와 전역 변수(global)  

*Javascript에서 지역변수는 JAVA와 달리 함수 안에서 선언된 것만이 지역 변수. for문이나 if 문 이런 곳 안에서 선언된 것은 지역변수로써 의미를 갖지 않는다. 주의!*

전역변수는 웬만하면 쓰지 말 것.  

브래드피트 너무 멋있따.  

<br>

#### 익명함수
전역 변수를 아예 사용하고 싶지 않을 때.  

```javascript
(function(){
    var MYAPP = {}
    MYAPP.calculator = {
        'left' : null,
        'right' : null
    }
    MYAPP.coordinate = {
        'left' : null,
        'right' : null
    }
    MYAPP.calculator.left = 10;
    MYAPP.calculator.right = 20;
    function sum(){
        return MYAPP.calculator.left + MYAPP.calculator.right;
    }
    document.write(sum());
}())
```


<br>

### 정적 유효범위(static scoping, lexical scoping)

사용될 때가 아닌 정의될 때의 전역변수가 사용된다.

```Javascript
var i = 5;

function a(){
    var i = 10;
    b();
}

function b(){
    document.write(i);
}

a();
```

결과

```javascript
5
```
