# 18 - 클로저

<https://opentutorials.org/course/743/6544>

9/23

# 클로저

## 외부함수와 내부함수

클로저(closure)는 내부함수가 외부함수의 맥락(context)에 접근할 수 있는 것을 가르킨다. 클로저는 자바스크립트를 이용한 고난이도 테크닉을 구사하는데 필수적인 개념으로 활용된다.

## 내부함수

--------------------------------------------------------------------------------

자바스크립트는 함수 안에서 또 다른 함수를 선언할 수 있다. 아래의 예제를 보자. 결과는 경고창에 coding everybody가 출력될 것이다.

```javascript
function outter(){
  function inner(){
    var title = 'coding everybody';
    alert(title);
  }
  inner();
}
outter();
```

위의 예제에서 함수 outter의 내부에는 함수 inner가 정의 되어 있다. 함수 inner를 내부 함수라고 한다.

내부함수는 외부함수의 지역변수에 접근할 수 있다. 아래의 예제를 보자. 결과는 coding everybody이다.

```javascript
function outter(){
    var title = 'coding everybody';  
    function inner(){        
        alert(title);
    }
    inner();
}
outter();
```

## 클로저란

클로저(closure)는 내부함수와 밀접한 관계를 가지고 있는 주제다. 내부함수는 외부함수의 지역변수에 접근 할 수 있는데 외부함수의 실행이 끝나서 외부함수가 소멸된 이후에도 내부함수가 외부함수의 변수에 접근 할 수 있다. 이러한 메커니즘을 클로저라고 한다. 아래의 예제는 이전의 예제를 조금 변형한 것이다. 결과는 경고창으로 coding everybody를 출력할 것이다.

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

예제의 실행순서를 주의깊게 살펴보자. 7행에서 함수 ouuter를 호출하고 있다. 그 결과가 변수 inner에 담긴다. 그 결과는 이름이 없는 함수다. 실행이 8행으로 넘어오면 outter 함수는 실행이 끝났기 때문에 이 함수의 지역변수는 소멸되는 것이 자연스럽다. 하지만 8행에서 함수 inner를 실행했을 때 coding everybody가 출력된 것은 외부함수의 지역변수 title이 소멸되지 않았다는 것을 의미한다. 클로저란 내부함수가 외부함수의 지역변수에 접근 할 수 있고, 외부함수는 외부함수의 지역변수를 사용하는 내부함수가 소멸될 때까지 소멸되지 않는 특성을 의미한다.

## private variable

조금 더 복잡한 아래 예제를 살펴보자. 아래 예제는 클로저를 이용해서 영화의 제목을 저장하고 있는 객체를 정의하고 있다. 실행결과는 Ghost in the shell -> Matrix -> 공각기동대 -> Matrix 이다.

```javascript
function factory_movie(title){
  return {
    get_title : function (){
      return title;
    },
    set_title : function(_title){
      title = _title
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

위의 예제를 통해서 알 수 있는 것들을 정리해보면 아래와 같다.

1. 클로저는 객체의 메소드에서도 사용할 수 있다. 위의 예제는 함수의 리턴값으로 객체를 반환하고 있다. 이 객체는 메소드 get_title과 set_title을 가지고 있다. 이 메소드들은 외부함수인 factory_movie의 인자값으로 전달된 지역변수 title을 사용하고 있다.

2. 동일한 외부함수 안에서 만들어진 내부함수나 메소드는 외부함수의 지역변수를 공유한다. 17행에서 실행된 set_title은 외부함수 factory_movie의 지역변수 title의 값을 '공각기동대'로 변경했다. 19행에서 ghost.get_title();의 값이 '공각기동대'인 것은 set_title와 get_title 함수가 title의 값을 공유하고 있다는 의미다.

3. 그런데 똑같은 외부함수 factory_movie를 공유하고 있는 ghost와 matrix의 get_title의 결과는 서로 각각 다르다. 그것은 외부함수가 실행될 때마다 새로운 지역변수를 포함하는 클로저가 생성되기 때문에 ghost와 matrix는 서로 완전히 독립된 객체가 된다.

4. factory_movie의 지역변수 title은 2행에서 정의된 객체의 메소드에서만 접근 할 수 있는 값이다. 이 말은 title의 값을 읽고 수정 할 수 있는 것은 factory_movie 메소드를 통해서 만들어진 객체 뿐이라는 의미다. JavaScript는 기본적으로 Private한 속성을 지원하지 않는데, 클로저의 이러한 특성을 이용해서 Private한 속성을 사용할 수 있게된다.

> 참고: Private 속성은 객체의 외부에서는 접근 할 수 없는 외부에 감춰진 속성이나 메소드를 의미한다. 이를 통해서 객체의 내부에서만 사용해야하는 값이 노출됨으로서 생길 수 있는 오류를 줄일 수 있다. 자바와 같은 언어에서는 이러한 특성을 언어 문법 차원에서 지원하고 있다.

## 클로저의 응용

```javascript
var arr = []
for(var i = 0; i < 5; i++){
  arr[i] function(){
    return i;
  }
}
for(var index in arr){
  console.log(arr[index]());
}
```

함수가 함수 외부의 컨텍스트에 접근할 수 있을 것으로 기대하겠지만 위의 결과는 아래와 같다.

```javascript
5
5
5
5
5
```

위의 코드는 아래와 같이 변경해야 한다.

```javascript
var arr = []
for(var i = 0; i < 5; i++){
  arr[i] = function(id){
    return function(){
      return id;
    }
  }(i);
}
for(var index in arr){
  console.log(arr[index]());
}
```

결과는 아래와 같다.

```javascript
0
1
2
3
4
```

# 클로저 참고

> <https://developer.mozilla.org/ko/docs/JavaScript/Guide/Closures>

> <http://ejohn.org/apps/learn/#48>

> <http://blog.javarouka.me/2012/01/javascripts-closure.html>
