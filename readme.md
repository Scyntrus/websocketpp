# Websocket++ for Bazel(Bzlmod)

This fork adds compatibility with the Bazel build system.  
This uses Bzlmod instead of WORKSPACE. See https://bazel.build/external/migration  
To use, clone this repo alongside your project repository. Add the following lines to MODULE.bazel file:  
```
bazel_dep(name = "websocketpp")
local_path_override(
    module_name = "websocketpp",
    path = "../websocketpp",
)
```
In your BUILD.bazel file, simply add `"@websocketpp"` to your build target 'deps'.  
Websocketpp headers can be included as usual with `#include "websocketpp/server.hpp"`.  
  
Changes made:  
* Add Bazel files
  * MODULE.bazel
  * BUILD.bazel
  * WORKSPACE (as of writing this, `local_path_override` fails if WORKSPACE doesn't exist, even when using Bzlmod.)
* Local header `#include`s are changed to use quotes instead of angle brackets
* A small workaround was added to "websocketpp/common/asio.hpp" on line 54 to resolve the right header for including.

WebSocket++ (0.8.2)
==========================

WebSocket++ is a header only C++ library that implements RFC6455 The WebSocket
Protocol. It allows integrating WebSocket client and server functionality into
C++ programs. It uses interchangeable network transport modules including one
based on raw char buffers, one based on C++ iostreams, and one based on Asio 
(either via Boost or standalone). End users can write additional transport
policies to support other networking or event libraries as needed.

Major Features
==============
* Full support for RFC6455
* Partial support for Hixie 76 / Hybi 00, 07-17 draft specs (server only)
* Message/event based interface
* Supports secure WebSockets (TLS), IPv6, and explicit proxies.
* Flexible dependency management (C++11 Standard Library or Boost)
* Interchangeable network transport modules (raw, iostream, Asio, or custom)
* Portable/cross platform (Posix/Windows, 32/64bit, Intel/ARM/PPC)
* Thread-safe

Get Involved
============

[![Build Status](https://travis-ci.org/zaphoyd/websocketpp.png)](https://travis-ci.org/zaphoyd/websocketpp)

**Project Website**
http://www.zaphoyd.com/websocketpp/

**User Manual**
http://docs.websocketpp.org/

**GitHub Repository**
https://github.com/zaphoyd/websocketpp/

GitHub pull requests should be submitted to the `develop` branch.

**Announcements Mailing List**
http://groups.google.com/group/websocketpp-announcements/

**IRC Channel**
 #websocketpp (freenode)

**Discussion / Development / Support Mailing List / Forum**
http://groups.google.com/group/websocketpp/

Author
======
Peter Thorson - websocketpp@zaphoyd.com
