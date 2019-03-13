---
layout: post
title: "객체 지향 javascript와 object 생성"
image: '/assets/img/'
main-class: 'js'
tag:
- javascript
- oop 
- constructor
categories: javascript
introduction: 자바스크립트 객체 생성 요약
---

## 객체 생성 요약
- 참고: [MDN Object-oriented JavaScript for beginners
](https://developer.mozilla.org/ko/docs/Learn/JavaScript/Objects/Object-oriented_JS)



입문자를 위한 자바스크립트 객체 지향 문서에 객체지향 관련 설명은 너무 잘되어 있어서 [링크](https://developer.mozilla.org/ko/docs/Learn/JavaScript/Objects/Object-oriented_JS#%EA%B0%9D%EC%B2%B4%EC%A7%80%ED%96%A5_%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D_%E2%80%94_%EA%B8%B0%EC%B4%88)로 대신합니다. 


객체를 생성하려할 때 사용할 수 있는 방법으로 앞서 살펴본 객체 리터럴을 사용하는 방법이 하나 있습니다.. 하지만 여러개의 객체를 생성해야할 때 이 객체 리터럴들을 모두 채워넣은 후 사용해야한다면 여간 불편한 일이 아닐 수 없습니다. 게다가 중복된 내용들을 고스란히 채워넣어야하는 부분도 불편한 일입니다. 

객체를 생성하기 위한 함수를 사용한다면 어떨까요? 아마 다음과 같은 형태가 될 것 입니다. 

{% highlight javascript %}
// 객체 생성을 위한 함수
function createNewPefunction createNewPerson(name) {
  var obj = {};
  obj.name = name; 
  obj.greeting =  function() {
    alert('Hi! I am '+this.name+'.');
  };
  return obj;
}

var salva = createNewPerson('Salva');
salva.name;
salva.greeting();

var tom = createNewPerson('Tom');
tom.name;
tom.greeting();
{% endhighlight %}

{% highlight javascript %}
// 생성자 함수 사용
function Person(name) {
  this.name = name; 
  this.greeting = function() {
    alert('Hi! I am '+ this.name + '.');
  };
}

var person1 = new Person('Bob');
var person2 = new Person('Sarah');

person1.name;
person1.greeting();
person2.name;
person2.greeting();


{% endhighlight %}