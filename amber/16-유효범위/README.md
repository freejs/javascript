## 유효범위

유효범위 = Scope = 변수의 수명  

지역 변수(local)와 전역 변수(global)  

전역변수는 웬만하면 쓰지 말 것.  

브래드피트 너무 멋있따.  

#### 익명함수
전역 변수를 아예 사용하고 싶지 않을 때.  

```
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
