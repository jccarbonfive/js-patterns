!SLIDE bullets

# Essentials

* Minimizing globals
* Implied globals

!SLIDE execute

# Globals

    @@@ JavaScript
    var a = 1;
    b = 2;

    function foo () {
      c = 2;
      var d = e = 0;
    }

    foo();

    alert('window.c = ' + window.c);
    alert('window.d = ' + window.d);
    alert('window.e = ' + window.e);

!SLIDE

# Single var Pattern

    @@@ JavaScript
    function foo () {
      var a = 0,
        b = 1,
        c = 2;
      // ...
    }

.notes - variables declared outside any function are global (properties on
  'this', the window in a browser)
 globals pollute global namespace, chance of naming collisions
 variables that aren't declared are automatically global
 'b' is global

!SLIDE execute

# Variable Hoisting

    @@@ JavaScript
    x = 'global'

    function foo () {
      alert('x = ' + x);
      var x = 'local';
      alert('x = ' + x);
    }

    foo();

!SLIDE small execute

# Avoid Implicit Typecasting

    @@@ JavaScript
    if (false == 0) {
      alert('false == 0');
    }

    if ("" == 0) {
      alert('"" == 0');
    }

    if (false === 0) {
      alert('unreachable code');
    }

    if ("" === 0) {
      alert('unreachable code');
    }

!SLIDE execute

# Avoid eval

    @@@ JavaScript
    var obj = {},
      property = 'name';

    eval("obj." + property);

    var name = obj[property];

    var foo = new Function("alert('foo');")
    foo();

!SLIDE small bullets

# Augmenting Built-in Prototypes

* AKA Monkey-patching
* First check if function exists

!SLIDE small execute

# Native String Object Extension

    @@@ JavaScript
    if (! String.prototype.first) {
      String.prototype.first = function () {
        return this[0];
      }
    }

    var string = 'hello';

    alert(string.first());

!SLIDE small execute

# Formatting

    @@@ JavaScript
    function foo () {
      return
      {
        name: 'foo'
      }
    }

    alert(foo());

    function foo2 () {
      return {
        name: 'foo'
      }
    }

    alert(JSON.stringify(foo2()));

!SLIDE small bullets

# Naming Conventions

    @@@ JavaScript
      function UserAccount () {
        this._privateMethod = function () {};
      }

      UserAccount.MAXIMUM_AGE = 100;

      var userAccount = new UserAccount();
