# jQuery



## ![jQuery](http://jquery.com/jquery-wp-content/themes/jquery/images/logo-jquery@2x.png)



## What is jQuery?

> It makes things like HTML document(DOM) traversal, manipulation, event handling, animation, and Ajax much simpler with an easy-to-use API that works across a multitude of browsers.


## Browser Support

http://jquery.com/browser-support/


## DOM (Document Object Model)

https://developer.mozilla.org/zh-TW/docs/Web/API/Document_Object_Model



## A Brief Look


### DOM Traversal and Manipulation

```
    $('button.continue').html('Next Step...')
```

### Event Handling

```
    var hiddenBox = $('#banner-message');
    $('#button-container button').on('click', function(event) {
        hiddenBox.show();
    });
```

### Ajax

```
    $.ajax({
        url: '/api/getWeather',
        data: {
            zipcode: 97201
        },
        success: function(result) {
            $('#weather-temp').html('<strong>' + result + '</strong> degrees');
        }
    });
```



## Selectors


## jQuery object

### $() or jQuery()


## Basic CSS Selectors

### selecting elements by id

```
    $('#main')
```

### selecting elements by class

```
    $('.container')
```

### selecting elements by tag

```
    $('form')
```

### selecting elements by attribute

```
    $('[name="email"]')
```


## Basic, Child, Content Filter Selectors

### basic filter

```
    :first, :last, :eq(), :odd, :even, :not(), :gt(), :lt()
```

### child filter

```
    :first-child, :last-child, :nth-child()
```

### content filter

```
    :empty, :parent, :has(), :contains()
```


## Form Selectors & Visibility filter Selectors

### form selector

```
    :checked, :disabled, :enabled, :selected, :focus
```

```
    :input, :text, :password, :checkbox, :radio, :file, :reset, :submit, :button
```

### visibility filter selector

```
    :hidden, :visible
```



## Traversing


```
    .first(), .last(), .eq(), .is(), .not(), .has()
```

```
    .filter(), .each(), .map(), .slice()
```

```
    .children(), .parents(), .siblings(), .next(), .prev(), .find()
```



## Manipulation


## Class Attribute

```
    .addClass(), .removeClass(), .toggleClass(), .hasClass()
```


## DOM Insertion, Inside

```
    .html(), .text(), .append(), appendTo(), .prepend(), prependTo()
```


## DOM Removal

```
    .remove(), .empty(), .detach()
```


## General Attributes

```
    .attr(), .removeAttr(), .prop(), .removeProp(), .val()
```


## Style Properties

```
    .css(), .width(), .height()
```



## Events


## Browser Events

```
    .resize(), .scroll()
```


## Document Loading

```
    .ready()
```


## Event Handler Attachment

```
    .on(), .off(), .one(), .trigger()
```


## Form Events

```
    .submit(), .focus(), .change(), .select(), .blur()
```


## Keyboard Events

```
    .keydown(), .keypress(), .keyup()
```


## Mouse Events

```
    .click(), .hover(), .dblclick()
```

```
    .mousedown(), .mouseenter(), .mouseleave(), .mousemove(), .mouseout(), .mouseover(), .mouseup()
```



## Effects


## Basics

```
    .show(), .hide(), .toggle()
```


## Fading

```
    .fadeIn(), .fadeOut(), .fadeToggle(), .fadeTo()
```


## Sliding

```
    .slideDown(), .slideUp(), .slideToggle()
```


## Custom

```
    .animate()
```



## Ajax

```
    $.ajax(), $.get(), $.post(), $.load(), $.getJSON(), $.getScript()
```



## Utilities

```
    $.each(), $.extend(), $.inArray(), $.map(), $.merge(), $.trim()
```

```
    $.isArray(), $.isFunction(), $.isNumeric()
```



## Launching Code on Document Ready


### X

```
    window.onload = function() {
        // Your code here.
    };
```


### O

```
    $(function() {
        // Your code here.
    });
```

```
    $(document).ready(function() {
        // Your code here.
    });
```



## Callbacks


## Callback without Arguments

```
    $.get('myhtmlpage.html', callback);
```


## Callback with Arguments

### X

```
    $.get('myhtmlpage.html', callback(param1, param2));
```

### O

```
    $.get('myhtmlpage.html', function() {
        callback(param1, param2);
    });
```



## jQuery utility-type methods vs jQuery object methods

### $.each() vs .each()



## Choosing Selectors


> Choosing good selectors is one way to improve JavaScript's performance. Too much specificity can be a bad thing.



## Does The Selection Contain Any Elements?


### X

> an object is always returned

```
    if ($('div.foo')) {
        ....
    }
```

### O

```
    if ($('div.foo').length) {
        ....
    }
```



## Saving Selections


> A selection only fetches the elements that are on the page at the time the selection is made. If elements are added to the page later, you'll have to repeat the selection or otherwise add them to the selection stored in the variable. Stored selections don't magically update when the DOM changes.

```
    var divs = $('div');
    var $divs = $('div');
```



## Getters & Setters


> Setters affect all elements in a selection, whereas getters return the requested value only for the first element in the selection, with the exception of .text(), which retrieves the values of all the elements.



## Chaining


> If you call a method on a selection and that method returns a jQuery object, you can continue to call jQuery methods on the object without pausing for a semicolon.


> Setters return a jQuery object, allowing you to continue calling jQuery methods on your selection. Getters return whatever they were asked to get, so you can't continue to call jQuery methods on the value returned by the getter.



## Creating New Elements


```
    $('<p>This is a new paragraph</p>');
    $('<li class=\"new\">new list item</li>');
```


```
    $('<a></a>', {
        html: 'This is a <strong>new</strong> link',
        'class': 'new',
        href: 'foo.html'
    });
```


## Reserved keywords in JavaScript

https://mathiasbynens.be/notes/reserved-keywords



## Manipulating Attributes


## Manipulating a single attribute

```
    $('#myDiv a:first').attr('href', 'newDestination.html');
```


## Manipulating multiple attributes

```
    $('#myDiv a:first').attr({
        href: 'newDestination.html',
        rel: 'nofollow'
    });
```



## The Object Literal


```
    var myFeature = {
        myProperty: 'hello',
        myMethod: function() {
            console.log(myFeature.myProperty);
        },
        init: function(settings) {
            myFeature.settings = settings;
        },
        readSettings: function() {
            console.log(myFeature.settings);
        }
    };
```



## The Module Pattern


```
    var feature = (function() {
        var privateThing = 'secret';

        var publicThing = 'not secret';

        var changePrivateThing = function() {
            privateThing = 'super secret';
        };

        var sayPrivateThing = function() {
            console.log(privateThing);
            changePrivateThing();
        };

        // Public API
        return {
            publicThing: publicThing,
            sayPrivateThing: sayPrivateThing
        };
    })();
    feature.publicThing;
    feature.sayPrivateThing();
```



## $.noConflict()


```
    $.noConflict();
    $j = $.noConflict();
```



## Deprecated or Removed


http://api.jquery.com/category/deprecated/

http://api.jquery.com/category/removed/



## Other Resources


## jQuery UI

http://jqueryui.com/


## jQuery Mobile

http://jquerymobile.com/



## Demo



## Homework

> pick up one from the below two, details at each repo readme.

* jquery diary
https://github.com/chenjenping/jquery_diary

* jquery tale
https://github.com/chenjenping/jquery_tale



## Thanks for Listening
