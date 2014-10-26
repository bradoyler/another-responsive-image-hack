Yet another responsive image hack
=============================

An ultra-light responsive image technique that even works in IE8

```html
<img class="js-adaptive-img" src='//:0' 
     data-bp0='http://bradoyler.com/pic-small.jpg' 
     data-bp1='http://bradoyler.com/pic-med.jpg' 
     data-bp2='http://bradoyler.com/pic-large.jpg' 
     data-bp3='http://bradoyler.com/pic-xlarge.jpg'>

<script>
// inline the minified js
function adaptImages(e,t,n){for(var r=0;r<n.length;r++){var i=n[r],s=r+1,o="99999";if(n[s]){o=n[s]}if(e>=i&&e<o){var u=document.querySelectorAll(t);for(var a=0;a<u.length;a++){u[a].setAttribute("src",u[a].getAttribute("data-bp"+r))}}}}function viewport(){var e=window,t="inner";if(!("innerWidth"in window)){t="client";e=document.documentElement||document.body}return{width:e[t+"Width"],height:e[t+"Height"]}}

// call adaptImage with screen width, img selector & breakpoints
adaptImages(viewport().width, '.js-adaptive-img', [0,768,992,1230]);
// u *could* attach this to window.onresize event
</script>
```
#### Thats it.
This was intended to be a performant technique for 'above the fold' responsive images.

#### [Demo](http://bradoyler.github.io/another-responsive-image-hack/)
