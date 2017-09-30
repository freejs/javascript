# 09 데이터 타입
다른 접근!! ?? 이해가 안댕

### 원시 데이터 타입
우끼! 우끼! 영어로 알아보자. Primitive type(프리미티브 타입)
```
숫자  -> Number     레퍼 객체
문자열 -> String     레퍼 객체
불리언 -> Boolean    레퍼 객체
null -> X
undefined ->
```

### 레퍼 객체
레레레레퍼퍼퍼 객체!! 아래! 코드! 르을! 살펴! 보자!

'.'의 이름을 처음알았어...... Object Access Operator

내부적으로 순식간에 객체를 생성해서 함수를 실행시키고 바로 삭제!
```javascript
var str = 'coding';
console.log(str.length);    // 6
console.log(str.charAt(0)); // 'c'
```

따라서 아래와 같은 코드를 실행할경우 이상한 결과를 얻게 된다.
```javascript
var str = 'coding';
str.prop = 'everybody';
console.log(str.prop);    // undefined
```

자동으로 객체화 시켜서 처리하고 삭제!! 시키는 원시 데이터들...
하지만 이러한 원시 데이터들을 객체로 사용하도록 하는 레퍼 클래스 들이 존재한당!! 언더 스탄드??
