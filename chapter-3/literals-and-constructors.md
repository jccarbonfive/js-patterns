!SLIDE

# Literal Notations

    @@@ JavaScript
    var obj = {};
    var obj = new Object();

    var array = [];
    var array = new Array();

    var regexp = /hello/i;
    var regexp = new RegExp('hello', 'i');

!SLIDE

# Cont'd

    @@@ JavaScript
    var string = 'hello';
    var string = new String('hello');

    var number = 3;
    var number = new Number(3);

    var boolean = false;
    var boolean = new Boolean();

    throw new Error('fail');
    throw {
      name: 'MyCustomError',
      message: 'fail'
    };

.notes - more concise, expressive, less error-prone, {} says objects are
  literals not something that needs to made from a recipe

!SLIDE execute

# Constructor Functions

    @@@ JavaScript
    var Person = function (name) {
      this.name = name;
    };
    var foo = new Person('foo');
    alert(foo.name);    // foo

    var bar = Person('bar');
    alert(bar);         // undefined
    alert(window.name); // bar

.notes - implicitly return a new object i.e., 'this'
 can return an object from a constructor function

!SLIDE small execute

# Optional `new`

    @@@ JavaScript
    function Person (name) {
      if (! (this instanceof arguments.callee)) {
        return new arguments.callee(name);
      }
      this.name = name;
    }

    var foo = new Person('foo');
    alert(JSON.stringify(foo)); // {"name":"foo"}

    var bar = Person('bar');
    alert(JSON.stringify(bar)); // {"name":"bar"}
