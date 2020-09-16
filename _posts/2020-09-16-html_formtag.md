---
layout: post
title: html의 Form tag 
tags: [web]
color: rgb(204, 204, 255)
---



html의 form tag를 연습해보고 정리

<br>

# Form tag

## form

form tag는 user input에 대해 HTML form을 만들기 위해서 사용된다.  form의 element는 input, textarea, button, select, option, optgroup, fieldset, label, output 중에서 하나 이성을 포함할 수 있다. 

- action: URL (form을 submit했을 때 form-data를 어디로 보낼지)
- method: get/post (form-data를 보낼 때 사용할 HTTP method를 표시)
- name: text (form의 이름)

<br>

## input

form tag내에 다양한 모양으로 입력할 수 있는 element를 제공한다. type속성으로 text, password, radio, checkbox, button, hidden, file, submit, reset 등이 있다. 

- name: element 이름

- id: element id

- readonly: 읽기 전용

- maxlength=10: 입력 글자수 개수 지정   

  *submit: form에 입력한 데이터를 서버로 전송 

  *reset: form안에 있는 element값을 초기화하는 기능 

![inputc](/assets/img/pp1/inputc.PNG)

![input](/assets/img/pp1/input.PNG)

<br>

## select / optgroup / option

 목록 중에서 항목을 선택하는 태그이다. multiple, selected 속성을 제공한다. 

![optionc](/assets/img/pp1/optionc.PNG)

![option](/assets/img/pp1/option.PNG)

<br>

## textarea 

여러줄의 텍스트를 입력받을 때 사용하는 태그이다. rows, cols 속성을 제공한다. 

![textc](/assets/img/pp1/textc.PNG)

![text](/assets/img/pp1/text.PNG)

<br>

## fieldset / legend

서로 관련된 element들을 form으로 묶는다. 

![legendc](/assets/img/pp1/legendc.PNG)

![legend](/assets/img/pp1/legend.PNG)

<br><br>

# form tag에 적용되는 CSS

## Styling input fields 

![style1code](/assets/img/pp1/style1.PNG)

![style1](/assets/img/pp1/style1-1.PNG)

![style2c](/assets/img/pp1/style2c.PNG)

![style2](/assets/img/pp1/style2.PNG)

특정 input type에 style을 주고 싶으면 attribute selector를 사용할 수 있다. input[type=text] : text field만 선택한다.

input[type=password] : password field만 선택한다. 

input[type=number] : number field만 선택한다. 

등등 

<br>

## Bordered Inputs 

 경계의 사이즈와 색을 변경할 때 border property를 사용할 수 있고, 모서리를 둥글게 할 때 border-radius를 사용할 수 있다. 

![borc](/assets/img/pp1/borc.PNG)

![bor](/assets/img/pp1/bor.PNG)



![bor2c](/assets/img/pp1/bor2c.PNG)

![bor2](/assets/img/pp1/bor2.PNG)



![borcolor](/assets/img/pp1/borcolor.PNG)

![borcol](/assets/img/pp1/borcol.PNG)

<br>

## Styling Select Menus 

![selecc](/assets/img/pp1/selecc.PNG)

![selec](/assets/img/pp1/selec.PNG)

<br>

<br>

#  Form 입력 내용을 점검하는 자바스크립트 이벤트 

 HTML event는 HTML element에서 생기는 것이다. JavaScript는 HTML page에서 사용되고 event에 반응할 수 있다. (예)

![exc](/assets/img/pp1/exc.PNG)

![ex](/assets/img/pp1/ex.PNG)

위 예시는 JavaScript code가 id=”demo로 element의 내용을 바꾼다. 반면에 아래 예시는 this.innerHTML을 사용해서 content를 바꾼다. 

![ex2c](/assets/img/pp1/ex2c.PNG)

![ex2](/assets/img/pp1/ex2.PNG)

<br>

- onchange - HTML 요소변경 
- onclick - 사용자가 HTML요소를 클릭 
- onmouseover - 사용자가 HTML요소 위로 마우스를 이동할 때 
- onmouseout - 사용자가 HTML요소에서 마우스를 멀리 이동할 때
- onkeydown - 사용자가 키보드 키를 누를 때 
- onload - 웹페이지 로딩 완료될 때 











