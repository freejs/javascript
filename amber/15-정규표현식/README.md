## 정규표현식
문자열이 있을 때 그 문자열 안에서 어떠한 문자가 있는지 없는지, 또는 어떠한 문자를 치환하던지 이러한 것들을 하게 해주는 강력한 도구.  

정규표현식 또한 JS같은 일종의 언어.  
정규표현식은 JS뿐만 아니라 자바, Perl, 등등 수 많은 언어에서 사용할 수 있다.  
정보를 처리하는 분야에서는 필수적임.  

정규표현식은 두 단계. 컴파일- 실행.  

컴파일 : 대상 찾기. 즉, 패턴 찾기.  
실행 : 찾은 대상에 대해서 어떠한 작업을 구체적으로 하는 것.  

<br>

1. **정규표현식 리터럴**  
패턴 만드는 방법. 패턴 찾는 방법.  
```javascript
var pattern = /a/
```
슬래시 사이에 위치한 a 가 바로 찾고자 하는 대상.  


```javascript
var pattern = new RegExp('a');
```
Regular Expression 의 약자인 RegExp 사용. new를 해서 정규표현식 객체를 만듬. a 라는 문자를 우리는 찾고자 한다.
결국 위 코드와 같은 뜻이다. 찾고자하는 것을 정규표현식 패턴에 저장하는 것.

<br>

2. **정규표현식 메소드 실행**  
어떠한 패턴을 만들면 그 패턴을 만드는 정보를 추출해내는 것. 즉, 추출하는 것, a가 어떠한 정보 안에 존재하는지 안하는지 테스트하는 것, 찾은 정보를 다른 정보로 치환하는 것 이 세가지가 정규표현식을 통해 하는 주요한 작업들이다.

```javascript
var pattern = /a/
```

pattern 이 바로 정규표현식 객체. 이 안에는 패턴이 들어있다.  

```javascript
pattern.exec('abcde');
```

결과

```javascript
["a"]
```

정규 표현식을 실행하는데 우리가 찾고자하는 것은 a이고, a가 있는지 없는지 알수는 없지만 찾으려는 곳은 'abcde'이다. 이 안에 a 가 있으므로 ["a"]를 추출해낸다.  

```javascript
var pattern = /a./;
pattern.exec('abcde');
```

결과

```javascript
["ab"]
```

.은 어떤 문자건 간에 하나의 문자를 말한다. 그래서 ab 가 추출되는 것.  

만약 a 가 포함되지 않은 인자를 전달하면

```javascript
pattern.exec('bcd');
```

결과

```javascript
null
```

a 가 없으므로 null 리턴.

따라서 **exec** 는 패턴이 찾는 정보를 대상에서 찾아서 그것이 있다면 그것을 배열로 리턴하는 함수인 것이다.  
이번에는

```javascript
pattern.test('abcd');
```

결과
```javascript
true
```

따라서 **test** 는 검색의 대상이 되는 첫번째 인자의 정보 안에 우리가 찾고자 하는 패턴이 존재한다면 리턴 값이 불린이기 때문에 true 를 리턴한다. 반대의 경우는 false 리턴.  

- 결국 **exec** 를 사용하는 이유는 추출이다.
- 결국 **test** 를 사용하는 이유는 우리가 찾고자 하는 정보가 있는지 없는지를 테스트하려는 것이다.  

<br>


3. **문자열 메소드 실행**
```javascript
var pattern = /a/;
var str = 'abcdef';
str.match(pattern);
```

결과

```javascript
["a"]
```

우리가 찾고자 하는 a 가 배열로 리턴이 된다.  
만약 대상에 a 가 없다면 null 이 리턴된다.  

```javascript
str.replace(pattern,'A');
```

결과

```javascript
"Abcdef"
```

replace 를 사용함으로써 찾고자했던 a를 찾아서 대문자 A로 바꿔준다.  

<br>


4. **옵션**

**i** 는 정규표현식의 패턴이 대문자와 소문자를 구분하게 하거나 구분하지 않게 할 때 사용하는 옵션이다.

```javascript
var xi = /a/;
"Abcde".match(xi);
```

xi는 i 옵션을 사용하지 않는다는 뜻이다.

결과

```javascript
null
```

```javascript
var oi = /a/i;
"Abcde".match(oi);
```

결과

```javascript
["A"]
```

처음에 소문자 a 를 패턴으로 지정했음에도 대문자 A 를 검출해주고 있다. 즉, 이러 이런 역할을 해주는 옵션이 i 이다.  


**g**

```javascript
var xg = /a/;
"abcdea".match(xg);
```

결과

```javascript
["a"]
```

a 가 두번 있음에도 한번만 검출하고 있다.

```javascript
var og = /a/g;
"abcdea".match(xg);
```

결과

```javascript
["a", "a"]
```

이번에는 a가 두번 나타났다. 문자열에 포함되어 있는 패턴에 포함되는 문자열을 전부 다 배열에 담아서 리턴해준다.

이 패턴들은 같이 사용할 수 있다.

```javascript
var ig = /a/ig;
"AabcdAa".match(ig);
```

이렇게 쓰면 대문자 소문자를 구분하지 않고, 이 패턴에 해당되는 모든 문자를 찾아서 리턴해준다.
결과

```javascript
["A", "a", "A", "a"]
```

<br>

5. **캡처**


`\w` 는 문자를, `\s` 는 공백을 의미한다. 문자 + 공백 + 문자.  
정규표현식 시각화하게 도와주는 도구.  

```javascript
var pattern = /(\w+)\s(\w+)/;
var str = "coding everybody";
var result = str.replace(pattern, "$2, $1");
console.log(result);

```

$2는 패턴에서 두번째 그룹을, $1 은 패턴에서 첫번째 그룹을 의미한다. 또한 공백은 ,공백으로 바뀌었으므로  

결과  

```javascript
everybody, coding
```

그룹을 지정하여 지정된 그룹을 가져와서 사용하는 기능을 캡처라고 한다. 이것을 이용해 치환을 할 수 있다.  

<br>


6. **치환**

나니?
