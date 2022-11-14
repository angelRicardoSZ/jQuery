
Notes from the book, jQuery in action (https://www.manning.com/books/jquery-in-action-third-edition)

chapter 2

**Selecting elements with jQuery by using CSS selectors

2.2 Basic selectors
  
example                | Description                                                      | in CSS
-----------------------|------------------------------------------------------------------|------------
"*"                    |     Matches all the elements in the page                         | yes
"#special-id"          | Matches the element with the ID value of special-id              | yes
"a"                    | Matches all anchor (a) elements                                  | yes
"a.special-class"      | Matches all anchor (a) elements that have the class special-class | yes
".class.special-class" | Matches all elements with the class class and class special-class | yes


** Discovering the unique jQuery-only filters

** Developing custom filters

** Learning the context parameter of the jQuery() function


2.2.1 the all (or Universal) selector
"*" => Allows you to retrieve all of the DOM elements of a web page, even the head element and its children

example: 
html file
<!DOCTYPE html>
<html>
   <head>
      <meta charset="utf-8" />
      <title>jQuery in Action, 3rd edition</title>
   </head>
   <body>
      <p>I'm a paragraph</p>
      <!-- <script src="//code.jquery.com/jquery-1.11.3.min.js"></script> -->
      <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
      <script>
         window.jQuery || document.write('<script src="../js/jquery-1.11.3.min.js"><\/script>');
         var $allElements = $('*');
      </script>
   </body>
</html>

     
console.log($allElements);
     
output>>   S.fn.init(8) [html, head, meta, title, body, p, script, script, prevObject: S.fn.init(1)]
     
     
2.2.2 The ID selector
     
     $('#id');   => When used with the ID selector, jQuery returns a collection of either zero or one DOM
                    element. In case you have more than one element on a page with the same ID, the
                    library retrieves only the first matched element encountered
     
2.2.3 The Class selector
     
    var $descriptions = $('.description');   =>  jQuery follows the CSS conventions, so you have to prepend a dot before the chosen class name
     
     example
     
     <body>
       <div>
       <h1 class="green">A title</h1>
       <p class="description">I'm a paragraph</p>
      www.it-ebooks.info
      Basic selectors 31
      </div>
      <div>
       <h1 class="green">Another title</h1>
       <p class="description blue">I'm yet another paragraph</p>
      </div>
     </body>
     
     var $descriptions = $('.description');
     
     
     console.log($descriptions)
     
     output>> S.fn.init(2) [p.description, p.description.blue, prevObject: S.fn.init(1)]
     
     The result of this statement is an object, often referred to by the documentation as
      a jQuery object or a jQuery collection (other names you can find in the wild are set of
      matched elements, or simply set or collection) containing the two paragraphs of the HTML
      snippet. The library will also select the nodes having multiple classes where one of
      them matches the given name (like the second paragraph).
     
     
     
  2.2.4 The Element selector
     
     The Element selector allows you to pick up elements based on their tag name. Because of its support in almost any browser (including IE6), jQuery uses get-
     ElementsByTagName() to select elements by tag name behind the scenes.
     
    Example

       If say you want all the <div>s in a page

       var $divs = $('div');
      
       if you want all <div>s having class clearfix
     
       var $clearfixDivs = $('div.clearfix');
     
     
     2.3 Retrieving elements by their hierarchy
     
     Sometimes you may want to select only the direct chil-dren of a certain element.
     
     Example
     
     
     Suppose that you wanted to select the a element pointing to the jQuery website but not those to various local pages describing the different CSS   specifications.
   
    html 
     
      <ul class="my-list">
      <li>
      <a href="http://jquery.com">jQuery supports</a>
      <ul>
      <li><a href="css1">CSS1</a></li>
      <li><a href="css2">CSS2</a></li>
      <li><a href="css3">CSS3</a></li>
      <li>Basic XPath</li>
      </ul>
      </li>
      <li>jQuery also supports
      <ul>
      <li>Custom selectors</li>
      <li>Form selectors</li>
      </ul>
      </li>
      </ul> 
     
    selector: ul.my-list > li > a
     
    2.4 Selecting elements using attributes
     
     Attribute selectors are extremely powerful and allow you to select elements based on their attributes. You can easily recognize these selectors because they’re wrapped with square brackets (for example, [selector]).
     
     Example
     
     <ul>
    <li>
    <a href="http://jquery.com">jQuery supports</a>
    <ul>
    <li><a href="css1">CSS1</a></li>
    <li><a href="css2">CSS2</a></li>
    <li><a href="css3">CSS3</a></li>
    <li>Basic XPath</li>
    </ul>
    </li>
    </ul>
     
    selector: a[href^='http://']
     
     
     
     
     
     
     
     

