## 배열
```
var li = ['a', 'b', 'c', 'd', 'e'];
li.push('f');
li = li.concat(['f', 'g']);
li.unshift('z');
li.splice(2, 0, 'B');
```
- `push`ㅡ 새로운 element (한 개) 맨 마지막 index에 추가.  
- `concat`ㅡ 새로운 element (여러 개) 맨 마지막 index에 추가. 거의 이어 붙이기.  
- `unshift`ㅡ 새로운 element 맨 앞에 추가.  
- `splice`ㅡ (해당 index에서 부터, 제거할 element수, 그리고 추가할 element)  
<br>
