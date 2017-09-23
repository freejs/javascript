# 16 - 유효범위

<https://opentutorials.org/course/743/6495>

9/23

# 유효범위

## 전역변수와 지역변수

유효범위(Scope)는 변수의 수명을 의미한다. 아래의 예제를 보자. 결과는 global이다.

```
var vscope = 'global';
function fscope(){
  alert(vscope);
}
```

함수 밖에서 변수를 선언하면 그 변수는 전역변수가 된다. 전역변수는 어플리케이션 전역에서 접근이 가능한 변수다. 다시 말해서 어떤 함수 안에서도 그 변수에 접근 할 수 있다. 그렇기 때무네 함수 fscope 내에서 vscope를 호출 했을 때 함수 밖에서 선언된 vscope의 값 global이 반환된 것이다. 아래의 예제를 보자. 결과는 '함수안 local'과 '함수밖 global'이 출력된다.

```
var vscope = 'global';
function fscope(){
  var vscope = 'local';
  alert('함수안 '+vscope);
}
fscope();
alert('함수밖 '+vscope);
```

> 변수를 선언할 때는 꼭 var을 붙이는 것을 습관화해야 한다. 전역변수를 사용해야 하는 경우라면 그것을 사용하는 이유를 명확히 알고 있을 때 사용하도록 하자.

--------------------------------------------------------------------------------

## 유효범위의 효용

--------------------------------------------------------------------------------

## 전역변수의 사용

불가피하게 전역변수를 사용해야 하는 경우는 하나의 객체를 전역변수로 만들고 객체의 속성으로 변수를 관리하는 방법을 사용한다.

```
MYAPP = {}
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
```

전역변수를 사용하고 싶지 않다면 아래와 같이 익명함수를 호출함으로써 이러한 목적을 달성할 수 있다.

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

위와 같은 방법은 자바스크립트에서 로직을 모듈화하는 일반적인 방법이다.

--------------------------------------------------------------------------------

## 유효범위의 대상 (함수)

자바스크립트는 함수에 대한 유효범위만을 제공한다. 많은 언어들이 블록(대체로 {,})에 대한 유효범위를 제공하는 것과 다른 점이다. 아래 예제의 결과는 coding everybody이다.

```
for(var i = 0; i < 1; i++){
  var name = 'coding everybody';
}
```

자바에서는 아래의 코드는 허용되지 않는다. name은 지역변수로 for 문 안에서 선언 되었는데 이를 for문 밖에서 호출하고 있기 때문이다.

```
for(int i = 0; i < 10; i++){
  String name = 'egoing';
}
```

> 자바스크립트의 지역변수는 함수에서만 유효하다.

--------------------------------------------------------------------------------

## 정적 유효범위

자바스크립트는 함수가 선언된 시점에서의 유효범위를 갖는다. 이러한 유효범위의 방식을 정적 유효범위(static scoping), 혹은 렉시컬(lexical scoping)이라고 한다.

```
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

실행 결과는 5이다.
