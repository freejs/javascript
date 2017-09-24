# 07 비교

### 대입 연산자
좌항의 변수에 우항의 값을 대입하는 연산자
```javascript
a = 1;
```

### 비교 연산자
좌항과 우항의 값을 비교
```javascript
alert(1 > 2);
alert(1 < 2);
alert(1 >= 2);
alert(1 <= 2);
```

### 동등 연산자 (equal operator)
좌항과 우항 값이 같은지 따라 결과를 true 또는 false로 표현
```javascript
alert(1 == 1);    // true
alert(1 == "1");  // true
```

### 엄격한 동등 연산자 (strict equal operator)
좌항과 우항 값이 자료형과 값이 같은지에 따라 결과를 true 또는 false로 표현
```javascript
alert(1 === 1);    // true
alert(1 === "1");  // false
```

### 자료형 참고
```javascript
Boolean   true/false
Number    - ~ +       // 숫자 전체
String    "abs"       // 큰 따옴표(")로 묶인 문자의 집합
undefined undefined
null      null
```

### 예시
```javascript
alert(null == undefined);   // true
alert(null === undefined);  // false

alert(true == 1);           // true
alert(true === 1);          // false
alert(true == "1");         // true
alert(true === "1");        // false

alert(0 === -0);            // true
alert(NaN === NaN);         // false, 이 부분이 조금 특별
```

### 부정
참과 거짓 값의 부정을 의미
```javascript
alert(1 != 2);      // true
alert(1 != 1);      // false
alert(1 != "1");    // false

alert(1 !== 2);     // true
alert(1 !== 1);     // false
alert(1 !== "1");   // true
```
