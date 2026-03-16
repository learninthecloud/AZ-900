# Azure Function

## index.js

```
module.exports = async (context, req) => {
    const {a,b,op} = req.query;
    const r = {"+":+a+ +b,"-":a-b,"*":a*b,"/":a/b};
    context.res = { body:{result:r[op]} };
};
```

## Test

```
https://az900func4-fcfwgqgegcf3fxhp.southeastasia-01.azurewebsites.net/api/HttpTrigger1?code=T3KcQGcSoqozSK8z7QLWMuYqraY7AD0X0MgIflbga3UpAzFujOoGdA==&a=10&b=5&op=+

https://az900func4-fcfwgqgegcf3fxhp.southeastasia-01.azurewebsites.net/api/HttpTrigger1?code=T3KcQGcSoqozSK8z7QLWMuYqraY7AD0X0MgIflbga3UpAzFujOoGdA==&a=10&b=5&op=-

https://az900func4-fcfwgqgegcf3fxhp.southeastasia-01.azurewebsites.net/api/HttpTrigger1?code=T3KcQGcSoqozSK8z7QLWMuYqraY7AD0X0MgIflbga3UpAzFujOoGdA==&a=10&b=5&op=*

https://az900func4-fcfwgqgegcf3fxhp.southeastasia-01.azurewebsites.net/api/HttpTrigger1?code=T3KcQGcSoqozSK8z7QLWMuYqraY7AD0X0MgIflbga3UpAzFujOoGdA==&a=10&b=5&op=/
```

...
