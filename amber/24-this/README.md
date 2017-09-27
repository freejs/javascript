## this

'이것'
this 는 함수 호출 맥락을 의미한다. 어떠한 의미가 정해져 있지 않고 사용하는 상황에 따라 가변적이다. this 는 함수 안에서만 사용할 수 있는 변수이다. 이 변수안에 담겨있는 값의 의미는 함수를 어떻게 호출하느냐에 따라 달라진다.  

```javascript
function func(){
  if(window===this){
    document.write("window===this");
  }
}

func();
```

```
window===this
```

this 안에 담겨 있는 값이 window를 의미함을 알 수 있다. 즉, this 가 함수안에서 전역객체를 의미하는 window를 의미한다.  

#### 메소드를 호출했을 때 this 의 값

```javascript
var o = {
  func : function(){
    if(o===this){
      document.write("o===this");
    }
  }
}
```

```
o===this
```

어떠한 객체 안에서 메소드에서 그 메소드를 호출하면 그 메소드가 소속되어 있는 객체를 this 로 접근할 수가 있다.

정리하자면,

- func() 함수를 정의 후 호출했을 때, 이 함수가 어느 객체에 소속되어 있지 않은 경우에 이 안에서 this 는 window 라는 전역객체를 가르켰다. (브라우저에서)
- o.func() 메소드를 호출하게 되면 이 this 는 o 를 가르켰다.

하지만 이 둘은 결국 같은 얘기. window라는 전역객체가 원래 앞에 생략되어 있기 때문. 우리에게는 단지 함수를 호출하는 것과 메소드를 호출하는 것 두 다른 느낌만이 들 뿐이다.  

#### 생성자 안에서의 this

매순간 this 는 다른 매커니즘 같지만 결국에는 같은 선상에 있다.

```javascript
function func(){ //생성자
  funcThis=this;
}
var o1=func();

function func(){ //함수
  if(funcThis===window){
    document.write('window <br>');
  }
}
var o2 = new func(); //new 가 붙었으므로 객체
//o2는 undefined. 빈 객체가 들어가므로.
if(funcThis===o2){
  document.write('o2 <br>');
}
```

생성자로 사용될 때에는 this 의 값이 생성될 객체를 가리킨다.  
함수로 호출될 때에는 함수안에서 this 의 값은 window 를 가리킨다.  


#### apply를 이용해 함수를 호출 할 때의 this

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
//this 는 함수로써 호출한 것이므로 window가 된다. 따라서 3번째 case 실행.
func.apply(o);
//apply를 호출할 때 첫번째 인자로 함수 호출 context를 대입한다. 결국, this의 값은 첫번째 인자는 o 가 된다. 따라서 1번째 case 실행.
func.apply(p);
//p를 호출하면 this의 값은 p. 따라서 2번째 case 실행.
```

결과

```
window
o
p
```

객체- 주인(master)  
메소드- 노예(slave)  

함수를 어떻게 호출하느냐에 따라 window 가 되기도 하고 o 가 되기도 하고 p 가 되기도 한다. 어쨌든 자바스크립트에서의 함수는 어떻게 호출하느냐에 따라서 맥락적으로 어떠한 객체에 종속되는 존재이다.  

this 가 어떤 맥락에서 어떤 의미를 갖는지 잘 알아야 한다. this 는 변화무쌍하다.  

암튼 Javascript는 유연하고 브래드피트는 멋지다.
