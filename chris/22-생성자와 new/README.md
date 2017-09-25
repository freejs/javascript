# 22 - 생성자와 new

<https://opentutorials.org/course/743/6570>

9/25

# 생성자와 new

--------------------------------------------------------------------------------

## 객체

--------------------------------------------------------------------------------

객체란 서로 연관된 변수와 함수를 그룹핑한 그릇이라고 할 수 있다. 객체 내의 변수를 프로퍼티(property) 함수를 메소드(method)라고 부른다. 객체를 만들어보자.

```javascript
var person = {}
person.name = 'egoing';
person.introduce = function(){
  return 'My name is '+this.name;
}
document.write(person.introduce());
```

객체를 만드는 과정에 분산되어 있다. 객체를 정의 할 때 값을 셋팅하도록 코드를 바꿔보자.

```javascript
var person = {
  'name' : 'egoing',
  'introduce' : function(){
    return 'My name is '+this.name;
  }
}
document.write(person.introduce());
```

만약 다른사람의 이름을 담을 객체가 필요하다면 객체의 정의를 반복해야 할 것이다. 객체의 구조를 재활용할 수 있는 방법이 필요하다. 이 때 사용하는 것이 생성자다.

## 생성자

--------------------------------------------------------------------------------

생성자(constructor)는 객체를 만드는 역할을 하는 함수다. 자바스크립트에서 함수는 재사용 가능한 로직의 묶음이 아니라 객체를 만드는 창조자라고 할 수 있다.

```javascript
function Person(){}
var p = new Person();
p.name = 'egoing';
p.introduce = function(){
  return 'My name is '+this.name;
}
document.write(p.introduce());
```

함수를 호출할 때 new을 붙이면 새로운 객체를 만든 후에 이를 리턴한다. 위의 코드는 새로운 객체를 변수 p에 담았다. 여러사람을 위한 객체를 만든다면 아래와 같이 코드를 작성해야 할 것이다.

> **_함수에 new를 붙여서 생성하면 객체가 된다. 가장중요!!_**

```javascript
function Person(){}
var p1 = new Person();
p1.name = 'egoing';
p1.introduce = function(){
  return 'My name is '+this.name;
}
document.write(p1.introduce()+"<br />");

var p2 = new Person();
p2.name = 'leezche';
p2.introduce = function(){
  return 'My name is '+this.name;
}
document.write(p2.introduce());
```

별로 개선된 것이 없다.

```javascript
function Person(name){
  this.name = name;
  this.introduce = function(){
    return 'My name is '+this.name;
  }
}
var p1 = new Person('egoing');
document.write(p1.introduce()+"<br />");

var p2 = new Person('leezche');
document.write(p2.introduce());
```

생성자 내에서 이 객체의 프로퍼티를 정의하고 있다. 이러한 작업을 초기화라고 한다. 이를 통해서 코드의 재사용성이 대폭 높아졌다.

코드를 통해서 알 수 있듯이 생성자 함수는 일반함수와 구분하기 위해서 첫글자를 대문자로 표시한다.

## 자바스크립트 생성자의 특징

--------------------------------------------------------------------------------

일반적인 객체지향 언어에서 생성자는 클래스의 소속이다. 하지만 자바스크립트에서 객체를 만드는 주체는 함수다. 함수에 new를 붙이는 것을 통해서 객체를 만들 수 있다는 점은 자바스크립트에서 함수의 위상을 암시하는 단서이면서 또 자바스크립트가 추구하는 자유로움을 보여주는 사례라고 할 수 있다.
