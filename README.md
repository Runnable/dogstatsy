# This isn't being actively maintained, you may be better off using: [node-dogstatsd](https://www.npmjs.com/package/node-dogstatsd)

# dogstatsy

  A simple DogStatsD client.

## Installation

```
$ npm install dogstatsy
```

## Example

```js

var Client = require('dogstatsy');
var http = require('http');
var stats = new Client({
  service: 'example'
});

setInterval(function(){
  stats.incr('requests', {
  	basic: 'tag'
  });
  var end = stats.timer('request');
  http.get('http://yahoo.com', function(err, res){
    // do stuff
    end({
      statusCode: res.statusCode
    });
  });
}, 1000);

```
