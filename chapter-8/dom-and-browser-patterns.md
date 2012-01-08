!SLIDE small

# DOM Access

* Expensive
* Avoid DOM lookups in loops
* Assign DOM references to local variables
* Cache the #length when iterating over HTML collections

!SLIDE small

# Event Delegation

    @@@ JavaScript
    $("table").on("click", "td", function() {
      console.log('td clicked');
    });
