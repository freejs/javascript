# 25 - 상속

<https://opentutorials.org/course/743/6572>

9/26

# 상속

--------------------------------------------------------------------------------

## 상속(inheritance)이란?

--------------------------------------------------------------------------------

객체는 연관된 로직들로 이루어진 작은 프로그램이라고 할 수 있다. 상속은 객체의 로직을 그대로 물려 받는 또 다른 객체를 만들 수 있는 기능을 의미한다. 단순히 물려받는 것이라면 의미가 없을 것이다. 기존의 로직을 수정하고 변경해서 파생된 새로운 객체를 만들 수 있게 해준다.

아래 코드는 이전 시간에 살펴본 코드다.

```javascript
function Person(name){
  this.name = name;
  this.introduce = function(){
    return 'My name is '+this.name;
  }
}
var p1 = new Person('egoing');
document.write(p1.introduce()+"<br />");
```

결과

```javascript
My name is egoing
```

위의 코드를 아래와 같이 바꿔보자.

```javascript
function Person(name){
  this.name = name;
}
Person.prototype.name=null;
Person.prototype.introduce = function(){
  return 'My name is '+this.name;
}
var p1 = new Person('egoing');
document.write(p1.introduce()+"<br />");
```

## 상속의 사용방법?

--------------------------------------------------------------------------------

```javascript
function Person(name){
  this.name = name;
}
Person.prototype.name=null;
Person.prototype.introduce = function(){
  return 'My name is '+this.name;
}
function Programmer(name){
  this.name = name;
}
Programmer.prototype = new Person();

var p1 = new Programmer('egoing')
document.write(p1.introduce()+"<br />");
```

Programmer이라는 생성자를 만들었다. 그리고 이 생성자의 prototype과 Person의 객체를 연결했더니 Programmer 객체도 메소드 introduce를 사용할 수 있게 되었다.

Programmer가 Person의 기능을 상속하고 있는 것이다. 단순히 똑같은 기능을 갖게 되는 것이라면 상속의 의의는 사라질 것이다. 부모의 기능을 계승 발전 할 수 있는 것이 상속의 가치다.

## 기능의 추가

--------------------------------------------------------------------------------

```javascript
function Person(name){
  this.name = name;
}
Person.prototype.name=null;
Person.prototype.introduce = function(){
  return 'My name is '+this.name;
}

function Programmer(name){
  this.name = name;
}
Programmer.prototype = new Person();
Programmer.prototype.coding = function(){
  return "hello world";
}

var p1 = new Programmer('egoing');
document.write(p1.introduce()+"<br />");
document.write(p1.coding()+"<br />");
```

결과

```javascript
My name is egoing
hello world
```

Programmer는 person의 기능을 가지고 있으면서 Person이 가지고 있지 않은 기능인 메소드 coding을 가지고 있다.

> prototype이 무엇인가 궁금할 것이다. 이번 시간은 상속에 대한 개념적인 부분만 살펴본 것이고 다음 시간에 prototype에 대해 구체적으로 알아보자.
