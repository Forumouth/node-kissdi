# Simple Dependency Injection for NodeJS
[![Build Status](https://travis-ci.org/Forumouth/node-kissdi.svg)](https://travis-ci.org/Forumouth/node-kissdi)

## What this?
This lib provides [Dependency Injection](https://msdn.microsoft.com/en-us/magazine/cc163739.aspx)
to NodeJS by super-simple approach.

## How to install
Just run ```npm install kissdi```

## How to use
~~~~
// kissdir has a function named 'inject' as library's member.
inject = require("kissdi").inject
/*
 * To use inject function, we need to create a "target function"
 * the target function should be an instance of Array that have a function as
 * a last element. i.e.
 */
var target = [
    "foo",
    "bar",
    function (foo, bar) {
        return function () {
            return [foo, bar];
        };
    }
];

// Then, call inject like this
var injected_func = inject(
    target,
    {
        "foo": "Hello",
        "bar": "World"
    }
);

// To obtain the return value from the target, call inject_func.invoke
var func = inject_func.invoke()
// Calling the function, ["Hello", "World"] is returned
var list = func()

// Calling invoke with an object that has corresponding paramenters as keys,
// the corresponding parameters are replaced with the given values.
var func = inject_func.invoke({
   "foo": "Konichiwa"
});
// func() returns ["Konichiwa", "World"]
var list = func()
// list = ["Konichiwa", "World"]
~~~~
