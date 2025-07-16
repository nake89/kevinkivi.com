---
title: "My first userscript"
date: 2006-05-07
lastmod: 2025-07-16T14:58:00+02:00
draft: false
tags:
  ["userscript", "javascript", "post-from-old-blog"]
---

Originally posted at: http://nake89.blogspot.com/2006/05/my-first-userscript.html

I know I havent posted in a long time. I totally forgot about blogger. Anyway just wanted to add something and now I have a reason. I made a cool userscript. Userscripts are things to change something about a page, to make it more usable or pretty or something. It works with firefox if you have greasemonkey installed. Anyway here is the script: [http://userscripts.org/scripts/show/4039](https://web.archive.org/web/20070119151139/http://userscripts.org/scripts/show/4039) It puts a simple favicon in a forum I post alot. The favicon: ![image](favicon.gif) Its short for ElxDraco. Well duh. :D

Update from 2025: I here is the userscript code:
```javascript
// ==UserScript==
// @name            FavIcon to elxdraco.net
// @namespace       http://nake89.blogspot.com
// @description     Puts a favicon to elxdraco.net, a popular hl-engine scripting site.
// @include         *elxdraco.net*
// ==/UserScript==



(function() {
  
// Creates an html element 
	var link = document.createElement('link');
	
// Sets attributes of element
	link.setAttribute('rel', 'shortcut icon');
	link.setAttribute('href', 

// Change this to the site of the picture you want to use for an icon
	'data:image/gif;base64,R0lGODlhEAAQAPcAAAAAAIAAAACAAICAAAAAgIAAgACAgICAgMDAwP8AAAD/AP//AAAA//8A/wD/ /////wAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAMwAAZgAAmQAAzAAA/wAzAAAzMwAzZgAzmQAzzAAz/wBm AABmMwBmZgBmmQBmzABm/wCZAACZMwCZZgCZmQCZzACZ/wDMAADMMwDMZgDMmQDMzADM/wD/AAD/ MwD/ZgD/mQD/zAD//zMAADMAMzMAZjMAmTMAzDMA/zMzADMzMzMzZjMzmTMzzDMz/zNmADNmMzNm ZjNmmTNmzDNm/zOZADOZMzOZZjOZmTOZzDOZ/zPMADPMMzPMZjPMmTPMzDPM/zP/ADP/MzP/ZjP/ mTP/zDP//2YAAGYAM2YAZmYAmWYAzGYA/2YzAGYzM2YzZmYzmWYzzGYz/2ZmAGZmM2ZmZmZmmWZm zGZm/2aZAGaZM2aZZmaZmWaZzGaZ/2bMAGbMM2bMZmbMmWbMzGbM/2b/AGb/M2b/Zmb/mWb/zGb/ /5kAAJkAM5kAZpkAmZkAzJkA/5kzAJkzM5kzZpkzmZkzzJkz/5lmAJlmM5lmZplmmZlmzJlm/5mZ AJmZM5mZZpmZmZmZzJmZ/5nMAJnMM5nMZpnMmZnMzJnM/5n/AJn/M5n/Zpn/mZn/zJn//8wAAMwA M8wAZswAmcwAzMwA/8wzAMwzM8wzZswzmcwzzMwz/8xmAMxmM8xmZsxmmcxmzMxm/8yZAMyZM8yZ ZsyZmcyZzMyZ/8zMAMzMM8zMZszMmczMzMzM/8z/AMz/M8z/Zsz/mcz/zMz///8AAP8AM/8AZv8A mf8AzP8A//8zAP8zM/8zZv8zmf8zzP8z//9mAP9mM/9mZv9mmf9mzP9m//+ZAP+ZM/+ZZv+Zmf+Z zP+Z///MAP/MM//MZv/Mmf/MzP/M////AP//M///Zv//mf//zP///yH5BAEAABAALAAAAAAQABAA AAg8ALkJHCjwn8GDBrkhXMhQIcOH/xxCXEiQIESJEw9i1Ggx4UOMDit21DhxY8SLDVFSVInQpMeW JWGWHBkQADs=');


// Sets dimensions of icon. 16px x 16px is the standard size
	link.setAttribute('height', '16px');
	link.setAttribute('width', '16px');

// Retrieves the <head> tag
	var head = document.getElementsByTagName('head')[0];

// Appends the html from the link variable into the head  
	head.appendChild(link);


})();
```
