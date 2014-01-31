# Frequently asked questions

## What do these nodes that are displayed in the profiler represent?

Every node represents a group of functions that have been traced.  Depending on the customization settings, multiple functions may be grouped together.

## What do the node positions mean, and why do they keep moving?

The graph is layed out top to bottom, similar to a call stack.  However, with asynchronous calls, note that it's not always a correct answer for what should be on 'top'

## What is an origin?

An origin is the code invoked through an application starting at some origination point, such as a web request.  Web routes (e.g. express routes) are built in by default.  To see the processing for an individual url for example, simply choose that origin in the customization panel.
