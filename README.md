


```
$> npm install
$> npm run mock
$> npm start

```

```js
var express = require('express');
var bodyParser = require('body-parser');
var app = express();

// app.use(function (req, res, next) {
//     req.on('data', function (chunk) {
//         console.log(JSON.parse(chunk.toString()))
//     });
//     next();
// });

app.get('/', function (req, res) {
    res.send('Hello World!');
});

app.use(bodyParser.json());

app.post('/payload', function (req, res) {
    console.log(new Date(), req.body.ref)
    res.send('ok');
});

app.listen(8088, function () {
    console.log('listening on port 8088!');
});
```


```js
var ngrok = require('ngrok');

ngrok.connect({addr: 8088}, function(err, url) {
    console.log(url)
});
```