# 03 클로저
클로저(closer)는 내부함수가 외부함수의 맥락(context)에 접근할 수 있는 것을 가르킨다.  

내부함수와 외부함수에 대하여 알아보자.
내부함수는 외부함수의 지역변수에 접근할 수 있다.  
```javascript
function outter(){    // 외부함수
    function inner(){   // 내부함수
        var title = 'coding everybody';
        alert(title);
    }
    inner();
}

function outter() {
  var inner = function {
    var title = 'coding everybody';
    alert(title);
  }
  inner()
}
```

내부함수는 외부함수의 지역변수에 접근 할 수 있는데 외부함수의 실행이 끝나서 외부함수가 소멸된 이후에도 내부함수가 외부함수의 변수에 접근 할 수 있다.
따라서 내부함수가 소멸되기 전까지 외부함수의 변수는 소멸되지 않는다.
```javascript
function outter(){
    var title = 'coding everybody';  
    return function(){        
        alert(title);
    }
}
inner = outter();
inner();
```

javascript에서 사용하는 private variable을 구현하는 방법은 신기하고 오묘하다.
이 개념은 내부함수가 외부 지역변수에 접근했을 때 내부함수 소멸전까지 존재함을 이용했다.
```javascript
function factory_movie(title){
    return {
        get_title : function (){
            return title;
        },
        set_title : function(_title){
            if(typeof _title === 'String') {
              title = _title
            } else {
              alert("제목은 문자열이어야 합니다.");
            }
    }
}
ghost = factory_movie('Ghost in the shell');
matrix = factory_movie('Matrix');

alert(ghost.get_title());
alert(matrix.get_title());

ghost.set_title('공각기동대');

alert(ghost.get_title());
alert(matrix.get_title());
```

외부함수의 내부함수의 내부함수의 외부함수의 개맨붕
