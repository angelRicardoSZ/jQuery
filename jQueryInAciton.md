
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
     
     
 2.5 Introducing filters
     
     
   2.5.1 Position filters
     
     This format of selector matches the first <a> on the page.
     
     a:first 
     
     
     
     Table 2.4 The position filters supported by jQuery
     
     Selector             |          Description                                                              
     -----------------------------------------------------------------------------------------------------------------------------------------------------
     :first               |       Selects the first match within the context. li a:first returns the first anchor that’s a descendant of a list item.
     -----------------------------------------------------------------------------------------------------------------------------------------------------
     :last                |       Selects the last match within the context. li a:last returns the last anchor that’s a descendant of a list item.
     -----------------------------------------------------------------------------------------------------------------------------------------------------
     :even                |       Selects even elements within the context. li:even returns every even-indexed list item.
     -----------------------------------------------------------------------------------------------------------------------------------------------------
     :eq(n)               |     Selects the nth matching element.
     -----------------------------------------------------------------------------------------------------------------------------------------------------
     
     
     
     
     
   2.5.2 Child filters
     
     Example 1:
     
     the last <li> child of each <ul> element is matched.
     
     ul li:last-child
     
     Example 2: 
     
     All <p>s inside a <div> that are the fourth child of their parent element.
     
     div p:nth-child(4)  
     
     Table 2.5 The Child filters of jQuery
     
     Selector          |           Description                                               |  In CSS?
    -----------------------------------------------------------------------------------------------------------------------------------------------------
     :first-child      |  Matches the first child element within the context                 |  yes
     -----------------------------------------------------------------------------------------------------------------------------------------------------
     :first-of-type    |  Matches the first child element of the given type                  |  yes
     -----------------------------------------------------------------------------------------------------------------------------------------------------
     :nth-child(n)     |  Matches the nth child element, even or odd child                   |  yes
     :nth-child(even|odd)  |  elements, or nth child element computed by the                 |  yes
     :nth-child(Xn+Y)  |  supplied formula within the context based on the                   |  yes
                       |  given parameter                                                    |
     
     Example 3: 
     
     <table id="languages">
    <thead>
    <tr>
    <th>Language</th>
    <th>Type</th>
    <th>Invented</th>
    </tr>
      </thead>
    <tbody>
    <tr>
    <td>Java</td>
    <td>Static</td>
    <td>1995</td>
    </tr>
    <tr>
    <td>Ruby</td>
    <td>Dynamic</td>
    <td>1993</td>
    </tr>
    <tr>
    <td>Smalltalk</td>
    <td>Dynamic</td>
    <td>1972</td>
    </tr>
    <tr>
    <td>C++</td>
    <td>Static</td>
    <td>1983</td>
    </tr>
    </tbody>
    </table>
     
     All of the table cells that contain the names of programming languages.
     
        #languages td:first-child or #languages td:nth-child(1)
     
     The name of the languages and their year of creation using :nth-child().
     
        #languages td:nth-child(odd)
      
     
 2.5.3 Form filters
     
     You might want to match all check boxes that are in a checked state. You might be tempted to try something along these lines:
     
      $('input[type="checkbox"][checked]');
     
     What you really want to check is the real-time state of the

      controls. CSS offers a pseudo-class, :checked, that matches elements that are in a checked state. For example, whereas the input[type="checkbox"] selector selects all input elements that are check boxes, the input[type="checkbox"]:checked selector narrows the search to only input elements that are check boxes and are currently checked.
     
     When rewriting your previous statement to select all the check boxes that are currently checked using the filter, you can write
     
      $('input[type="checkbox"]:checked');
     
     jQuery also provides a handful of powerful custom filter selectors, not specified by CSS, that make identifying target elements even easier. For example, the custom :checkbox selector identifies all check box elements. Combining these custom selec- tors can be powerful and shrink your selectors even more. Consider rewriting once again our example using filters only:
     
        $('input:checkbox:checked');
     
     Table 2.6   The CSS and custom jQuery filter selectors
     
     Selector       |                       Description                                                                                          |  In CSS?
     ------------------------------------------------------------------------------------------------------------------------------------------------------
     :button        |     Selects only button elements (input[type=submit], input[type=reset], input[type=button], or button)                    |  no
     -------------------------------------------------------------------------------------------------------------------------------------------------------
     :checkbox      |    Selects only check box elements (input[type=checkbox])                                                                  |  no
     -------------------------------------------------------------------------------------------------------------------------------------------------------
     :checked       |     Selects check boxes or radio elements in the checked state or options of select elements that are in a selected state  |  yes
     -------------------------------------------------------------------------------------------------------------------------------------------------------
      :disabled      |      Selects only elements in the disabled state                                                                          |  yes     
     -------------------------------------------------------------------------------------------------------------------------------------------------------
     
     For example, if you want to select only enabled and checked check boxes, you could use
     
        $('input:checkbox:checked:enabled');
  
     
     
     
     
     
     
     
     
     
     
     
     
     

