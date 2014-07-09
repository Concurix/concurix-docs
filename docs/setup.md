# Getting started

## Creating an account

To create an account for Concurix, go to http://concurix.com/plans and follow the instructions for the product you wish to buy. 

Once you have registered, you will be taken to the [manage projects](http://concurix.com/manage_projects) page to configure your initial project and get an account key.

## Adding Concurix monitoring to your Node.js project

Add the `concurix` module to your project:

```bash
$ npm install --save concurix
```

Then, in the beginning of your server code, before you `require` any modules you wish to monitor, initialize and start the Concurix monitor.

Include your API key.

```javascript
var concurix = require("concurix")({
  accountKey: "<Your Account Key>",
  email: "your@email.com"  // replace with your email address to get support
})
```

This wraps the `require` function to add monitoring to any modules that are subsequently `require`d.

## Optional: expose additional debug info

Optionally, you can pass the option `--expose-debug-as=v8debug` to `node` when you start your server, which will allow Concurix to display more precise line numbers when inspecting code.

package.json example:

```json
"scripts":{
  "start": "node --expose-debug-as=v8debug server.js"
}
```

If you start `node` without the `--expose-debug-as=v8debug` option, Concurix monitoring will still work, but line numbers will be less precise.

<!-- TODO: explain *how* line numbers will be less precise (eg. function-level instead of statement-level) -->

## Connecting to your project on concurix.com

Go to to http://concurix.com/dashboard, where you should see your project listed. (If not, check the output from your Node app in your server logs for errors.)

Click the name of your project from the dropdown on the top navigation bar.

Enjoy!
