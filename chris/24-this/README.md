# 24 - this

<https://opentutorials.org/course/743/6571>

9/26

# this

--------------------------------------------------------------------------------

this는 함수 내에서 함수 호출 맥락(context)를 의미한다. 맥락이라는 것은 상황에 따라서 달라진다는 의미인데 즉 함수를 어떻게 호출하느냐에 따라서 this가 가리키는 대상이 달라진다는 뜻이다. 함수와 객체의 관계가 느슨한 자바스크립트에서 this는 이 둘을 연결시켜주는 실질적인 연결점의 역할을 한다.

## 함수호출

--------------------------------------------------------------------------------

함수를 호출했을 때 this는 무엇을 가르키는지 살펴보자. this는 전역객체인 window와 같다.

```javascript
function func(){
  if(window === this){
    document.write("window === this");
  }
}
func();
```

결과

```javascript
window === this
```

## 메소드의 호출

--------------------------------------------------------------------------------

객체의 소속인 메소드의 this는 그 객체를 가르킨다.

```javascript
var o = {
  func : function(){
    if(o === this){
      document.write("o === this");
    }
  }
}
o.func();
```

결과

```javascript
o === this
```

## 생성자의 호출

--------------------------------------------------------------------------------

아래 코드는 함수를 호출했을 때와 new를 이용해서 생성자를 호출했을 때의 차이를 보여준다.

```javascript
var funcThis = null;

function Func(){
  funcThis = this;
}
var o1 = Func();
if(funcThis === window){
  document.write('window <br />');
}

var o2 = new Func();
if(funcThis === o2){
  document.write('o2 <br />');
}
```

결과

```javascript
window
o2
```

생성자는 빈 객체를 만든다. 그리고 이 객체내에서 this는 만들어진 객체를 가르킨다. 이것은 매우 중요한 사실이다. 생성자가 실행되기 전까지는 객체는 변수에도 할당될 수 없기 때문에 this가 아니면 객체에 어떠한 작업을 할 수 없기 때문이다.

```javascript
function Func(){
  document.write(o);
}
var o = new Func();
```

결과는 아래와 같다.

```javascript
undefined
```

## apply, call

--------------------------------------------------------------------------------

함수의 메소드인 apply, call을 이용하면 this의 값을 제어할 수 있다.

```javascript
var o = {}
var p = {}
function func(){
  switch(this){
    case o:
      document.write('o<br />');
      break;
    case p:
      document.write('p<br />');
      break;
    case window:
      document.write('window<br />');
      break;
  }
}
func();
func.apply(o);
func.apply(p);
```

결과

```javascript
window
o
p
```
