## Interpreting the Visualization

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
