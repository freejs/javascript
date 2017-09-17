## 배열
```
var li = ['a', 'b', 'c', 'd', 'e'];
li.push('f');
li = li.concat(['f', 'g']);
li.unshift('z');
li.splice(2, 0, 'B');
```
- `push`ㅡ element (한 개) 맨 마지막 index에 추가.
- `concat`ㅡ element (여러 개) 맨 마지막 index에 추가. 거의 이어 붙이기.
- `unshift`ㅡ element 맨 앞에 추가.
- `splice`ㅡ (해당 index에서 부터, 제거할 element수, 그리고 추가할 element);
