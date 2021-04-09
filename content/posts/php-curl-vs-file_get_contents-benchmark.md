---
title: 'PHP: Curl vs file_get_contents benchmark'
date: Mon, 13 Aug 2018 17:55:17 +0000
draft: false
tags: ['PHP']
---

I benchmarked curl vs file\_get\_contents in **getting headers only** and returning the HTTP Status Code. Here are the results:
```
kevinkivi@server:~/my/secret/directory$ php curlvsfgctest.php
Testing curl speed

Domain: http://google.com
Status: 301
Domain: http://yahoo.com
Status: 301
Domain: http://nytimes.com
Status: 301
Domain: http://theguardian.com
Status: 301
Domain: http://wikipedia.org
Status: 301

Curl speed was 0.35739207267761


Testing file\_get\_contents speed

Domain: http://google.com
Status: HTTP/1.0 301 Moved Permanently
Domain: http://yahoo.com
Status: HTTP/1.0 301 Moved Permanently
Domain: http://nytimes.com
Status: HTTP/1.1 301 Moved Permanently
Domain: http://theguardian.com
Status: HTTP/1.1 301
Domain: http://wikipedia.org
Status: HTTP/1.1 301 TLS Redirect

file\_get\_contents was 1.7153549194336
```
Below is the source code:

```php
<?php
 
class Curlvsfg {
 
    public function curlGetHeaders($url) {
        // Create a cURL handle
        $ch = curl_init($url);
        // stop printing everything on screen
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
        //enable headers
        curl_setopt($ch, CURLOPT_HEADER, 1);
        //get only headers
        curl_setopt($ch, CURLOPT_NOBODY, 1);
        // Execute
        curl_exec($ch); 
        // Check HTTP status code
        if (!curl_errno($ch)) {
            $http_code = curl_getinfo($ch, CURLINFO_RESPONSE_CODE);
        } 
        // Close handle
        curl_close($ch);
        
        if ($http_code) {
            return $http_code;
        } else {
            return FALSE;
        }
    }
 
    public function fgcGetHeaders($url) {
        $options['http'] = array(
            'method' => "HEAD",
            'ignore_errors' => 1,
        );
        $context = stream_context_create($options);
        $body = file_get_contents($url, NULL, $context);
        return $http_response_header[0];
    }
 
}
 
$test = new Curlvsfg;
 
$domains[] = "http://google.com";
$domains[] = "http://yahoo.com";
$domains[] = "http://nytimes.com";
$domains[] = "http://theguardian.com";
$domains[] = "http://wikipedia.org";
 
echo "Testing curl speed\n\n";
$time_pre = microtime(true);
foreach ($domains as $domain) {
    echo "Domain: $domain\n";
    echo "Status: ".$test->curlGetHeaders($domain)."\n";
}
$time_post = microtime(true);
$exec_time = $time_post - $time_pre;
echo "\n";
echo "Curl speed was $exec_time\n";
echo "\n";
echo "\n";
 
echo "Testing file_get_contents speed\n\n";
$time_pre = microtime(true);
foreach ($domains as $domain) {
    echo "Domain: $domain\n";
    echo "Status: ".$test->fgcGetHeaders($domain)."\n";
}
$time_post = microtime(true);
$exec_time = $time_post - $time_pre;
echo "\n";
echo "file_get_contents was $exec_time";
echo "\n";
echo "\n";
```

Closing statement: Curl is almost 5 times faster. Use Curl unless you cant.
