!SLIDE

# Namespaces

    @@@ JavaScript
    var MYAPP = {}
    MYAPP.Person = function () {}
    MYAPP.Company = function () {}

.notes - use namespace to reduce total number of globals and avoid polluting global namesapce
 ALL CAPS is a common convention

!SLIDE bullets incremental

# Access Control

* Every attribute and method is public
* No public, private, or protected modifiers
* Can use closures to simulate privacy

!SLIDE execute

# Privileged Method

    @@@ JavaScript
    function User (name) {
      var greeting = 'hi';
      this.hi = function () {
        alert(greeting + ' ' + name);
      };
    }

    var user = new User('foo')
    user.hi();            // hi foo
    alert(user.name);     // undefined
    alert(user.greeting); // undefined

.notes - watch returning objects from functions, would have to do a deep copy
  to prevent overwriting

!SLIDE execute

# Cont'd

    @@@ JavaScript
    var obj = {
      name: 'foo'
    };

    (function () {
      var greeting = 'hi';
      obj.hi = function () {
        alert(greeting + ' ' + this.name);
      };
    }());

    obj.hi();    // hi foo

!SLIDE bullets incremental

# Module Pattern

* Organizational pattern
* JavaScript has no packages/modules

!SLIDE small execute

# Cont'd

    @@@ JavaScript
    MYAPP = {};
    MYAPP.Person = (function () {
      var name = 'foo';
      return function () {
        this.hi = function () {
          alert(name);
        };
      };
    }());

    var person = new MYAPP.Person();
    person.hi(); // foo


!SLIDE small execute

# Cont'd

    @@@ JavaScript
    MYAPP = {};
    (function (global) {
      var name = 'foo';
      global.MYAPP.Person = function () {
        this.hi = function () {
          alert(name);
        };
      };
    }(window));

    var person = new MYAPP.Person();
    person.hi(); // foo

!SLIDE

# Chaining Pattern

    @@@ JavaScript
    $("#menu")
       .fadeIn('fast')
       .addClass("active")
       .css('marginRight', '10px');
