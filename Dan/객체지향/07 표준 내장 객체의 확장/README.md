# 07 표준 내장 객체의 확장
뚠뚠~ 공부하기 귀찮은걸

표준 내장 객체라는건 기본적으로 제공해주는 객체들을 의미한다!!
무려 9개나 있다.
```
Object
Function
Array
String
Boolean
Number
Math
Date
RegExp
```

자자 그럼 내장 객체를 확장하는 방법에 대해 알아보자.
자자자자자 일단 이 소스 먼저 보자.
```javascript
var arr = new Array('seoul','new york','ladarkh','pusan', 'Tsukuba');
function getRandomValueFromArray(haystack){
    var index = Math.floor(haystack.length*Math.random());
    return haystack[index];
}
console.log(getRandomValueFromArray(arr));
```

이 소스가 마법처럼 바뀔것이당!!
```javascript
Array.prototype.random =  function() {
  var index = Math.floor(this.length*Math.random());
  return [index];
}
var arr = new Array('seoul','new york','ladarkh','pusan', 'Tsukuba');
console.log(arr.random());
```

코드의 가독성을 높여준다.
인자값이 없으므로 사용자가 신경을 덜써도 되니까 좋음.

너무 놀라지 말자.

이건 생각보다 재밌게 쓰일것 같다.
