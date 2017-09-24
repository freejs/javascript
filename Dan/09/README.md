# 09 반복문
어디에서나 볼 수있는 흔한 반복문
```javascript
while(true) {
  document.write('coding everybody <br />');
}

for(var i = 0; i < 10; i++){
    document.write('coding everybody'+i+'<br />');
}

for(var i = 0; i < 10; i++){
    if(i === 5) {
        break;
    }
    document.write('coding everybody'+i+'<br />');
}

for(var i = 0; i < 10; i++){
    if(i === 5) {
        continue;
    }
    document.write('coding everybody'+i+'<br />');
}
```
