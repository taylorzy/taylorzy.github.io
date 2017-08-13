---
layout: post
title: RedCloth Missing problem when run Jekyll as local server
---

<h2 class="lightBlue">{{ page.title }}</h2>

<p class="description">{{ page.date | date_to_string }}</p>

<p>Following the instruction on Github help: "Using Jekyll with Pages":https://help.github.com/articles/using-jekyll-with-pages/ will meet the below error when trying to execute server running command:</p>

<pre class="prettyprint">
bundle exec jekyll serve
</pre>

<img src="/images/missingRedClothError.png"></img>

Run redcloth.bat under &lt;your ruby install directory&gt;/bin will see error:
<img src="/images/redClothScanReadError.png"></img>

Go to <pre class="prettyprint">&lt;your ruby install directory&gt;/lib/ruby/gems/2.2.0/gems/RedCloth-4.2.9/ext</pre>

Create folder "2.2" and copy /redcloth_scan/redcloth_scan.so into the new folder created.

Go back to application directory and rerun 
<pre class="prettyprint">bundle exec jekyll serve</pre> 
problem should be disappeared and the server is running successfully on http://localhost:4000/.