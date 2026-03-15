# Azure Function

## index.js

```
module.exports = async function (context, req) {

    const a = parseFloat(req.query.a || (req.body && req.body.a));
    const b = parseFloat(req.query.b || (req.body && req.body.b));
    const op = req.query.op || (req.body && req.body.op);

    if (isNaN(a) || isNaN(b) || !op) {
        context.res = {
            status: 400,
            body: {
                error: "Please provide a, b, and op"
            }
        };
        return;
    }

    let result;

    switch (op) {
        case "add":
        case "+":
            result = a + b;
            break;

        case "sub":
        case "-":
            result = a - b;
            break;

        case "mul":
        case "*":
            result = a * b;
            break;

        case "div":
        case "/":
            if (b === 0) {
                context.res = {
                    status: 400,
                    body: { error: "Division by zero" }
                };
                return;
            }
            result = a / b;
            break;

        default:
            context.res = {
                status: 400,
                body: { error: "Invalid operation (add, sub, mul, div)" }
            };
            return;
    }

    context.res = {
        status: 200,
        body: {
            a: a,
            b: b,
            operation: op,
            result: result
        }
    };
};
```

## Test

```
https://az900func4-fcfwgqgegcf3fxhp.southeastasia-01.azurewebsites.net/api/HttpTrigger1?code=T3KcQGcSoqozSK8z7QLWMuYqraY7AD0X0MgIflbga3UpAzFujOoGdA==&a=10&b=5&op=add

https://az900func4-fcfwgqgegcf3fxhp.southeastasia-01.azurewebsites.net/api/HttpTrigger1?code=T3KcQGcSoqozSK8z7QLWMuYqraY7AD0X0MgIflbga3UpAzFujOoGdA==&a=10&b=5&op=sub

https://az900func4-fcfwgqgegcf3fxhp.southeastasia-01.azurewebsites.net/api/HttpTrigger1?code=T3KcQGcSoqozSK8z7QLWMuYqraY7AD0X0MgIflbga3UpAzFujOoGdA==&a=10&b=5&op=mul

https://az900func4-fcfwgqgegcf3fxhp.southeastasia-01.azurewebsites.net/api/HttpTrigger1?code=T3KcQGcSoqozSK8z7QLWMuYqraY7AD0X0MgIflbga3UpAzFujOoGdA==&a=10&b=5&op=div
```

...