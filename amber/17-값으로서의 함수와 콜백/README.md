## 값으로서의 함수

함수가 일종의 값이라는 것은 함수 역시도 변수에 담을 수 있다는 것이다. 즉, 함수 자체가 값이 될 수 있다는 것이다. 또한 함수는 인자(parameter)도 될 수 있다.  

```javascript
function a(){}
```

a 라는 변수에 담겨진 함수.

```javascript
var a = function(){}
```

와 같다.

```javascript
a = {
  b : function(){  
  }
};
```

b 는 key, function(){}은 value.  
b (key)가 변수와 같은 역할을 하고 있다.  
b 를 속성이라고 한다. 이 속성의 값은 함수. 이 함수를 method 라고 부른다.  

그냥 정의 된 함수는 함수, 객체 안에 정의되어 있는 것은 method 라고 부른다.  

변수, 매개변수, 리턴값으로도 쓰이는 것을 first-class citizen/object 라고 한다.  


<br>

## 콜백

어떠한 함수가 수신하는 인자가 함수인 경우를 콜백이라고 한다.  
콜백이 가능한 것 또한 Javascript의 함수가 값이기 때문이다.  

<br>

#### 비동기 처리
**Ajaxㅡ** Asynchronous(비동기) Javascript and XML  
