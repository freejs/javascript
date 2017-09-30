# 05 상속
상속받은 객체가 부모객체의 어떤 기능은 제외하고 어떤 기능은 추가하여 맥락에 맞게 사용.

영어로 inheritance!!

이것은 기본적인 객체의 사용법!
```javascript
function Person(name) {
  this.name = name;
  this.introduce = function() {
    return 'My name is ' + this.name;
  }
}

var pl = new Person('egoing')
document.write(p1.introduce()+"<br />");
```

```javascript
function Person(name) {
  this.name = name;
}

Person.prototype.name = null;
Person.prototype.introduce = function() {
  return 'My name is ' + this.name;
}
var pl = new Person('octave');
document.write(pl.introduce()+"<br />");
```

어찌하여 prototype에 대하여 알려주지 않는 것입니까...
인내하라니요...

### 상속 사용법
Person을 상속받는 Programer에 대하여 생각해보자.
와 진심 기묘하다....
자식의 프로퍼티에 부모의 프로퍼티를 넣는다라니... 뭥미
```javascript
function Person(name) {
  this.name = name;
}
Person.prototype.name = null;
Person.prptotype.introduce = function() {
  return 'My name is ' + this.name;
}

function Programer(name) {
  this.name = name;
}

Programer.prototype = new Person();

var p1 = new Programer('octave');
document.write(p1.introduce() + "<br />");
```

### 그래 감잡았어!!
생성자는 그냥 생성자로 있는 것이고...
property를 통해서 상속시킬 아이들을 정해주는 거고...
상속 받은 아이들은 또다시 prototype를 이용해 자신만의 함수를 만들어내고...
이 내용들을 또 상속시키면 또 상속 앜... 알다가 모르겠다
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

function Designer(name) {
  this.name = name;
}
Designer.prototype = new Person();
Designer.prototype.disign = function() {
  return "beautifull";
}

var p1 = new Programmer('geja');
document.write(p1.introduce()+"<br />");
document.write(p1.coding()+"<br />");

var p2 = new Designer('Deval');
document.write(p2.introduce()+"<br />");
document.write(p2.desing()+"<br />");
```

아앜!! 프로토타입이 모냐!!
