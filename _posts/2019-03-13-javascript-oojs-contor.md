---
layout: post
title: "객체 지향 javascript와 object 생성"
image: '/assets/img/'
main-class: 'js'
tag:
- javascript
- oop 
- constructor
- prototype
categories: javascript
introduction: 자바스크립트 객체 생성 요약
---

## 객체 생성 요약
- 참고: [MDN Object-oriented JavaScript for beginners
](https://developer.mozilla.org/ko/docs/Learn/JavaScript/Objects/Object-oriented_JS)
- 참고: [MDN Object Prototypes](https://developer.mozilla.org/ko/docs/Learn/JavaScript/Objects/Object_prototypes)



입문자를 위한 자바스크립트 객체 지향 문서에 객체지향 관련 설명은 충분히 잘되어 있어서 [링크](https://developer.mozilla.org/ko/docs/Learn/JavaScript/Objects/Object-oriented_JS#%EA%B0%9D%EC%B2%B4%EC%A7%80%ED%96%A5_%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D_%E2%80%94_%EA%B8%B0%EC%B4%88)로 대신합니다. 


객체를 생성하려할 때 사용할 수 있는 방법 중 하나로 앞서 살펴본 객체 리터럴을 사용하는 방법이 있습니다. 하지만 여러개의 객체를 생성해야할 때 반복적으로 객체 리터럴들을 모두 채워넣은 후 사용해야한다면 여간 불편한 일이 아닐 수 없습니다.
심지어 중복되는 부분들도 포함해서 말입니다. 

중복된 부분들은 자동으로 채워 넣어주는 객체를 생성하기 위한 함수를 만들어 사용한다면 어떨까요? 아마 다음과 같은 형태가 될 것 입니다. 

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

위 함수에서는 빈 객체를 생성 한후 리턴하여 프로퍼티와 메소드를 할당하고 있습니다.
자바스크립트는 객체를 생성하는 다른 방법으로 생성자 함수 형태를 제공하고 있습니다. 

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
빈 객체를 생성하고 리턴하는 구문등이 없어 상대적으로 더 깔끔하게 표현됩니다.

생성자 내에서 this 키워드를 사용하여 객체 내 할당을 진행하여 메소드와 프로퍼티를 만들고 있습니다. 
- 관습적으로 생성자 함수명은 대문자로 시작합니다. 

또한 new 키워드를 사용하여 브라우저에게 새로운 객체를 만들려 한다는 것을 알려줍니다. 

새 객체가 생성된 이후 person1, person2 변수는 다음과 같은 객체들을 가지게 됩니다. 

{% highlight javascript %}
{
  name: 'Bob',
  greeting: function() {
    alert('Hi! I\'m ' + this.name + '.');
  }
}

{
  name: 'Sarah',
  greeting: function() {
    alert('Hi! I\'m ' + this.name + '.');
  }
}
{% endhighlight %}

greeting 함수의 경우 동일한 내용임에도 불구하고 생성자 함수를 호출할 때마다 매번 다시 정의하는 것으로 보입니다. 이를 피하기 위해 prototype에 함수를 정의합니다. 

### prototype 기반 언어?

javascript는 흔히 Prototyppe-based language로 불립니다. 
모든 객체들은 메소드와 속성들을 상속 받기 위한 템플릿으로 프로토타입 객체를(prototype object)를 가지기 때문입니다. 

프로토 타입객체도 또 다시 상위 프로토타입 객체로부터 메소드와 속성을 상속 받을 수도 있고 그 상위의 프로토타입 객체도 마찬가지 입니다. 이것을 프로토타입 체인(prototype chain)이라고 합니다. 

보다 엄밀히 말하자면 상속되는 속성과 메소드들은 각 객체가 아니라. 객체의 생성자의 prototype이라는 속성에 정의되어 있습니다. 

javascript에서는 객체 인스턴스와 프로토타입이 연결되어(일반적으로 생성자 속성의 prototype속성의 __proto__을 사용하고 있습니다.) 있으며 이 연결을 따라 프로토타입 체인을 타고 올라가며 속성과 메소드를 탐색하게 됩니다. 
```
여기에서 객체의 prototype 속성과 생성자의 prototype 속성이 다르다는 것을 인지하는게 중요합니다. 전자의 경우 객체의 prototype 속성은 개별 객체 속성이며, 후자는 생성자의 속성입니다.
```
일반적으로 수학 연산에서 자주 사용되는 Math객체의 프로토타입을 확인해보겠습니다. 

{% highlight javascript %}
// Math Object
Math
​
E: 2.718281828459045
​LN10: 2.302585092994046
​LN2: 0.6931471805599453
​LOG10E: 0.4342944819032518
​LOG2E: 1.4426950408889634
​PI: 3.141592653589793
​SQRT1_2: 0.7071067811865476
​SQRT2: 1.4142135623730951
​abs: function abs()

...
​
<prototype>: {…}
​​__defineGetter__: function __defineGetter__()
​​__defineSetter__: function __defineSetter__()
​​__lookupGetter__: function __lookupGetter__()
​​__lookupSetter__: function __lookupSetter__()
​​__proto__: {…}
​​​
	__defineGetter__: function __defineGetter__()
	__defineSetter__: function __defineSetter__()
​​	__lookupGetter__: function __lookupGetter__()
​​​	__lookupSetter__: function __lookupSetter__()
​​​	__proto__: null
​​​	constructor: function Object()
​​​	hasOwnProperty: function hasOwnProperty()
​​​	isPrototypeOf: function isPrototypeOf()
​​​	propertyIsEnumerable: function propertyIsEnumerable()
​​​	toLocaleString: function toLocaleString()
​​​	toSource: function toSource()
​​​	toString: function toString()
​​​	valueOf: function valueOf()
​​​	<get __proto__()>: function __proto__()
​​​	<set __proto__()>: function __proto__()
​​constructor: function Object()
​hasOwnProperty: function hasOwnProperty()
​​isPrototypeOf: function isPrototypeOf()
​​propertyIsEnumerable: function propertyIsEnumerable()
​​toLocaleString: function toLocaleString()
​​toSource: function toSource()
​​toString: function toString()
​​valueOf: function valueOf()
​​<get __proto__()>: function __proto__()
​​<set __proto__()>: function __proto__()
{% endhighlight %}

Math객체의 prototype속성 중 __proto__ 속성으로 프로토타입 객체인 Object를 연결하고 있습니다. 

이번엔 생성자를 사용한 예제에서 사용했던 Person 생성자 함수를 통해서 프로토타입 체인에 대해서 더 살펴봅시다. 

{% highlight javascript %}
function Person(first, last, age, gender, interests) {
  this.name = {
    'first': first,
    'last' : last
  };
  this.age = age;
  this.gender = gender;
  this.interests = interests;
  this.bio = function() {
    alert(this.name.first + ' ' + this.name.last + ' is ' + this.age + ' years old. He likes ' + this.interests[0] + ' and ' + this.interests[1] + '.');
  };
  this.greeting = function() {
    alert('Hi! I\'m ' + this.name.first + '.');
  };
}
{% endhighlight %}

콘솔창에서 아래 코드를 입력하여 인스턴스 하나를 생성해봅시다.

{% highlight javascript %}
var person1 = new Person('Bob', 'Smith', 32, 'male', ['music', 'skiing']);
{% endhighlight%}

콘솔창에서 "person1."을 치게되면 브라우저에서 객체 멤버들을 자동완성 팝업으로 추천해줍니다.
생성자의 프로토타입 객체인 Person()에서 기술하지 않았던 프로퍼티들인 watch, valueOf와 같은Person()의 프로퍼티 객체인 Object에 정의된 다른 멤버들도 함께 보여지게 됩니다.
이것으로 우리는 프로토타입 체인이 동작한다는 것을 알 수 있습니다. 

실제로 Object에 정의되어 있는 valueOf 메소드를 person1에서 호출해 보겠습니다. 

{% highlight javascript %}
person1.valueOf();
{% endhighlight %}

위 메소드를 호출할 경우 먼저  person1객체에서 valueOf() 메소드를 가지고 있는지 체크합니다. 
없으므로 person1의 프로토타입 객체인 Person() 생성자의 프로토 타입에 valueOf() 메소드가 있는지 체크합니다. 
없으므로 Person() 생성자의 프로토 타입 객체의 프로토타입 객체인 Object() 생성자의 프로토타입의 valueOf()메소드가 있는지 체크하게 되고 있으니 호출하며 끝나게 됩니다. 

**NOTE**
- 프로토타입 체인에서 객체의 메소드와 속성이 복사되는 것이 아니라. 체인을 통해 거슬러 올라가며 탐색하는 구조입니다. 
- 특정 객체의 프로토타입 객체로 바로 접근하는 공식적인 방법은 없습니다. - javascript 언어 표준 스펙에서는 프로토 타입 객체에 대한 링크는 내부 속성으로 정의되어 있습니다. 하지만 많은 수의 모던 브라우저들이 __proto__속성을 통해 특정 객체의 프로토타입 객체에 접근할 수 있도록 구현되어 있는 상태입니다. 
ECMAScript2015부터는 Object.getPrototypeOf(obj) 함수를 통해 객체의 프로토타입 객체에 바로 접근할 수 있게 되었습니다. 



