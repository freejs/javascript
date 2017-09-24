# 08 조건문
어디에서나 볼 수있는 흔한 조건문
```javascript
if(false) {
  alert(1);
} else if(true) {
  alert(2);
} else {
  alert(3);
}
```

### 기타 false로 간주되는 데이터 형
이 부분이 좀 신기함
```javascript
if(!0) {
  alert('0 입니다.')
}
if(1) {
  alert('1 입니다.')
}
if(!''){
  alert('빈 문자열')
}
if(!undefined){
  alert('undefined');
}
var a;
if(!a){
  alert('값이 할당되지 않은 변수');
}
if(!null){
  alert('null');
}
if(!NaN){
  alert('NaN');
}
```
