#JavaScript is Awesome

```javascript
var _name, _dob, _clock;

function Player(options) {
  _name = options.name;
  _dob = options.dob;
}

Person.prototype = {
  get age() {
    return _clock.now() - new Date()
  }
  
  set dob(value) {
    
    return this._clock.now() - new Date()
  }
}
```




# javascript-as-a-non-toy-language

##History

 - original purpose
 - asi
 

##The Event Loop
Single threading benefits.
Asynchronous code
setTimeout/setInterval

##Types

typeof
instanceof

##Prototypes

{ __proto__: foo }
Object.setPrototypeOf
Object.getPrototypeOf
V8 optimisations via hidden classes

##Scope


##The Receiver



##Functions as Obejcts

```javascript
function noop() {}

noop.truthy = function() {
	return true;
};

noop.falsy = function() {
	return false;
};

return noop;
```
	
 - noop example
 - examples of implementations in other languages
 - Number and event-loop, performance optimizations, people involved in creation of V8 and historical association
 - origins of Java / JavaScript

performance comparisons 

##Concurrency

##Lazy Evaluation and Thunks

http://stackoverflow.com/questions/17329083/javascript-lazy-evaluation-fibonacci-function?rq=1

	var fib = function (a, b) {
	  var c = a + b
	  return { "this": c, "next": function () { return fib(b, c) } }
	}

Yield.

##Continuations

##Monadic Style

 - Promises, deferreds

##Recursion

##Closures

##Currying (partial application)

	function partial(fn) {
	  var args, slice;
	
	  if(typeof fn !== 'function') {
	    throw 'First argument must be a function.';
	  }
	
	  if(arguments.length <= 1) {
	  	return fn;
	  }
	
	  slice = Array.prototype.slice;
	  args = slice.call(arguments, 1);
	
	  return function() {    
	    return fn.apply(this, args.concat(slice.call(arguments)));
	  }
	}
	
	function foo (a, b) {
		console.log(a, b);
	}
	
	var fnP = partial(partial(foo, 'a'), 'b');

	fnP('c'); // a b c
