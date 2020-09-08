---
layout: post
title: html과 css 기본
tags: [web]
color: rgb(204, 204, 255)
---



기본적인 html 태그와 css 속성 정리

<br>

# HTML 태그

몇가지 기본적인 html tag들에 대해서 정리한다. 

### - HTML Heading 

html heading은  제목이나 부제목을 쓸 때 주로 사용한다. 

``` html
<h1> Heading1 </h1>
<h2> Heading2 </h2>
<h3> Heading3 </h3>
<h4> Heading4 </h4>
<h5> Heading5 </h5>
<h6> Heading6 </h6>
```

![heading](/assets/img/pp1/heading.PNG)

<br>

### - HTML Paragraph 

paragraph는 새 줄에서 시작하고, text block으로 생각하면 된다.

```html
<p>This is a paragraph.</p>
<p>This is another paragraph.</p>
<p>Hello, parargaph:)</p>
```

![para](/assets/img/pp1/para.PNG)

<br>

### - HTML Style 

html style attribute는 element에 color, font, size 등등 으로 스타일을 줄 수 있다. 

```html
<h1 style="text-align:center;">Centered Heading</h1>
<p>I am normal</p>
<p style="color:yellow;background-color:gray;">I am yellow and gray background</p>
<p style="color:tomato;background-color:powderblue;">I am tomato and powderblue background</p>
<p style="font-size:35px;color:green;">I am big and green</p>
<p style="font-family:courier;"><strong>This is a paragraph.</strong></p>
```

#### - Use `background-color` for background color

#### - Use `color` for text colors

#### - Use `font-family` for text fonts

#### - Use `font-size` for text sizes

#### - Use `text-align` for text alignment

![st1](/assets/img/pp1/st2.PNG)

<br>

### - HTML Comments 

html에서의 주석이다. 주석은 웹에서 보이지 않는다. 

```html
<!-- 주석입니다.~ -->
```

<br>

### - HTML Links 

html link는 typerlink이다. link를 클릭해서, 다른 document로 넘어갈 수 있다. 

`<a>` element 의 attribute에서 가장 중요한 부분은 `href`인데, 이 부분에 link의 destination이 들어간다. 

```html
<a href="https://www.w3schools.com">This is w3 schools. Click it!</a>
```

![link](/assets/img/pp1/link.PNG)

<br>

### - HTML Images

html을 통해서 웹 페이지에 image를 올릴수 있다. 

```html
<h2>HTML Image</h2>
<img src="img_girl.jpg" alt="Girl in a jacket" width="240" height="320">
```

![image](/assets/img/pp1/image.PNG)

<br>

### - HTML Table

```html
<table style="width:60%">
  <tr>
    <th>Firstname</th>
    <th>Lastname</th> 
    <th>Age</th>
  </tr>
  <tr>
    <td>Eve</td>
    <td>Jackson</td>
    <td>94</td>
  </tr>
  <tr>
    <td>John</td>
    <td>Doe</td>
    <td>80</td>
  </tr>
</table>
```

![table](/assets/img/pp1/table.PNG)

<br>

### - HTML Lists

요소들을 list로 묶을 수 있다. 

```html
<ul>
  <li>Coffee</li>
  <li>Tea</li>
</ul>  

<ol>
  <li>Monkey</li>
  <li>Rabbit</li>
</ol> 

<dl>
  <dt>Coffee</dt>
  <dd>- black hot drink</dd>
  <dt>Milk</dt>
  <dd>- white cold drink</dd>
</dl>
```

![list](/assets/img/pp1/list.PNG)

<br>

### - HTML Block and Inline elements

block-level element는 새 줄에서 시작하고, 넓이를 꽉 채운다. inline element는 새 줄에서 시작하지 않고 가능한 만큼 차지한다.  

```html
<p>This is an inline span <span style="border: 1px solid black">Hello World</span> element inside a paragraph.</p>

<div style="border: 1px solid black">Hello World</div>

<p>The DIV element is a block element, and will always start on a new line and take up the full width available (stretches out to the left and right as far as it can).</p>

<p>The SPAN element is an inline element, and will not start on a new line and only takes up as much width as necessary.</p>
```

![div](/assets/img/pp1/div.PNG)

<br>

### - HTML class Attribute

The HTML `class` attribute는 HTML element에 대해 class를 나눌때 사용한다. 

Multiple HTML elements can share the same class. 

class는 스타일에서 점(.)을 찍는다. 

```html
<head>
<style>
.city {
  background-color: tomato;
  color: white;
  border: 2px solid black;
  margin: 20px;
  padding: 20px;
}
</style>
</head>
<body>

<div class="city">
<h2>London</h2>
<p>London is the capital of England.</p>
</div> 

<div class="city">
<h2>Paris</h2>
<p>Paris is the capital of France.</p>
</div>

<div class="city">
<h2>Tokyo</h2>
<p>Tokyo is the capital of Japan.</p>
</div>

</body>
```

![class](/assets/img/pp1/class.PNG)

<br>

### - HTML id Attribute

The HTML `id` attribute는 HTML element에 대해 unique한 id를 나눌 때 사용된다. 

You cannot have more than one element with the same id in an HTML document.

id는 style에서 #으로 표시한다. 

``` html
<head>
<style>
#myHeader {
  background-color: lightblue;
  color: black;
  padding: 40px;
  text-align: center;
} 
</style>
</head>
<body>

<h2>The id Attribute</h2>
<p>Use CSS to style an element with the id "myHeader":</p>

<h1 id="myHeader">My Header</h1>

</body>
```

![id](/assets/img/pp1/id.PNG)

<br>



# CSS 태그

