
Notes from official documentation (https://api.jquery.com/) 


**jQuery()

  Return a collection of matched elements either found in the DOM based on passed argument(s) or created by passing an HTML string.

  jQuery( selector [, context ] )
  
  -- Description
  
  Accepts a string containing a CSS selector which is then used to match a set of elements
  
  -- selector
  
  Type: Selector
  A string containing a selector expression
  
  -- context
  Type: Element or jQuery or Selector
  A DOM Element, Document, jQuery or selector to use as context
  
  ## Example 1
  
  In the first formulation listed above, jQuery() — which can also be written as $() — searches through the DOM for any elements that match the provided selector and creates a new jQuery object that references these elements:
  
  $( "div.foo" );
  
  If no elements match the provided selector, the new jQuery object is "empty"; that is, it contains no elements and has .length property of 0.
  
  ## Example 2: selector context
  
  By default, selectors perform their searches within the DOM starting at the document root. However, an alternate context can be given for the search by using the optional second parameter to the $() function. For example, to do a search within an event handler, the search can be restricted like so:
  
  $( "div.foo" ).click(function() {
  $( "span", this ).addClass( "bar" );
  });
  
  When the search for the span selector is restricted to the context of this, only spans within the clicked element will get the additional class.

  Internally, selector context is implemented with the .find() method, so $( "span", this ) is equivalent to $( this ).find( "span" ).

  
  
  

  
  
