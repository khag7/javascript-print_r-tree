# Javascript print_r beautifier.
==============================


Converts scalar string output from PHP print_r function to collapsible DOM structure.

Demo: http://vearutop.github.io/javascript-print_r-tree/

For PHP code you can use `print_rc` (`print_rc.php`) function instead of `print_r`.

Or just add a javascript bookmarklet as so...

```
javascript:(function(e){function n(e){return e.replace(/(Array|Object)\n(\s*)\(/g,'<span class="debug-controls"><a class="toggle-display" href="#">$1</a> '+'<a class="toggle-children" href="#" title="toggle children">\\</a> '+'<a class="toggle-recursive" href="#" title="toggle recursive">*</a> '+'</span><span class="debug-data" style="display:none"> '+"\n$2(").replace(/\n(\s*?)\)\n/g,"\n$1)\n</span>")}function r(e,t){if("undefined"==typeof t){t=i(e,0)}e.style.display=t?"":"none";return t}function i(e,t){var n;if(!t){return e.style.display=="none"}else{for(var r=0;r<e.childNodes.length;++r){if("debug-data"==e.childNodes[r].className){n=i(e.childNodes[r],t-1);if(-1!=n){return n}}}}return-1}function s(e,t,n){if("undefined"==typeof n){n=i(e,t?2:1);if(-1==n){if(t){s(e,false);return}else{r(e);return}}}for(var o=0;o<e.childNodes.length;++o){if("debug-data"==e.childNodes[o].className){r(e.childNodes[o],n);if(t){s(e.childNodes[o],true,n)}}}if(n){r(e,n)}}function o(e){e.innerHTML=n(e.innerHTML);var t=e.getElementsByTagName("a");for(var i=0;i<t.length;++i){t[i].onclick=function(){var e=this.className,t=this.parentNode.nextSibling;if(e=="toggle-display"){r(t)}else if(e=="toggle-children"){s(t,false)}else if(e=="toggle-recursive"){s(t,true)}return false}}if("none"==e.style.display){e.style.display=""}}if("undefined"==typeof e){var t=document.getElementsByTagName("pre");Array.prototype.forEach.call(t,o);}})()
```
