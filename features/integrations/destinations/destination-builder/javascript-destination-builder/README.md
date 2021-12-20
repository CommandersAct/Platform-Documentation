# Javascript destination builder

For more advanced users, we propose to create custom destinations using server-side **javascript** (aka Node.js), but with a simplified subset of Node.js : the _Sandboxed Javascript_.

## Sandboxed Javascript

Sandboxed JavaScript is a simplified Javascript that allows you to execute arbitrary JavaScript logic from your custom destination in a secure manner. Some JavaScript functionalities have been restricted or disabled in order to create a safe and fast execution environment.

This simplified Javascript is based on [helpers](serverside-js-helpers.md), set of methods that allow you to easily process and send your data.
