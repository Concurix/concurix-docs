## Overview

Concurix software gives you the ability to trace and debug Node.js programs
in a web browser through the concurix.com website. Our tracer allows you
to visualize your program running in real time for in-depth structure analysis.
Our web-based debugger lets you connect to your program, examine its state
in detail, step through code, edit running code and continue.

We will describe the steps for you to set up tracing and debugging for a project
and then to visualize and debug it on concurix.com.

### Choose a Node.js Program

You can choose to trace one of your own Node.js programs or our
example program using the express web framework, located in our
public GitHub repository [express_example](https://github.com/Concurix/express_example).

To use our express_example program, clone the repository.

```bash
cd ~/Concurix
git clone http://github.com/Concurix/express_example
```

### Go to concurix.com

At the top of the concurix.com homepage, you will see a profiler link and a
debugger link.  Click on the profiler link to go to the visualization dashboard,
where you can connect to a Node.js program running the Concurix tracer. On
the dashboard, you will find a login link and a drop-down menu to select projects.
You can log in with a Google or Facebook ID or with your email address. By purchasing a
[Concurix subscription](http://www.concurix.com/products)
you can create your own projects and retrieve data from previously traced programs.
There are also two public projects that anyone may use: "Guest Project for Localhost",
which can be used for any program running on the same machine as your web browser
and "Node.js Express Demo", which connects to a continuously running demo.

### Start Tracing and Visualization

After you have created a new project associated with your ID on concurix.com,  our server
is ready to accept tracing data from your Node.js app.  The last steps are to install the
Concurix npm module, require() and start() the module in your app.js, and launch your app
which should start the tracing.

1.  Install the Concurix npm package to your node_modules directory:

    ```bash
    $ npm install concurixjs
    ```

2.  add the following line to your app.js file:

    ```js
    var cx = require('concurixjs')();
    cx.start();
    ```

3.  Run your program, which will generate trace data and open a websocket
    listening for a connection from concurix.com.

    ```bash
    $ node --expose-debug-as=v8debug app.js
    ```

Back in your browser window, select a project, either one you created yourself, or
"Guest Project for Localhost". The graphs should be updating in real 
time, displaying the trace data sent by your program.

### Interpret the Visualization

The dashboard shows features of a running program. The runtime system watches the
running programs, gathering data such as the counts and execution times of calls to
exported functions, CPU and memory usage, and the delay between registering a
callback function and calling it. Every two seconds, a snapshot of these statistics
is written to a file and sent to the dashboard. The dashboard condenses a lot of data;
the full-screen option is recommended for smaller text. Some graph features pop up a
box of detail when the mouse hovers over them.

In the upper left is a [force-directed graph](http://en.wikipedia.org/wiki/Force-directed_graph_drawing)
that summarizes function call and callback times. Each node denotes a function exported
from a Node.js module or a callback passed to a function. Each link summarizes the number
of calls between two functions or, for dotted lines, invocations of callbacks.
Large nodes represent more execution time than small ones, and thick links represent more
calls than thin ones. In both cases, log scaling keeps the elephants from obscuring
the mice. Link lengths do not map directly to input data but are rather used to keep
nodes from piling up. Node color indicates a function's module. Force-directed graphs
are typically laid out with an initial approximation that is then improved over a series
of steps, so these charts show motion both within and between time steps.

### Enable debugging

 
The concurixjs module also supports web-based debugging.  To enable the debugging
option, add a configuration option when requiring the conscurixjs module.

```js
var cx = require('concurixjs')({ enableDebugger: true });

cx.start();
```
 
Enabling the debugger spawns a second process that listens for a remote debugger
to connect and control your Node.js application. In your browser, open to concurix.com,
click on "debugger". Select your project from the dropdown menu or, for local projects,
use the "Guest Project for Localhost". You should see the Chrome DevTools UI open with
the source code of your program paused at a breakpoint.

With your program paused, you can examine variables, move up or down the call stack,
set breakpoints and single-step or resume your program. You can also edit your program
source code, with changes taking effect immediately. Note that changes are only made in
the memory of the running V8 engine and are not saved after the program terminates.
