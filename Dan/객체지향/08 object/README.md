# 08 Object
모든 객체는 Object를 상속받습니다.
따라서 Object객체의 prototype을 추가하면 표준 내부 함수 확장에 의하여 모든 객체에서 추가된 객체를 사용할 수 있습니다.

#### Object.xxx 친구들과 Object.prototype.xxx 친구들은 어떤 차이가 있을까요 여러분?
(모르겠어요!!)

Object.xxx들은 Object.keys(arr)와 같이 사용하면 됩니다.
Object.prototype.xxx들은 o.toString()과 같이 사용하면 됩니다.

참 쉽죠?

### 그래서 무엇?
모든 객체에서 사용가능하도록 하는 Object의 함수 확장을 해보자.
```javascript
Object.prototype.contain = function(needle) {
  for(var name in this) {
    if(this[name] === needle) {
      return true;
    }
  }
  return false;
}

var o = {'name': 'octave', 'city': 'seoul'}
console.log(o.contain('octave'));
var a = ['egoing', 'octave', 'freejs'];
console.log(a.contain('freejs'));
```
하지만!! 이런식의 확장은 위험해!! 왤까?
답 => 모든 객체에 영향을 주기때문입니다. 짜잔

이게 좀 애매한 부분이 있는데...
name에 대해서 스터디에서 이야기 해봅시다.

갑자기 꿀팁을 주셨다. 기능자체 보다는 어떻게 사용되는지에 집중해서 설계합시다.
