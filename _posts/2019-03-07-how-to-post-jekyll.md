---
layout: post
title: "jekyll 포스팅 시작하기 #1"
image: '/assets/img/'
description:
main-class: 'misc'
color: '#2DA0C3'
tags:
- jekyll
- tutorial
categories: jekyll
introduction: '코드 하이라이팅'
---

## 코드 하이라이팅
기술 블로그를 운영하다 보면 소스 코드에 대한 내용을 작성할 일이 많습니다. 소스 코드의 가독성을 높이기 위해 jekyll에서 제공하는 코드 하이라이팅 을 살펴 봅시다.

jekyll에서는 코드 하이라이팅 모듈로 rouge를 많이 사용합니다.  
rouge라니 뭔가 거실을 아름답게 꾸며줄 것 같은 느낌이 드네요. rouge 홈페이지에서 다음과 같이 소개하고 있습니다.

> 순수한 루비로 작성된 엘레강스하고 확장가능한 코드 하이라이터이다.

> 'An elegant, extendable code highlighter written in pure Ruby.'


[rouge 홈페이지](http://rouge.jneen.net/)에서 코드 하이라이팅 가능한 언어에 대한 안내와 테스트 해볼 수 있는 페이지가 제공됩니다.


사용법은 정말 간단합니다. 포스팅 작성 중 다음과 같은 liquid구문을 사용하여 코드 하이라이팅을 할 수 있습니다.  
```
{% raw %}
{% highlight ruby %}`

{% endhighlight %}`
{% endraw %}
```
- highlight ruby라고 적혀있는 부분의 ruby 대신에 bash, c++, javascript, java, php, python등 하이라이팅 하고자 하는 언어를 넣어주면 해당 언어들을 코드 하이라이팅 해줍니다.  

**TIP**
jekyll은 liquid를 이용하여 정적 페이지를 생성합니다. 그럼 liquid 구문을 포함한 소스코드를 블로그 포스팅에 포함하고 싶을때는 어떻게 해야할까요? liquid 구문을 포스틩 내용 중 표시하고 싶을 때는 해석되지 않도록 escape과정이 필요합니다. raw와 endraw 구문을 사용하면 간단히 문제를 해결 할 수 있습니다. 자세한 내용은 다음 페이지를 확인해주세요. [liquid tag escape](https://stackoverflow.com/questions/3426182/how-to-escape-liquid-template-tags)

## c++ 예제

저는 첫 샘플 예제로 c++ 코드 하이라이팅 기능을 포함한 포스팅을 작성하려고 합니다.
먼저 highlight할 언어로 c++을 적어준 후 liquid구문 사이에 하이라이팅할 코드를 적습니다. 저는 getting start 단골메뉴인 hello world 예제를 작성해보겠습니다.

```
{% raw %}
{% highlight c++ %}
#include <iostream>
using namespace std;
int main()
{
	cout << "hello rouge highlighter" << endl;
	return 0;
}
{% endhighlight %}
{% endraw %}
```

{% highlight c++ %}
#include <iostream>
using namespace std;
int main()
{
	cout << "hello rouge highlight world" << endl;
	return 0;
}
{% endhighlight %}

코드가 한결 아름답고 가독성이 좋아졌습니다.
