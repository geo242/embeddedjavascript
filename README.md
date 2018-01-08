# embeddedjavascript / EJS
This is a port of embeddedjavascript from [Google Code](https://code.google.com/archive/p/embeddedjavascript)

## Description
EJS is essentially a port of Masatoshi Seki's erb.rb in the Ruby Core. It operates in the same way that PHP, ERB, or any of the other embedded language interpreters work, except where all existing preprocessing engines execute on the server-side, EJS is intended to run within the web browser. This allows client-side code to process JavaScript-based web templates for insertion into the current page without consulting the server.

EJS uses `<% %>` or `[% %]` as its magic tags. Like most other frameworks of its type, `<% %>` tags cause all code within them to be executed, and the addition of an equals sign (`<%= %>`) causes the enclosed code to be evaluated and the toString representation of the result appended to the document.

## Typical Use
EJS templates can be loaded within a page or a separate file. Once the EJS template is loaded, it is passed data used to render template. The result of the render is typically used to update HTML on the page.

## Example
With this example, we will create and load a template that displays a list of cleaning supplies.

First, lets create a template file that iterates through a list of supplies:

### Supplies

Next, we create an object to hold those supplies: `var my_supplies = {supplies: ['mop', 'broom', 'duster']}`

Finally, we load the template, render it with the supply object, and update an HTML element with the results.

`var result = new EJS({url: 'templates/supplies.ejs'}).render(my_supplies); document.getElementById('supply_list').innerHTML = result`

## View Helpers
EJS includes view helpers to make building repetitive HTML snippets easier. The view helpers are very similar to Ruby on Rails ActionView helpers.

## Example
The following builds a form that adds cleaning supplies. 
`<%= form_tag('/cleaning/add_supply') %> <%= input_field_tag('cleaning_supply') %> <%= submit_tag('Submit') %> <%= form_tag_end() %>`

## Error Handling
Using a special version of JSLint, EJS can provide nice error handling when you are developing your templates. By including ejs_fulljslint similar to 

EJS will error with a line number if there is a syntax error.
