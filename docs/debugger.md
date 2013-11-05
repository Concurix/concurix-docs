## Notice: the debugger is deprecated

The Concurix debugger module is currently transitioning from a hosted service on
concurix.com to an open-source project. This document explains how to access the
inspector for any users who still wish to use it in this transitional period.

### Enable debugging

The concurixjs module supports web-based debugging. To enable the debugging
option, add a configuration option when requiring the conscurixjs module.

```js
var cx = require('concurixjs')({ enableDebugger: true });

cx.start();
```
 
Enabling the debugger spawns a second process that listens for a remote debugger
to connect and control your Node.js application. In your browser, go to http://concurix.com/debug
and select your project from the dropdown menu (for local projects,
use "Guest Project for Localhost"). You should see the Chrome DevTools UI open with
the source code of your program paused at a breakpoint.

With your program paused, you can examine variables, move up or down the call stack,
set breakpoints and single-step or resume your program. You can also edit your program
source code, with changes taking effect immediately. Note that changes are only made in
the memory of the running V8 engine and are not saved after the program terminates.
