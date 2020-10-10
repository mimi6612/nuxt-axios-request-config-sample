# nuxt-axios-request-config-sample
I created a repository for axios bug verification.

I asked on stack over flow.
https://stackoverflow.com/questions/64294100/axios-may-ignore-default-headers

When I make a request by setting headers config in the request config, the default headers are ignored on node.js.

When I run the following code on node.js (on server side rendering), the default headers are ignored.

```
import axios from "axios";
axios.defaults.headers.common["default-header"] = "default-header";
axios.get("https://jsonplaceholder.typicode.com/todos/1", {
  headers: { header1: "header1" },
})
.then((response) => {
  console.error(response.config);
});
```

The response config headers is as follows

```
  headers: {
    header1: 'header1',
    'User-Agent': 'axios/0.20.0'
  }
```

The expected response config headers is as follows

```
  headers: {
    default-header: "default-header"
    header1: "header1"
  }
```

When I run the following code on browser (like Chrome), response config headers is as expected.

Is this a bug in axios?
