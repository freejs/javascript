# 17 - 값으로서의 함수와 콜백

<https://opentutorials.org/course/743/6508>

9/23

# 값으로서의 함수와 콜백

## 함수의 용도 1

javascript에서는 함수도 객체다. 다시 말해서 일종의 값이다. 거의 모든 언어가 함수를 가지고 있다. Javascript의 함수가 다른 언어의 함수와 다른 점은 함수가 값이 될 수 있다는 점이다. 다음 예제를 통해서 그 의미를 알아보자.

```
function a(){}
```

위의 예제에서 함수 a는 변수 a에 담겨진 값이다. 또한 함수는 객체의 값드로 포함될 수 있다. 이렇게 객체의 속성 값으로 담겨진 함수를 메소드(method)라고 부른다.

```
a = {
  b:function(){

  }
};
```

함수는 값이기 때문에 다른 함수의 인자로 전달 될수도 있다. 아래 예제를 보자.

```
function cal(func, num){
  return func(num)
}
function increase(num){
  return num+1
}
function decrease(num){
  return num-1
}
alert(cal(increase, 1));
alert(cal(decrease, 1));
```

10행을 실행하면 함수 increase와 값 1이 함수 cal의 진자로 전달된다. 함수 cal은 첫번째 인자로 전달된 increase를 실행하는데 이 때 두번째 인자의 값이 1을 인자로 전달한다. 함수 increase는 계산된 결과를 리턴하고 cal은 다시 그 값을 리턴한다.

--------------------------------------------------------------------------------

## 함수의 용도 2

함수는 함수의 리턴 값으로도 사용할 수 있다.

```
function cal(mode){
  var funcs = {
    'plus' : function(left, right){return left + right},
    'minus' : function(left, right){return left - right}
  }
  return funcs[mode];
}
alert(cal('plus')(2,1));
alert(cal('minus')(2,1));
```

당연히 배열의 값으로도 사용할 수 있다.

```
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

--------------------------------------------------------------------------------

## 콜백

### 처리의 위임

값으로 사용될 수 있는 특성을 이용하면 함수의 인자로 함수로 전달할 수 있다. 값으로 전달된 함수는 호출될 수 있기 때문에 이를 이용하면 함수의 동작을 완전히 바꿀 수 있다. 인자로 전달된 함수 sortNumber의 구현에 따라서 sort의 동작방법이 완전히 바뀌게 된다.

```{.javascript}
function sortNumber(a,b){
  return b-a;
}
var numbers = [20, 10, 9, 8, 7, 6, 5, 4, 3, 2, 1];
alert(numbers.sort(sortNumber));
```

### 비동기 처리

콜백은 비동기처리에서도 유용하게 사용된다. 시간이 오래걸리는 작업이 있을 때 이 작업이 완료된 후에 처리해야 할 일을 콜백으로 지정하면 해당 작업이 끝났을 때 미리 등록한 작업을 실행하도록 할 수 있다. 다음 코드는 일반적인 환경에서는 작동하지 않고 서버 환경에서만 동작한다. 동영상을 참고한다.

**_datasource.json.js_**

```{.javascript}
{'title':'Javascript','author':'egoing'}
```

**_demo1.html_**

```{.html}
<!DOCTYPE html>
<html>
<head>
<script src="//code.jquery.com/jquery-1.11.0.min.js"></script>
</head>
<body>
<script type="text/javascript">
    $.get('./datasource.json.js', function(result){
        console.log(result);
    }, 'json');
</script>
</body>
</html>
```
