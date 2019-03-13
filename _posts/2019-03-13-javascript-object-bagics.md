---
layout: post
title: "2019-03-13 javascript object basic"
image: '/assets/img/'
main-class: 'js'
tags:
- javascript
- object
categories: javascript
introduction: 자바스크립트 객체 기본 요약
---

## 객체 기본 요약
- 참고: [MDN javascript Object Bagics](https://developer.mozilla.org/ko/docs/Learn/JavaScript/Objects/Basics)
- javascript 객체는 메소드와 프로퍼티로 구성됩니다.

{% highlight javascript %}
var person = {
  name: ['Bob', 'Smith'],
  age: 32,
  gender: 'male',
  interests: ['music', 'skiing'],
  bio: function() {
    alert(this.name[0] + ' ' + this.name[1] + ' is ' + this.age + ' years old. He likes ' + this.interests[0] + ' and ' + this.interests[1] + '.');
  },
  greeting: function() {
    alert('Hi! I\'m ' + this.name[0] + '.');
  }
};
{% endhighlight %}
- method: person객체의 마지막 2개에 해당하는 함수를 메소드라고 합니다. 메소드는 데이터를 가지고 뭔가 일을 할 수 있게 해줍니다.
- property: person객체에서 처음 4개에 해당하는 문자열, 숫자 , 배열등의 데이터를 프로퍼티(속성)이라고 합니다.
- 위와 같은 형태를 [object literal](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Object_initializer)이라고 합니다.

### 하위 namespace 접근법
#### 점 표기법
객체의 프로퍼티와 메소드는 점 표기법으로 접근할 수 있습닏. 
객체 이름은 네임스페이스처럼 동작합니다. 객체 내 캡슐화되어 있는 것에 접근하려면 점을 찍고 접근하고자 하는 하위 항목을 입력합니다. 
간단한 프로퍼티 이름일 수도 있고, 배열의 일부이거나 객체 내 메소드를 호출할 수도 있습니다. 
{% highlight javascript %}
person.age
person.interests[1]
person.bio()
{% endhighlight %}
#### 괄호 표기법

{% highlight javascript %}
person['age']
person['name']['first']
{% endhighlight %}
객체 프로퍼티에 접근하는 방법으로 괄호를 이용하는 방법입니다. 
배열 속의 항목을 가져오는 형태와 유사한데 인덱스로 숫자 대신 이름을 사용하는 형태로 '연관배열(associate arryas)'로 불리기도 합니다. 

괄호 표기법은 점 표기법과 달리 동적인 이름으로 프로퍼티를 생성할 수 있습니다. (점 표기법은 정적인 이름으로만 프로퍼티를 생성할 수 있습니다.)

{% highlight javascript %}
var person = {};
var myDataName = 'height';
var myDataValue = '1.75m';
person[myDataName] = myDataValue;
person[myDataName] = myDataValue; // OK, person.height

person = {}; // reset
person.myDataName = myDataValue; // Not Ok, person.height이 생성되지 않고 myDataName이름으로 추가됩니다.
{% endhighlight %}


### this란 무엇인가?

{% highlight javascript %}
greeting: function() {
  alert('Hi! I\'m ' + this.name.first + '.');
}
{% endhighlight %}

this키워드는 지금 동작하고 있는 코드를 가지고 있는 객체를 가리킵니다. 객체 지향에서 생성자를 사용할 때 매우 유용하게 사용됩니다. 

### 객체는 줄곧 사용해 왔습니다. 

아래와 같이 DOM에 접근할때 

{% highlight javascript %}
var myDiv = document.createElement('div');
var myVideo = document.querySelector('video');
{% endhighlight %}

Document 클래스의 인스턴스를 점 표기법으로 접근하여 메소드를 사용하고 있습니다. 
다른 내장 객체들/API(Array, Math, String 등등)도 마찬가지입니다.

