---
layout: post
title: "jekyll 포스팅 글 작성해보기 #1"
image: '/assets/img/'
description:
main-class: 'misc'
color: '#2DA0C3'
tags: 
- jekyll
- getting start
categories: jekyll
introduction: '코드 하이라이팅'
---

## 코드 하이라이팅
개발 블로그다 보니 아무래도 포스팅 글에서 주로 소스에 대한 내용을 올릴 일이 많기 때문에 코드 하이라이팅부터 알아보기로 했다. 

저자가 사용한 테마의 경우 코드 하이라이팅 모듈로 rouge를 사용한다고
_config.yml에 설정되어 있다. 


```
# Build settings
markdown: kramdown
highlighter: rouge
permalink: /:title/
```
rouge라니! 뭔가 거실을 아름답게 꾸며줄 것 같은 느낌의 이 모듈은 rouge 홈페이지에서 다음과 같이 소개하고 있다. 

> 순수한 루비로 작성된 엘레강스하고 확장가능한 코드 하이라이터 모듈이다. 


[rouge홈페이지](http://rouge.jneen.net/)로 접속하여 사용가능한 코드 종류 및 테스트를 진행해 볼 수 있다. 


사용법은 정말 간단하다. 포스팅 작성 중 다음과 같은 liquid구문을 사용해서 제어할 수 있다. 
```
{% raw %}
{% highlight ruby %}`

{% endhighlight %}`
{% endraw %}
```
- highlight ruby라고 적혀있는 부분의 ruby 대신에 bash, c++, javascript, java, php, python등 다양한 언어의 하이라이팅이 가능하다. 

**TIP**
liquid tag에 대한 기술 하고 싶을때 escape과정이 필요하다. raw와 endraw 구문을 사용하면 해당 문제를 해결 할 수 있다. [liquid tag escape](https://stackoverflow.com/questions/3426182/how-to-escape-liquid-template-tags)

## c++ 예제

highlight할 언어로 c++을 적어준 후 liquid구문 사이에 하이라이팅할 소스 구문을 적어보자. 진부하지만 고전적인 hello world 예제를 작성해보았다.

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

칙칙한 코드가 아름답게 하이라이팅 된 것을 확인할 수 있다.
