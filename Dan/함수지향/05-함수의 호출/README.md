# 05 함수의 호출
apply와  call에 대해 알아보고 싶지만 apply에 대해서만 알려준다.
this는 함수 호출시에 결정된다!!
```javascript
o1 = {val1:1, val2:2, val3:3}
o2 = {v1:10, v2:50, v3:100, v4:25}
function sum(){
    var _sum = 0;
    for(name in this){
        _sum += this[name];
    }
    return _sum;
}
alert(sum.apply(o1)) // 6
alert(sum.apply(o2)) // 185
```
