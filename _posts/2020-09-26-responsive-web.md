---
layout: post
title: Responsive web
tags: [web]
color: rgb(204, 204, 255)

---



Responsive web에 대해서 간단한 정리

<br>

# Responsive Web 

반응형 웹이란 다양한 디바이스에서 크기에 따라 배치가 예쁘게 보일 수 있게 페이지를 만드는 것이다. 즉 웹페이지를 디바이스 화면 크기에 맞취 적합한 정보만 표시할 수 있도록 스타일을 설정하는 것이다. 

<br>

## viewport 

디바이스 화면에서 보여지는 영역이다. Desktop 사용자를 위해 만든 페이지의 크기는 mobile디바이스 화면에 안맞을 수 있다. 디바이스마다 다른 wiewport를 제어할 수 있는 방법으로, head태그안에 meta태그를 사용한다. 

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

<br>

## @media

미디어 쿼리는 단말기의 유형과 어떤 특성이나 수치에 따라 웹 사이트나 앱의 스타일을 수정할 때 유용하다. 특정 조건이 만족되는 경우에 적용되는 @media rule을 사용하여 스타일을 정의한다. 

```html
<style>
   .left, .right {
     float: left;
     width: 20%; /* The width is 20%, by default */
   }
  
   .main {
     float: left;
     width: 60%; /* The width is 60%, by default */
   }
  
   /* Use a media query to add a breakpoint at 800px: */
   @media screen and (max-width: 800px) {
     .left, .main, .right {
       width: 100%; /* The width is 100%, when the viewport is 800px or smaller */
     }
   }
</style>
```

![1](/assets/img/pp1/1.png)

![2](/assets/img/pp1/2.png)

<br>

## box-sizing 

 box-sizing은 박스의 크기를 화면에 표시하는 방식을 변경하는 속성이다. width와 height는 엘리먼트의 컨텐츠의 크기를 지정한다. 따라서 테두리가 있는 경우에는 테두리의 두께로 인해 원하는 크기를 찾기가 어렵다. box-sizing속성을 border-box로 지정하면 테두리를 포함한 크기를 지정할 수 있기 때문에 예측하기가 더 쉽다. 

```html
<head>
   <style>
       *{
           box-sizing:border-box;
       }
       div{
           margin:10px;
           width:150px;
       }
       #small{
           border:10px solid black;
       }
       #large{
           border:30px solid black;
       }
   </style>
</head>
<body>
      <div id="small">Hello</div>
      <div id="large">Hello</div>
</body>
```

![3](/assets/img/pp1/3.png)

<br>

responsive web 만들기 실습 => [http://hgusj.dothome.co.kr/lab4.html](http://hgusj.dothome.co.kr/lab4.html)