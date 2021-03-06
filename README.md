node-requirejs-define
=====================

[![Build Status](https://travis-ci.org/docmarionum1/node-requirejs-define.svg?branch=master)](https://travis-ci.org/docmarionum1/node-requirejs-define)

Implements the `define` function for node to allow the same AMD modules created for client-side to be reused on the server without maintaining a second copy.

##Install

    npm install node-requirejs-define
  
##Usage

###Define a module
    
    // c.js
    define([
      'lib/a', //Include some custom modules in a defined path
      'lib/b', 
      'fs' //Include builtin modules or other modules not defined as AMD
    ], function(a, b, fs) {
      //Do stuff
      return stuff;
    });

###Require the module
    
    // Require define
    define = require('node-requirejs-define');
    
    //Configure define using the same configuration as requestsjs.
    define.config({
      baseUrl: __dirname,
      paths: {
        'bar': 'lib/foo/bar',
        'biz': 'lib/foo/biz'
      }
    });
    
    //Require your AMD module
    c = require('./c');
    
##Tests

    npm tests
