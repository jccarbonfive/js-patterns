!SLIDE bullets

# Essentials

!SLIDE smaller execute

# Globals

    @@@ JavaScript
    var a = 1;
    b = 2;

    function foo () {
      c = 2;
      var d = e = 0;
    }

    foo();

    alert('window.c = ' + window.c); // window.c = 2
    alert('window.d = ' + window.d); // window.d = undefined
    alert('window.e = ' + window.e); // window.e = 0

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
      alert('x = ' + x); // x = undefined
      var x = 'local';
      alert('x = ' + x); // x = local
    }

    foo();

!SLIDE small execute

# Implicit Typecasting

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

# eval

    @@@ JavaScript
    var obj = {},
      property = 'name';

    var name = eval("obj." + property);

    name = obj[property];

    var foo = new Function("alert('foo');")
    foo(); // foo

!SLIDE small execute

# Monkey Patching

    @@@ JavaScript
    if (! String.prototype.first) {
      String.prototype.first = function () {
        return this[0];
      }
    }

    var string = 'hello';

    alert(string.first()); // 'h'

!SLIDE small execute

# Formatting

    @@@ JavaScript
    function foo () {
      return
      {
        name: 'foo'
      };
    }

    alert(foo());  // undefined

    function foo2 () {
      return {
        name: 'foo'
      };
    }

    alert(JSON.stringify(foo2())); // {"name":"foo"}

!SLIDE smaller execute

# Cont'd

    @@@ JavaScript
    var array = [1, 2, 3, 4, 5];

    for (var i = 0; i < array.length; i++) if (array[i] > 2)
      alert(array[i]); // 3, 4, 5

!SLIDE small bullets

# Naming Conventions

    @@@ JavaScript
      function UserAccount () {
        this._privateMethod = function () {};
      }

      UserAccount.MAXIMUM_AGE = 100;

      var userAccount = new UserAccount();
