# 12 객체
배열을 선언시 인덱스로 문자를 사용하고 싶다면 객체(dictionary)를 사용해야 한다.  
다른 언어에서 사용되는 연관배열(associative array) 또는 맵( map), 딕셔너리(Dictionary)라는 데이터 타입이 객체에 해당한다.

### 객체의 생성
```javascript
var grades = {'egoing': 10, 'k8805': 6, 'sorialgi': 80};

var grades = {};
grades['egoing'] = 10;
grades['k8805'] = 6;
grades['sorialgi'] = 80;

var grades = new Object();
grades['egoing'] = 10;
grades['k8805'] = 6;
grades['sorialgi'] = 80;

alert(grades['sorialgi']);
alert(grades.sorialgi);
```

### 객체의 사용 예제
```javascript
var grades = {'egoing': 10, 'k8805': 6, 'sorialgi': 80};
for(key in grades) {
    document.write("key : "+key+" value : "+grades[key]+"<br />");
}

var grades = {
    'list': {'egoing': 10, 'k8805': 6, 'sorialgi': 80},
    'show' : function(){
        for(var name in this.list){
            document.write(name+':'+this.list[name]+"<br />");
        }
    }
};
grades.show();
```
