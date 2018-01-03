Sometimes you want a section to fill the entire screen, no matter what the screen size is. You can control this with vh, or view height. The number before it is a percentage, so if you want it to fill 100% of the browser, you would set it to 100. You might set it to a value like 85% to accommodate a fixed navigation menu. Create a class for the …

.fullheight { height: 85vh; }


input new types


```

<input type="search">
 
<input type="tel">
 
<input type="url">
 
<input type="email">
 
<input type="datetime">
 
<input type="date">
 
<input type="month">
 
<input type="week">
 
<input type="time">
 
<input type="datetime-local">
 
<input type="number">
 
<input type="range">
 
<input type="color">
```

#compatibilité ie
By placing the following code in between your pages’ tags, we can easily avoid many of the non-compatibility problems between HTML5 and Internet Explorer.
html5shiv.js 
remysharp.com/2009/01/07/html5-enabling-script



```
<!--[if IE]> 
<script src="http://html5shim.googlecode.com/svn/trunk/html5.js"></script> 
<![endif]--> 
```




