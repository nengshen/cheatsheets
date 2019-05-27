---
title: JavaScript Faq
category: JavaScript
layout: 2017/sheet
---

## Failed to execute 'open' on 'XMLHttpRequest': Invalid URL

```
Uncaught (in promise) DOMException: Failed to execute 'open' on 'XMLHttpRequest': Invalid URL
```

解决方案：url前面一定要加http://

https://segmentfault.com/q/1010000013378685
https://blog.csdn.net/rainbow8300/article/details/88662490


## Access-Control-Allow-* ##

关于 Access-Control-Allow-* 的设置问题.

### 常规写法 ###

```javascript
var app = express()
app.use(function(req,res,next){
    res.header('Access-Control-Allow-Origin', 'http://localhost:3000');
    res.header('Access-Control-Allow-Credentials','true');
    res.header('Access-Control-Allow-Methods', 'GET,PUT,POST,DELETE,OPTIONS,HEAD');
    res.header('Access-Control-Allow-Headers', 'Origin, X-Requested-With, Content-Type, Accept');
    next();
});
```

### cors包 ###

```javascript
var app = express()
var cors = require('cors');
const corsOptions = {
     origin: [
         'http://localhost:3000',
     ],
     methods: 'GET,HEAD,PUT,PATCH,POST,DELETE,OPTIONS',
     credentials: true,
     allowedHeaders: ['Origin, X-Requested-With, Content-Type, Accept', 'Authorization']
};
app.use(cors(corsOptions));
```

或者

```javascript
var app = express()
var whitelist = ['http://localhost:3000', 'http://example1.com', 'http://example2.com']
var corsOptions = function (req, callback) {
    var corsOptions;
    if (whitelist.indexOf(req.header('Origin')) !== -1) {
         corsOptions = { origin: true } // reflect (enable) the requested origin in the CORS response
    } else {
         corsOptions = { origin: false } // disable CORS for this request
    }
    callback(null, corsOptions) // callback expects two parameters: error and options
}
corsOptions.method = 'GET,HEAD,PUT,PATCH,POST,DELETE,OPTIONS',
corsOptions.credentials = true,
corsOptions.allowedHeaders = ['Origin, X-Requested-With, Content-Type, Accept', 'Authorization']
app.use(cors(corsOptions));
```
