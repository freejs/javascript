## 비교
```
alert(1=='1');              //true
alert(1==='1');             //false
```

두 연산자의 차이는 데이터타입 비교하는지 안하는지.  
프로그램을 짤 때 비교를 할 때 === 를 꼭 쓸 것.  

null : 프로그래머가 의도한 값이 없는 상황.  
undifined : 프로그래머가 의도하지 않고 값이 없는 상황.  
NaN : 성립하지 않는 수. 계산할 수 없음. ex) 0/0 = NaN  
```
alert(null == undefined);       //true
alert(null === undefined);      //false
alert(true == 1);               //true
alert(true === 1);              //false
alert(true == '1');             //true
alert(true === '1');            //false

alert(0 === -0);                //true
alert(NaN === NaN);             //false
```
`==` 숫자 1 만을 true 로 간주. 나머지 숫자들은 false.  
`===` 숫자 1 도 false.  
