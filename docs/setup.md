# Getting started

## Creating an account

If you want to see an example of how Concurix works without having to creating an account, you can monitor our example Express app at http://concurix.com/demo.

To create an account for Concurix, go to http://concurix.com/plans and click Register. <!-- TODO: Make sure products/plans page is simple enough for this to make sense. --> 

Copy your API key from a page on the site. <!-- TODO: Where? -->

## Adding Concurix monitoring to your Node.js project

(You can set up your own copy of our example project by checking out 

Add the `concurix-monitor` module to your project:

```bash
$ npm install --save concurix-monitor
```

Then, in the beginning of your server code, before you `require` any modules you wish to monitor, initialize and start the Concurix monitor.

Include your API key. <!-- TODO: How? -->

```
var cx = require("concurix-monitor")({accountKey: <your account key>});
cx.start();
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

Click the name of your project. <!-- TODO: Reconcile this with new Dashboard flow -->
