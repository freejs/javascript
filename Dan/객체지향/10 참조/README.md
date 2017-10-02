# 10 참조
중요한 키워드는 복제와 참조

### 복제
그렇군요... 복제라는 것은 call by value군요... 값만을 복사 하기 때문에 원본의 값은 변하지 않습니다.
원시 데이터들은 복제를 하게 됩니다.
```javascript
var a = 1;
var b = a;
b = 2;
console.log(a);     // 1
```

### 참조
그렇다면 이건 call by reference라고 할 수 있겠어요.
원시데이터가 아닌 것들은 모두 참조를 하게 됩니다.
```javascript
var a = {'id': 1};
var b = a;
b.id = 2;
console.log(a.id);     // 2
```

이런 문제 때문에 함수에서 문제가 좀 발생합니다.

### 함수에서 참조때문에 겪는 곤란함...
흠..? 이건 예제보면 바로 이해가 될듯 그냥 보고 느껴라.

인자 값으로 원시 데이터 할당도 원시 데이터
```javascript
var a = 1;
function func(b){
    b = 2;
}
func(a);
console.log(a); // 1
```

인자 값으로 객체 할당은 새로운 객체
```javascript
var a = {'id':1};
function func(b){
    b = {'id':2};
}
func(a);
console.log(a.id);  // 1
```

인자 값으로 객체 할당은 기존 객체에
```javascript
var a = {'id':1};
function func(b){
    b.id = 2;
}
func(a);
console.log(a.id);  // 2
```
