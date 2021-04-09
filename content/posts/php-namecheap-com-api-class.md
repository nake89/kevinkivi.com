---
title: 'PHP: Namecheap.com API Class'
date: Tue, 16 May 2017 18:19:52 +0000
draft: false
tags: ['Code', 'PHP']
---

I built a simple to use class in PHP for the namecheap.com API. It supports all of Namecheap's API methods. I released the code on GitHub. Example of usage:
```php
<?php
require 'namecheap.class.php';
$username = 'YOUR USERNAME';
$apiKey = 'YOUR API KEY';
$clientIp = 'IP WHERE THIS YOUR SCRIPT IS HOSTED';
$namecheap = new Namecheap ($username, $apiKey, $clientIp) ;
$data\["Command"\] = "namecheap.ssl.getList";
$returned = $namecheap->request($data);
print\_r($returned)
 ?>
```
GitHub release:[ https://github.com/nake89/namecheap](https://github.com/nake89/namecheap)
