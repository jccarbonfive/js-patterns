!SLIDE bullets incremental

# Inheritance

* No classes in JavaScript
* Class-based inheritance
* Prototypal inheritance

!SLIDE small execute

# Class-based Inheritanceo

    @@@ JavaScript
    function Parent() {}

    Parent.prototype.hi = function () {
      alert('parent');
    };

    function Child () {}

    Child.prototype = new Parent();

    var child = new Child();
    child.hi(); // parent

!SLIDE small execute

# Prototypal Inheritance

    @@@ JavaScript
    var parent = {
      hi: function () {
        alert('parent');
      }
    }

    Object.create = function (object) {
      var F = function () {};
      F.prototype = object;
      return new F();
    };

    var child = Object.create(parent);
    child.hi(); // parent

!SLIDE bullets incremental

# Borrowing Methods

* Function#apply
* Function#call
* First argument is the context i.e., 'this'
* Differ in remaining parameters

!SLIDE smaller execute

# Cont'd

    @@@ JavaScript
    function foo () {
      var args = Array.prototype.slice.call(arguments, 1, 3);
      // args is now an Array
    }

    var bar = {
      hi: function (greeting) {
        alert(greeting + ' ' + this.name);
      }
    };

    var baz = {
      name: 'baz'
    }

    bar.hi.apply(baz, ['yo']); // yo baz
    bar.hi.call(baz, 'hi');    // hi baz

!SLIDE smaller execute

# Function Binding

    @@@ JavaScript
    var obj = {
      name: 'foo',
      hi: function () {
        alert('hi ' + this.name);
      }
    };

    function foo (callback) {
      callback();
    };

    foo(obj.hi);            // hi

    function bind (object, fn) {
      return function () {
        fn.apply(object, Array.prototype.slice.call(arguments));
      }
    }

    foo(bind(obj, obj.hi)); // hi foo
