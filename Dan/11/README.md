# 11 배열
배열(Array)은 원소(element)들의 집합으로 각 원소의 순번은 색인(index)로 구분

### 배열의 생성
```javascript
var member = ['chris', 'amber', 'dan']
```

### 배열의 조작
간단한 예제를 통해 배열을 어떻게 조작하는지 알아본다
```javascript
var arr = [1, 2, 3, 4, 5];
alert(arr.length);    // 5

var li = ['a', 'b', 'c', 'd', 'e'];
li.push('f');
alert(li);    // a, b, c, d, e, f

var li = ['a', 'b', 'c', 'd', 'e'];
li.pop();
alert(li);    // a, b, c, d

var li = ['a', 'b', 'c', 'd', 'e'];
li = li.concat(['f', 'g']);
alert(li);    // a, b, c, d, e, f, g

var li = ['a', 'b', 'c', 'd', 'e'];
li.shift();
alert(li);    // b, c, d, e

var li = ['a', 'b', 'c', 'd', 'e'];
li.unshift('z');
alert(li);    // z, a, b, c, d, e

var li = ['a', 'b', 'c', 'd', 'e'];
li.splice(2, 0, 'B');
alert(li);    // a, b, B, d, e

var li = ['c', 'e', 'a', 'b', 'd'];
li.sort();
alert(li);    // a, b, c, d, e

var li = ['c', 'e', 'a', 'b', 'd'];
li.reverse();
alert(li);    // e, d, c, b, a
```
