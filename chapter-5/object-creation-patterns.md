!SLIDE

# Namespaces

    @@@ JavaScript
    var MYAPP = {}
    MYAPP.Person = function () {}
    MYAPP.Company = function () {}

.notes - use namespace to reduce total number of globals and avoid polluting global namesapce
 ALL CAPS is a common convention

!SLIDE bullets

# Access Control

* Every attribute and function is public
* No public, private, or protected modifiers
* Can use closures to simulate privacy

!SLIDE execute

# Private method

    @@@ JavaScript
    function User () {
      var name = 'foo';
      this.hi = function () {
        alert(name);
      };
    }

    var user = new User()
    user.hi();
    alert(user.name);

.notes - watch returning objects from functions, would have to do a deep copy
  to prevent overwriting

!SLIDE bullets

# Module Pattern

* Organizational pattrn
* JavaScript has no packages/modules

!SLIDE small execute

# Module Pattern

    @@@ JavaScript
    MYAPP = {};
    MYAPP.Person = (function () {
      var name = 'foo';
      var fn = function () {
        this.name = name;
        this.hi = function () {
          alert(this.name);
        };
      };
      return fn;
    }());

    var person = new MYAPP.Person();
    person.hi();


!SLIDE small execute

# Module Pattern

    @@@ JavaScript
    MYAPP = {};
    (function (global) {
      var name = 'foo';
      global.MYAPP.Person = function () {
        this.name = name;
        this.hi = function () {
          alert(this.name);
        };
      };
    }(window));

    var person = new MYAPP.Person();
    person.hi();
