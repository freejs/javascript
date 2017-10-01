# 06 prototype
prototype은 한국어로 원형이란다. 핳핳핳핳  
알기 쉽게 이야기 하자면 객체의 원형을 의미한단당.  
오오... 바로 이해가 됬어!!  

이걸 보고 한번에 이해했길 바란다.

```javascript
function Ultra() {}
Ultra.prototype.ultraProp = true;

function Super() {}
Super.prototype = new Ultra();

function Sub() {}
Sub.prototype = new Sub();

var o = new Sub();
console.log(o.ultraProp);
```

위나 아래나 거기서 거기!!
```javascript
function Ultra() {
  this.ultraProp = true;
}

function Super() {
  this.ultraProp = true;
}

function Sub() {
  this.ultraProp = true;
}

var o = new Sub();
console.log(o.ultraProp);
```
서로가 서로에 연결되어있는 이러한 개념을 바로  Prototype Chain이라고 한당!! 크아아아앙!!

Prototype Chain
1. 객체 o에서 ultraProp를 찾는다.
2. 없다면 Sub.prototype.ultraProp를 찾는다.
3. 없다면 Super.prototype.ultraProp를 찾는다.
4. 없다면 Ultra.prototype.ultraProp를 찾는다.

주의할점이 있다!!
prototype을 상속 받을 때는 직접적으로 prototype을 전달할 경우 하위 객체의 기능 추가가 부모객체에 반영되므로 꼭꼭꼭!! 생성자를 사용하여 객체의 prototype을 전달해야 합니다.
```javascript
function Ultra() {}
Ultra.prototype.ultraProp = true;

function Super() {}
Super.prototype = new Ultra();

function Sub() {}
Sub.prototype = new Sub();
// Sub.prototype = Super.prototype
// 위에 처럼 사용하면 ㅈ됩니당

var o = new Sub();
console.log(o.ultraProp);
```
