# 02 값으로서의 함수와 콜백
javascript에서 함수도 객체다. 즉, 변수에 함수를 담을 수 있다.

아래는 함수(function)이다.
```javascript
function a() { }
```

객체의 속성 값으로 담겨진 함수를 메소드(method)라고 부른다.
```javascript
a = {
  b: function() {

  }
}
```

함수의 인자값으로 다른 함수를 전달할 수 있다.
```javascript
function cal(func, num){
    return func(num)
}
function increase(num){
    return num+1
}
function decrease(num){
    return num-1
}
alert(cal(increase, 1));    // 2
alert(cal(decrease, 1));    // 0
```

이런 사용방법은 처음 알았다! 재미있다.
```javascript
function cal(mode){
    var funcs = {
        'plus' : function(left, right){return left + right},
        'minus' : function(left, right){return left - right}
    }
    return funcs[mode];
}
alert(cal('plus')(2,1));    // 3
alert(cal('minus')(2,1));   // 1
```

배열에 담는 방법도 진짜 신기하다!
```javascript
var process = [
    function(input){ return input + 10;},
    function(input){ return input * input;},
    function(input){ return input / 2;}
];
var input = 1;
for(var i = 0; i < process.length; i++){
    input = process[i](input);
}
alert(input);
```

함수가 사용될 수 있는 곳은 변수, 매개변수, 리턴값으로 다양하게 사용가능합니다.
이를 first-class citizen or first-class object라고 부릅니다.

### 콜백
함수의 인자에 들어가는 함수에 따라서 다르게 동작하는 경우에 콜백함수라 부른다.
```javascript
var numbers = [1, 3, 5, 6, 7,8, 9, 10, 2, 4]
var sortfunc = function(a, b) {
  return b - a;
}
alert(numbers.sort(sortfunc))
```

### Ajax를 이용한 비동기 처리
콜백을 통해서 사용자에게 임의의 처리를 요구한다. 이를  Ajax를 위한 처리는 동일하다.
하지만 무슨일을 해야할지에 대한 부분을 비지니스 로직이라고 한다.  
이를 사용자에게 위임 해야 하는데 이 부분은 콜백함수를 통해서 이루어 진다.   
Jquery이용해서 쓰던데 나중에 찾아봐야한다.
