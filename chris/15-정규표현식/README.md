# 15 - 정규표현식

https://opentutorials.org/course/743/6580

9/23

# 컴파일

## 정규표현식 만드는 방법

### 1. 리터럴

> var pattern = /a/;

### 2. 객체 생성자

> var pattern = new RegExp('a');


# 정규표현식 메소드 실행

## 객체를 만든 후 문자열에서 원하는 문자를 찾는 법

### RegExp.exec()

> console.log(pattern.exec('abcdef'));

["a"]

> console.log(pattern.exec('bcdefg'));

null

### RegExp.test()

> console.log(pattern.test('abcdef'));

true

> console.log(pattern.test('bcdefg'));

false


# 문자열 메소드 실행

## 문자열 객체의 몇몇 메소드는 정규표현식을 사용할 수 있다.

### String.match()

> console.log('abcdef'.match(pattern));

["a"]

> console.log('bcdefg'.match(pattern));

null

### String.replace()

> console.log('abcdef'.replace(pattern, 'A'));

abcdef


# 옵션

## 정규표현식 패턴을 만들 때 옵션을 설정할 수 있다.

### i

i를 붙이면 대소문자를 구분하지 않는다.

> var xi = /a/;

> console.log('Abcde'.match(xi));

null

> var oi = /a/i;

> console.log('Abcde'.match(oi));

['A']

### g

g를 붙이면 검색된 모든 결과를 리턴한다.

> var xg = /a/;

> console.log('abcdea'.match(xg));

['a']

> var og = /a/g;

> console.log('abcdea'.match(og));

['a', 'a']

같이 사용도 가능

> var ig = /a/ig;

> console.log('AabcdAa'.match(ig));

['A', 'a', 'A', 'a']


# 사례

## 캡처

괄호안의 패턴은 마치 변수처럼 재사용 할 수 있다. 이 때 기호 $를 사용하는데 아래 코드는 coding과 everybody의 순서를 역전시킨다.

> var pattern = /(\w+)\s(\w+)/;

> var str = "coding everybody";

> var result = str.replace(pattern, '$2, $1');

> console.log(result);


## 치환

아래 코드는 본문 중의 URL을 링크 html 태그로 교체한다.

> var urlPattern = /\b(?:https?):/\/\[a-z0-9-+&@#/\%?=-|!/gim;

> content = '생활코딩 : http://opentutorials.org/course/1 입니다. 네이버 : http://naver.com 입니다. ';

> var result = content.replace(urlPattern, function(url){
  return '<a href="'+url+'">'+url+'</a>';
});

> console.log(result);
