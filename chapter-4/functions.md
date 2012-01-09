!SLIDE bullets incremental

# Functions

* First class objects
* Can have attributes and methods
* Provide local scope

.notes - if, for, try don't introduce new scope

!SLIDE execute

# Defining a Function

    @@@ JavaScript
    // function declaration
    function User () {}

    // anonymous unnamed functions
    var User = function () {}
    var user = {
      hi: function () {}
    }

    // anonymous named function
    var User = function fn () {}

!SLIDE smaller execute

# Function Hoisting

    @@@ JavaScript
    function foo () {
      alert('global foo')
    }

    function bar () {
      foo();  // local foo

      function foo() {
        alert('local foo');
      }

      // baz(); undefined is not a function

      var baz = function () {
        alert('baz');
      }

      baz(); // baz
    }

    bar();
.notes - only function declarations are hoisted

!SLIDE execute

# Callback Function

    @@@ JavaScript
    function foo(callback) {
      // do something
      callback();
    }

    function bar () {
      var baz = 'baz';
      foo(function () {
        alert(baz);
      });
    }

    bar();

!SLIDE execute small

# Immediate Function

    @@@ JavaScript
    (function () {
      alert('immediate fn 1'); // immediate fn 1
    }());

    (function () {
      alert('immediate fn 2'); // immediate fn 2
    })();

    (function (global) {
      global.Person = function () {}
    }(window))

    var foo = new Person();
    foo.name = (function () { return 'foo'; }());
    alert('foo.name = ' + foo.name); // foo.name = foo

.notes - function executed right after it's created
- useful for providing a private scope

!SLIDE

# Memoization

    @@@ JavaScript
    var fibonacci = function fn (n) {
      if (! fn.cache[n]) {
        // calculate fibonacci of n
        // store it in fn.cache[n]
      }
      return fn.cache[n];
    };
    fibonacci.cache = {};
    fibonacci(4);
    fibonacci(2); // from cache

.notes - optimization to store results of previous calls in a property on the function

!SLIDE

# Configuration Objects

    @@@ JavaScript
    var foo = new Person('foo', 'bar', 42);

    var foo = new Person({ firstName: 'foo',
                           lastName: 'bar',
                           age: 42 });
