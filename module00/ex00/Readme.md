# XSS vulnerabilities 

XSS is a security breach that occurs in web applications. It occurs when client-side scripts can be injected within a web application.

This usually occurs when external input are not protected within a web page. Any script entered within a form by a user by example could then be executed. 

An easy way to spot if a website is vulnerable to XSS attacks is to enter the following command into a form field
```js
<script>alert('hello_world')</script>
```
or
```js
alert('hello_world')
```
If a pop-up shows, the website is vulnerable to XSS attacks.