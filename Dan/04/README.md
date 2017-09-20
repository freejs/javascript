# 04 변수
문자나 숫자를 담을 수 있는 그릇으로서 변할 수 있는 값이다.  
var이라는 키워드를 이용해서 변수를 선언한다.  
var을 생략하여 변수를 선언할 수 있지만 이것은 유효범위라는 것에 영향을 미친다.  
(따라서 명확하게 사용하는 것이 중요하다.)  

```Javascript
    var a = 1;
    alert(a + 1);                 // 2,
    var first = "coding";
    alert(first + " everybody");  // coding everybody,
```

### 변수를 왜 사용하는가?
결론 : 코드의 재활용성을 높여준다. -> 유지보수에 용이  

##### 변수를 사용하지 않을 때
```Javascript
    alert(100+10);
    alert((100+10)/10);
    alert(((100+10)/10)-10);
    alert((((100+10)/10)-10)*10);
```
##### 변수를 사용할 때
```Javascript
    var a = 100;
    a = a + 10;
    alert(a);       // 110,
    a = a / 10;
    alert(a);       // 11,
    a = a - 10;
    alert(a);       // 1,
    a = a * 10;
    alert(a);       // 10,
```
