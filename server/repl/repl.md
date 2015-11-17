# REPL

The idea is simple: you can start a REPL for your application and interact with it.

## Basic Example

- Make a file called `main.js` that contains all your modules. In this file we are going to set up a REPL.
- Make another file called `custom.js`. In this file we are going to add a custom function that gets exported. The idea is simple: we want to load the custom function when the REPL starts.


### `custom.js`

Our `custom.js` file is going to look very simple:

```javascript
module.exports = function () {
    return 'hello world';
};

```

That's it for now. Our file exports a function that returns the string `hello world` once it is called.

### `main.js`

In this file, first we are going to require our custom file:

```javascript
var custom = require('./custom');
```

So far, nothing special. Now, here comes the interesting part: we are going to require the `REPL` module and set its context:

```javascript

var repl = require("repl");
var replServer = repl.start({
    prompt: "App > "
});
replServer.context.custom = custom;
```

Now, if you run `node main.js` you should be able to see the repl:


```
App > custom()
'hello world'
```

## Summary

Just to recap, your final files would look like this:

`custom.js`

```javascript
module.exports = function () {
    return 'hello world';
};
```

`main.js`

```javascript
var custom = require('./custom');
var repl = require("repl");
var replServer = repl.start({
    prompt: "App > "
});
replServer.context.custom = custom;

```

Then you can start the REPL with `node main.js` and when the REPL comes up, you can run the method:


```
App > custom()
'hello world'
```

# Reference

Adopted from Derek's [blog](http://derickbailey.com/2014/07/02/build-your-own-app-specific-repl-for-your-nodejs-app/?__s=6n2n6htgba6o5nfw3kib)

