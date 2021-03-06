---
layout: post
title: HTML fill border color solid
---

<h2 class="lightBlue">{{ page.title }}</h2>

<p class="description">{{ page.date | date_to_string }}</p>
  

CSS: 

{% highlight scss %}
div {
  height:200px;
  width:200px;
  border:solid 5px black;
  background:#159;
  border-radius:100%;
  display:inline-block;
  margin:1em;
  position:relative;
  text-align:center;
  line-height:200px;
  color:white;
  font-size:2em;
  transform:rotate(45deg);
  box-shadow:0 0 5px black, inset 0 0 5px #48a;
}
div > span {
  display:inline-block;
  transform:rotate(-45deg);
}
div:before,div:after {
  content:'';
  position:absolute;
  top:-5px;
  left:-5px;
  border:solid 5px transparent;
  height:inherit;
    width:inherit;
  border-radius:inherit;
}
.c30, .c40, .c50 {
  border-top-color:tomato;
  border-right-color:tomato;
}
.c30:before {
  border-right-color:black;
  transform:rotate(18deg)
}
.c40:before {
  border-top-color:black;
  transform:rotate(144deg)
}
.c80 {
  border-color:tomato;
  border-left-color:black;
}
.c80:before {
  border-bottom-color:tomato;
  transform:rotate(18deg)
}
body {background: #456;}
{% endhighlight %}

HTML: 

{% highlight html %}
<div class="c30">c30</div>
<div class="c40">c40</div>
<div class="c50">c50</div>
<div class="c80"><span>c80</span></div>
<p>i.e. calculate rotation needed : 30%-25% = 5% of 360deg equals 18deg to increase rotation of one border to add those 5.%</p>
{% endhighlight %}

<img src="/images/fillBorder.png"></img>