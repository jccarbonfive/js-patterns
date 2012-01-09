!SLIDE smaller

# Literal Notations

    @@@ JavaScript
    var obj = {};
    var obj = new Object();  // obj.constructor === Object
    var obj = new Object(1); // obj.constructor === Number

    var array = [];
    var array = new Array();    // #length === 0
    var array = new Array(3);   // #length === 3
    var array = new Array(5.5); // RangeError: invalid array length

    var regexp = /\\/g;
    var regexp = new RegExp("\\\\", 'g');
    var regexp = /*hello*/; // SyntaxError: unexpected token ;

!SLIDE smaller execute

# Cont'd

    @@@ JavaScript
    var s = 'hello';
    s.name = 'foo';
    alert(s.name);        // undefined

    var s = new String('hello');
    s.name = 'foo';
    alert(s.name);       // foo

    var n = 3;             // typeof n === 'number'
    var n = new Number(3); // typeof n === 'object'

    var boolean = false;
    var boolean = new Boolean();

    throw new Error('fail');
    throw {
      name: 'MyCustomError',
      message: 'fail'
    };

    var date = new Date(); // no literal constructor

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
