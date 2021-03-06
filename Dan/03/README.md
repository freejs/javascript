# 03 숫자와 문자
자바스크립트에는 숫자(number)와 문자(string)이라는 두개의 변수형이 존재한다.

### 숫자
자바스크립트에서는 정수와 실수의 구분없이 포괄적으로 숫자(number)라고 사용한다.
숫자는 큰따옴표나 작은따옴표가 붙지 않는 숫자를 숫자로 인식한다.

#### 사칙연산

```Javascript
    alert(1 + 3); // 더하기
    alert(3 - 2); // 빼기
    alert(2 / 2); // 나누기
    alert(4 * 1); // 곱셈
```

#### Math를 이용한 복잡한 연산
Math는 수학과 관련된 명령들의 카테고리이다.

```Javascript
    Math.pow(3, 2);       // 9, 3의 2승
    Math.round(10.6);     // 11, 10.6을 반올림
    Math.ceil(10.2);      // 11, 10.2를 올림
    Math.floor(10.6);     // 10, 10.6을 내림
    Math.sqrt(9);         // 3, 3의 제곱근
    Math.random();        // 0부터 1.0 사이의 랜덤한 숫자
```

### 문자
문자는 큰따옴표 또는 작은따옴표 사이에 넣어야 한다.
자바스크립트를 해석하는 브라우저에게 큰(작은)따옴표가 나온 이후에 다시 큰(작은)따옴표가 다시 나올때까지의 입력을 문자로 입력받는다.  
역슬래쉬를 이용하여 특수 문자('나 " 같은 녀석들)들을 문자로서 역활을 수행시키는 것을 escape라고 한다.

```Javascript
    alert('FreeJs\'s javascript') // 역슬래쉬를 사용하여 문자열에 " 또는 '를 삽입
```

<hr/>

#### 데이터의 형식
약속된 typeof 함수를 이용하여 주어진 변수의 타입을 알 수 있다.

```Javascript
    alert(typeof "1")   // "string"
    alert(typeof 1)     // number
```

#### 약속된 표현
```Javascript
    alert("FreeJS\n everybody")     // \n은 줄바꿈을 의미
    alert("FreeJS" + "everybody")   // +는 문자열의 결합을 의미    
```

#### 형에 따른 + 연산자의 사용
```Javascript
    alert(1 + 1)        // 2, 숫자의 연산
    alert("1" + "1")    // 11, 문자의 연산
```

<hr/>
추가 적으로 필요한 함수들은 직접 API문서를 찾아보면서 사용하면 된다.
