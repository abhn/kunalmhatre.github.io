---
title: "JavaScript - A comedian for beginners"
layout: post
date: 2018-06-02
headerImage: false
tag:
- JAVASCRIPT
category: blog
author: kunalmhatre
description: Article showing off how JavaScript is funny when it comes to learning the basics. 
---

I always used to be serious while learning programming languages, but that did not happen with JavaScript, especially when I was learning the basics. Before I write about some amusing things about JavaScript, let me throw some light on the versatility of the JavaScript. 

When it comes to web development, JavaScript is present everywhere. Frontend - [ReactJS](https://reactjs.org/), [AngularJS](https://angularjs.org/), etc. Backend - [Express.js](https://expressjs.com/), [Meteor.js](https://www.meteor.com/), etc. Guess what? You can also build an Android app using your ReactJS skills, and for that, we have [React Native](https://facebook.github.io/react-native/) to the rescue. Being a beginner, I am not aware of more amazing frameworks, but I admit that JavaScript is very versatile and a very interesting language to learn. 

Now let's see some fun facts - but very important to remember, to avoid coding mistakes.

# The implicit type conversion for Arithmetic operators

## Multiplication

The obvious way to multiply 2 by 2

{% highlight js %}

2 * 2 = 4 

{% endhighlight js %}

JavaScript can also take string operands and perform implicit type conversion on them, provided they are convertible into numeric values. For example, 

{% highlight js %}

"5" * 2 = 10

{% endhighlight js %}

OR

{% highlight js %}

"3" * "3" = 9

"JS" * 6 = NaN  //"JS" cannot be converted to a number

"Two" * 3 = NaN //"Two" cannot be converted to a number as well

{% endhighlight js %}

## Division

The obvious way to divide 10 by 2

{% highlight js %}

10 / 2 = 5

{% endhighlight js %}

By now, you might be familiar.

{% highlight js %}

"30" / 2 = 15

{% endhighlight js %}

Again,

{% highlight js %}

"100" / "4" = 25

{% endhighlight js %}

Let's get this done with the last operator.

## Addition

Well, this needs no explanation. 

{% highlight js %}

5 + 5 = 10

{% endhighlight js %}

**But,**

{% highlight js %}

"10" + 10 = 1010

{% endhighlight js %}

![Are you serious?](/assets/images/2018_06_02/serious.jpg)

**WTF? 1010? No implicit type conversion?** 

Yes, things work quite differently for "+" operator, so whenever one of the operands is of type string, the other operand gets converted to the string type too. 

For addition to work, both the operands should be of numeric types. 

{% highlight js %}

10 + 10 = 20

{% endhighlight js %}
 
OR
 
{% highlight js %}

30 + Number("20") = 50

{% endhighlight js %}

OR

{% highlight js %}

20 + +"20" = 40

{% endhighlight js %}

**What?** - Wait, I am not drunk. That is an amazing thing about using "+" as a unary operator. Prepend it to any string representing a number, and it converts the string into its equivalent numeric value. 

For simplicity:

{% highlight js %}

20 + (+"20") = 40

{% endhighlight js %}

Hold on, let me show you some more interesting things about using "+" as a unary operator. *Caution: Do not go crazy.* 

{% highlight js %}

25 + +null = 25

{% endhighlight js %}

Also,

{% highlight js %}

50 + +"" = 50

{% endhighlight js %}

In JS, the equivalent numeric value for the null and empty string is 0. 

**Point to note:** If you prepend it to any string containing alphabetic keywords like "Hulk" or "Tron", it would result into NaN (Not a Number) and any operation with NaN, results as NaN. 

# The comparison and equality operators

Usually comparison and equality operators like >, >=, <, <=, and == are used with numbers. 

For example, let's say we want to check if 2 is greater than 1.

{% highlight js %}

2 > 1 

{% endhighlight js %}

This will return a boolean value, either <span style="color: green">true</span> or <span style="color: red">false</span>, depending on the comparison. In above example, it will return <span style="color: green">true</span>.  

Well, you won't be surprised to know that JavaScript performs implicit type conversion here as well - just like it did for arithmetic operators. 

Let's provide a string representing a numeric value.

{% highlight js %}

"10" == 100  

{% endhighlight js %}

Returns <span style="color: red">false</span>.

{% highlight js %}

"100" > "10"

{% endhighlight js %}

Returns <span style="color: green">true</span>.

Let's try out something cooler.

{% highlight js %}

true > 0

{% endhighlight js %}

Returns <span style="color: green">true</span>, since <span style="color: green">true</span> is represented as 1 in its numeric form, 1 > 0 is always true.

{% highlight js %}

false <= 0

{% endhighlight js %}

Returns <span style="color: green">true</span>, since <span style="color: red">false</span> is represented as 0 in its numeric form, 0 <= 0 is always true. 

Also, for empty strings,

{% highlight js %}

"" > -1

{% endhighlight js %}

Returns <span style="color: green">true</span>, since &quot;&quot; (empty string) is represented as 0 in it's numeric form, 0 > -1 is always true.

Same applies to null,

{% highlight js %}

null > 0

{% endhighlight js %}

Returns <span style="color: red">false</span>, because null is represented as 0, and 0 > 0 is always false.

Also,

{% highlight js %}

null >= 0

{% endhighlight js %}

Returns <span style="color: green">true</span>, as null is not greater than 0, from this we can confirm that null is equal to 0.

**But,**

{% highlight js %}

null == 0

{% endhighlight js %}

Returns <span style="color: red">false</span>. 

**WTF?** If null > 0 is <span style="color: red">false</span>, and null >= 0 is <span style="color: green">true</span>, it becomes clear that null has to be equal to 0, right? Nope, not in JavaScript. 

**Rather,**

{% highlight js %}

null == undefined

{% endhighlight js %}

Returns <span style="color: green">true</span>.

**WHAT THE F\*CK IS GOING ON HERE!**

![Seriously?](/assets/images/2018_06_02/seriously.gif)

Although it is a part of design spec, I googled why null == undefined returns <span style="color: green">true</span>, it's because (take this with a pinch of salt) both null and undefined technically represents nothing (and are also falsy in nature), hence they are shown to be equal when we use the equality operator. Of course, if we use strict equality (===), we get false because both belong to types of their own. Therefore, a point to remember is that the null represents itself to be 0 when used with comparison operators like >= or <= or < or >, but that does not apply when we use the equality operator. 

Well, that was it. I am sure there is more to come, but I hope you guys find JavaScript amusing as well. If I failed to prove that, I would recommend few videos by Gary Bernhardt on JavaScript. 

## Recommended

 - [Wat](https://www.destroyallsoftware.com/talks/wat) (JS starting from 1:21)
 - [The Birth & Death of JavaScript](https://www.destroyallsoftware.com/talks/the-birth-and-death-of-javascript)
