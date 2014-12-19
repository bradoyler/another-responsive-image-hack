Yet another responsive image hack
=============================

An ultra-light responsive image technique that even works in IE8

```html
<img class="js-adaptive-img" src="data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACwAAAAAAQABAAACAkQBADs=" 
     data-bp0='http://bradoyler.com/pic-small.jpg' 
     data-bp1='http://bradoyler.com/pic-med.jpg' 
     data-bp2='http://bradoyler.com/pic-large.jpg' 
     data-bp3='http://bradoyler.com/pic-xlarge.jpg'>

<script>
// minify and inline this after the targeted img tags
   function adaptImages(viewportwidth, selector, breakpoints){
    for(var i=0;i<breakpoints.length;i++) {
      var startwidth = breakpoints[i], nextIdx = i+1, nextwidth = '99999';
      if(breakpoints[nextIdx]) {
        nextwidth = breakpoints[nextIdx];
      }
      if(viewportwidth>=startwidth && viewportwidth < nextwidth) {
          var imgs = document.querySelectorAll(selector);
          for(var j=0;j<imgs.length;j++) {
            imgs[j].setAttribute('src',imgs[j].getAttribute('data-bp'+ i));
          }
          break;
      }
    }
  };
  // gets viewport dimensions
  function viewport() {
    var t=window,n="inner";
    if(!("innerWidth"in window)) {
      n="client";t=document.documentElement||document.body
    }
    return { width:t[n+"Width"], height:t[n+"Height"]};
  };
  
// call adaptImages with screen width, img selector & breakpoints
adaptImages(viewport().width, '.js-adaptive-img', [0,768,992,1230]);
// u *could* attach this to window.onresize event
</script>
```
#### Thats it.
This was intended to be a performant technique for 'above the fold' responsive images.

#### [Demo](http://bradoyler.github.io/another-responsive-image-hack/)
