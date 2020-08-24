# Web with Python questions

## Software design

### Clean code

#### Point out 5 suggestions, how to format an SQL query!
	>Indentation helps keep your query clean by identifying where each block of code begins.
 This makes program structure more understandable.
 
 	>Explain Yourself with Comments.
 
 	>It is also very important to use a single naming convention for tables, 		columns, and queries.
  	This makes the code easier to write and read.
  
	>Define SELECT Fields instead of SELECT *
	
	>Use WHERE instead of HAVING to Define Filters:
	>>Per the SQL Order of Operations, HAVING statements are calculated after WHERE statements. 
If the intent is to filter a query based on conditions, a WHERE statement is more efficient.

#### What layers can you name in a simple web application?
1. The View Layer. (It can be called view, presentation, UI. In this layer the application shows to the user what is needed to be seen and gives the tools for interaction.)
2. The Business Logic Layer (The central layer of the model deals with the logic of the program. It receives data from the upper level and transforms it, using in the inner application logics. It also retrieves data from the deepest data level and uses it to the logics. And, by integrating these two processes, it can do modifications in both levels as well.)
3. The Data Layer (The deepest level in the layered architecture, the data layer deals with data retrieval from its sources. It is an abstraction to get the plain data, that can be in a wide variety of forms.)

### Error handling
#### What error can occur, when an array does not have an element on the requested index?
IndexError - use try/except to avoid, or an expression
#### What is the “finally” block, and how would you use it?
>The finally block is as the name implies,
 some code that you want to execute regardless of what happens.
>>A classic example of try…catch…finally is database resource management.
#### Why should we catch special exception types?
>Nothing is worse than an application crashing with some user unfriendly stacktrace dumped to the screen.
 >>Not only does it give (perhaps unwanted) insight into your code,
     but it also confuses your end-user, and sometimes even scares them away to a competing application.
### Security
#### What is SQL injection? How to protect an application against it?
>An SQL injection is a computer attack in which malicious code is embedded in a poorly-designed application
 and then passed to the backend database
>>You can prevent SQL Injection vulnerabilities in web applications by utilizing parameterized
database queries with bound, typed parameters and careful use of parameterized stored procedures in the database.
>>>Before substitute into query, we need to do the validation. for remove ir escaped the special character like single quote, key words like select, Union…
>>>>Don’t use normal query, use Named query like this
#### What is XSS? How to protect an application against it?
    Cross-site Scripting (XSS)
>Cross-site Scripting (XSS) is a client-side code injection attack. The attacker aims to execute malicious scripts in a web browser of the victim
by including malicious code in a legitimate web page or web application.
>>commonly used for Cross-site Scripting attacks are forums, message boards, and web pages that allow comments.
    
    To protect:
>To protect against stored XSS attacks, make sure any dynamic content coming from the data store cannot be used
 to inject JavaScript on a page.
 >> - Whitelist Values
 
 >> - HTTP-only Cookies : meaning that cookies will be received, stored, and sent by the browser, but cannot be modified or read by JavaScript.
#### How to properly store passwords?
>First of all you have to hash the password and store data information like that in the database.
>>Secondly you need a good encrypt algorithm for that process.
>>>Finally the best practise the you storing your database a specific local storage.(etc.)
#### What is HTTPS?
>Hypertext Transfer Protocol Secure (HTTPS) is an extension of the Hypertext Transfer Protocol (HTTP).
 It is used for secure communication over a computer network, and is widely used on the Internet
>>It protects against man-in-the-middle attacks. 
#### What is encryption and decryption?
>Encryption is the process of translating plain text data (plaintext) into something that appears to be random and meaningless (ciphertext).
>>Decryption is the process of converting ciphertext back to plaintext.
#### What is hashing?
>A hash function is where a computer takes an input of any length and content (e.g. letters, numbers, and symbols) and
 uses a mathematical formula to chop it, mix it up, and produce an output of a specific length. 
#### What is the difference between encryption and hashing? When would you use which?
>The key difference between encryption and hashing is that encrypted strings can be reversed back into their original
 decrypted form if you have the right key.
 
    Hashing:
    Hashing is an ideal way to store passwords,
    as hashes are inherently one-way in their nature.
    + salt
    
    Encryption:
    Encryption should only ever be used over hashing when
     it is a necessity to decrypt the resulting message.
     for example: send a secure messages to someone on the other side of the world 

#### What encryption methods do you know?
Symmetric encryption
   using the same key for encryption and decryption
   problem: since internet is open this can't  be shared


Asymmetric encryption
   both parties have a public and a private key
   the encrypt with the other's public key and they can decrypt with their own private key


Double encryption
   1) encrypt with your own private key (this ensures that you sent the message)
   2) encrypt with other's public key (this ensure that only they can read it)


Most times symmetric encryption is used for communicating, as it is much faster than asymmetric. The latter is mainly used for sharing the symmetric key at the beginning of the communication.




Advanced Encryption Standard (AES):
   symmetric algorithm
   encrypts 128 bit data segments
   puts plain text through a number of transformations determined by the key size


RSA:
   asymmetric algorithm
   based on factorization of the product of two large prime numbers


ECC (Elliptic Curve Cryptography):
   relies on the algebraic structure of elliptic curves over finite fields
#### What hashing methods do you know?
Message Digest 5 (MD5) - This is a widely used cryptographic hash function that produces a 128-bit (16-byte) hash value. It is not recommended now.
Secure Hash Algorithm (SHA) - SHA algorithms are structured differently. There are three of them: SHA-0, SHA-1, and SHA-2. SHA-2 is used by the NSA for example.
Cyclic redundancy check (CRC) - This is an error-detecting code. Although commonly used in digital networks and storage devices to detect accidental changes to raw data, it is a hash method.

#### How/where would you store sensitive data (like db password, API key, ...) of your application?
How/where would you store sensitive data (like db password, API key, ...) of your application?
- Store sensitive data in environment variables
 - key/value pair
 - pycharm path: Run > Edit Configurations > Environment row > Icon
 - terminal: 
   - to create: export EDITOR=nano
   - to see value of variable: printenv EDITOR
   - to delete: unset EDITOR


must never be placed in VCS
## Computer science

### Algorithms

#### What is the difference between Stack and Queue data structure?
What is the difference between Stack and Queue data structure?
A stack is a linear data structure in which elements can be inserted and deleted only from the top. It uses the LIFO (Last In First Out) principle.
A queue is a linear data structure in which elements can be inserted only from the rear, and the elements can be deleted only from the front side. It follows the FIFO (First In First Out) principle.
#### What is BubbleSort? Describe the main logic of this sorting algorithm.
BubbleSort is a sorting method that repeatedly loops over a list switching the two adjacent numbers to be in the correct order.
This loop continues until the all adjacent numbers are in order


<li>Bubble Sort is the simplest sorting algorithm that works by repeatedly swapping the adjacent elements if they are in wrong order.


for i in range(n):
       for j in range(n-i):
           if myList[j] > myList[j+1]:
               container = myList[j]
               myList[j] = myList[j+1]
               myList[j+1] = container
#### Explain the process of finding the maximum and minimum value in a list of numbers!
<li>METHOD 1 (Simple Linear Search)
Initialize values of min and max as minimum and maximum of the first two elements respectively. Starting from 3rd, compare each element with max and min, and change max and min accordingly (i.e., if the element is smaller than min then change min, else if the element is greater than max then change max, else ignore the element)
<li>METHOD 2 (Tournament Method)
Divide the array into two parts and compare the maximums and minimums of the two parts to get the maximum and the minimum of the whole array.
#### Explain the process of calculating the average value in an array of numbers!
<li>Iterative:
Iterative program is easy. We need to find sum and divide sum by total number of elements.


   def average( a , n ):
   sum = 0
   for i in range(n):
       sum += a[i]
   return sum/n;
   arr = [10, 2, 3, 4, 5, 6, 7, 8, 9]
   n = len(arr)
   print(average(arr, n))
<li>Recursive:
The idea is to pass index of element as an additional parameter and recursively compute sum. After computing sum, divide the sum by n.
   def avgRec( a , i , n ):  
   if i == n-1:
       return a[i]
   if i == 0:
       return ((a[i] + avgRec(a, i+1, n)) / n)
   return (a[i] + avgRec(a, i+1, n)
   def average(a, n):
       return avgRec(a, 0, n)
   arr = [10, 2, 3, 4, 5, 6, 7, 8, 9]
   n = len(arr)
   print(average(arr, n))
#### What is Big O complexity? Explain time and space complexity!
 It is how we compare the efficiency of different approaches to a problem.
- how quickly the runtime grows : use Big O Notation to talk about how quickly the runtime grows.

- relative to the input :  With Big O Notation, we use the size of the input, which we call “n”. So we can say things like the runtime grows “on the order of the size of the input” (O(n))
 or “on the order of the square of the size of the input” (O(n²)).


- as the input gets larger : we care more about the stuff that grows fastest as the input grows,
 because everything else is quickly eclipsed as n gets very large.

#### Explain the process of calculating the average value in a list of numbers!
sum all of the data values and divide by the number of nodes in the list.

### Procedural
#### How the CASE condition works in SQL?
>The CASE statement goes through conditions and returns a value when the first condition is met.

>>So, once a condition is true, it will stop reading and return the result. If no conditions are true, it returns the value in the ELSE clause.

#### How the switch-case condition works in JavaScript?
>The switch statement is used to perform different actions based on different conditions.

>>Use the switch statement to select one of many code blocks to be executed.


#### How to achieve a switch-case-like structure in Python?
Use a dictionary or a complex if-elif-else structure. First is the recommended.
Syntax for dictionary solution is below. You can use function names as values
def switch_demo(argument):
    switcher = {
        1: "First",
        2: "Second",
        3: "Third"
    }
    switcher.get(argument, "Invalid data")
#### Explain variable scoping in Python!
A variable created inside a function belongs to the local scope of that function, and can only be used inside that function.
A variable created in the main body of the Python code is a global variable and belongs to the global scope.
Global variables are available from within any scope, global and local.


L - local - defined inside function/class
E - enclosed - Defined inside enclosing functions(Nested function concept)
G - global - defined at the uppermost level
B - built-in - reserved names in Python builtin modules
          
           x = 0


           def outer():
               x = 1
               def inner():
                   x = 2
                   print("inner:", x)
               inner()
               print("outer:", x)


           outer()
           print("global:", x)


           prints:
           inner: 2
           outer: 1
           global: 0
#### What’s the difference between const and var in JavaScript?
>The const keyword creates a declaration that cannot be reassigned.

#### How the list comprehension looks like in Python?
 list_of_numbers = [number for number in range(0, 10, 2)]
#### How the “ternary expression” looks like in Python?
Ternary operators also known as conditional expressions are operators that evaluate something based on a condition being true or false.
It simply allows to test a condition in a single line replacing the multiline if-else making the code compact.


   [on_true] if [expression] else [on_false]
   True if x = 0 else False


-  a, b = 10, 20 
  min = a if a < b else b
- tuple((if_test_false, if_test_true)[test]) -> (b, a) [a < b]

#### How the ternary expression looks like in JavaScript?
The conditional (ternary) operator is the only JavaScript operator that takes three operands:
a condition followed by a question mark (?),
then an expression to execute if the condition is truthy followed by a colon (:),
and finally the expression to execute if the condition is falsy.
This operator is frequently used as a shortcut for the if statement.


<li>You can use the ternary operator as the shortcut for the if-else statement.
   <ul>Syntax</ul>
      
       condition ? expression_1 : expression_2;


- condition ? doThisIfTrue : doThisIfFalse
#### How to import a function from another module in Python?
    • from module_name import function_name
    •    import module_name (call as module_name.function_name)
    •    from module_name import * (call as function_name)
#### How to import a function from another module in JavaScript?
<li>The static import statement is used to import read only live bindings which are exported by another module. Imported modules are in strict mode whether you declare them as such or not. The import statement cannot be used in embedded scripts unless such script has a type="module". Bindings imported are called live bindings because they are updated by the module that exported the binding.


There is also a function-like dynamic import(), which does not require scripts of type="module".


   import defaultExport from "module-name";
   import * as name from "module-name";
   import { export1 } from "module-name";
   import { export1 as alias1 } from "module-name";
   import { export1 , export2 } from "module-name";
   import { foo , bar } from "module-name/path/to/specific/un-exported/file";
   import { export1 , export2 as alias2 , [...] } from "module-name";
   import defaultExport, { export1 [ , [...] ] } from "module-name";
   import defaultExport, * as name from "module-name";
   import "module-name";
   var promise = import("module-name");

### Functional
#### What is recursion?
- A recursive function is a function that calls itself until a “base condition” is true, and execution stops.
- While false, we will keep placing execution contexts on top of the stack. 
This may happen until we have a “stack overflow”. 
A stack overflow is when we run out of memory to hold items in the stack.

#### Write a recursive function which calculates the Fibonacci numbers!
def fibonacci(n):
    if n == 0:
        return 0
    elif n == 1:
        return 1
    else:
        return fibonacci(n - 1) + fibonacci(n - 2)
How to store a function in a variable in Python?
def apple_writer():
    return 'apple'

#### How to store a function in a variable in Python?
def apple_writer():
    return 'apple'


peach = apple_writer
#### List the ways of defining a callable logical unit in JavaScript!
Functions are values. They can be assigned, copied or declared in any place of the code. If the function is declared as a separate statement in the main code flow, that’s called a “Function Declaration”. If the function is created as a part of an expression, it’s called a “Function Expression”. Function Declarations are processed before the code block is executed. They are visible everywhere in the block. Function Expressions are created when the execution flow reaches them.
* Function Declaration
function showMessage() {
  alert( 'Hello everyone!' );
}


* Function Expression
let sayHi = function() {
  alert( "Hello" );
};


* Arrow Functions
let sum = (a, b) => a + b;
#### What is an event listener? How to attach one?
The EventListener interface represents an object that can handle an event dispatched by an EventTarget object. An HTML event can be something the browser does, or something a user does. When the specified event occurs, the listener calls a function or object.
Syntax:
element.addEventListener(event, function, useCapture);
(useCapture parameter is optional - event bubbling or event capturing)
We can attach an event listener to a certain DOM-element as follows:


   const emailInput = document.querySelector('#email');
   emailInput.addEventListener('input', checkForValidInput);


   function checkForValidInput() {
       ...
   }
- An event listener attaches an event handler to the specified element
- You call the element you want to add an event listener to and attach the .addEventListener() method, 
document.getElementById("myBtn").addEventListener("click", displayDate);
#### How to trigger an event in JavaScript?
- There are many ways, but a few of them, click, mouseover, keyup, keydown
let winEvent = new CustomEvent('win', {bubbles: true, cancelable: true})
 window.dispatchEvent(winEvent)

#### What is a callback function? Tell some examples of its usage.
emailInput.addEventListener('input', checkForValidInput);


setTimeout((() => alert('Time is up!')), 1000)


...
.then(response => response.json())
 .then(json_response => callback(json_response))


A callback function is any executable code that is passed as an argument to other code that is expected to call back (execute) the argument at a given time.
This execution maybe synchronous or asynchronous.
Event listeners have a callback function, promises have call back functions,setTimeout(), and fetch().
This all needs a callback function that is called when the event is triggered, the promise is completed, or the fetch has been completed.
***
- a callback, also known as a "call-after" function, is any executable code that is passed as an argument to other code; that other code is expected to call back (execute) the argument at a given time. This execution may be immediate as in a synchronous callback, or it might happen at a later time as in an asynchronous callback. 
--authentication on remote server
-  function greeting(name) { 
    alert('Hello ' + name); 
  } 
  function processUserInput(callback) { 
    var name = prompt('Please enter your name.'); 
    callback(name); 
  }
  processUserInput(greeting);

#### What is a Python decorator? How does it work? Tell some examples of its usage.
Decorator functions allow us to wrap another function to extend the behavior of wrapped function, without permanently modifying it.
Functions are taken as arguments into another function and then called inside the (wrapper) function.
Example:
def hello_decorator(func): 
    def inner1(): 
        print("Hello, this is before function execution") 
        func() 
        print("This is after function execution") 
    return inner1 


def function_to_be_used(): 
    print("This is inside the function !!") 


function_to_be_used = hello_decorator(function_to_be_used) 
function_to_be_used()


   @app.route: to match endpoints with Python functions
   @lru_cache: to store function return values in a cache memory
   to create connection and execute a query on a database and close it afterwards
   measuring time it takes the function to run
   to convert the return value of a function to json format
   to check if the user is logged in and if not redirect them to the login page

#### What is the difference between synchronous and asynchronous execution?

When you execute something synchronously, you wait for it to finish before moving on to another task
. When you execute something asynchronously, you can move on to another task before it finishes.




- Synchronous basically means that you can only execute one thing at a time
- Asynchronous means that you can execute multiple things at a time and you 
don't have to finish executing the current thing in order to move on to the next one.

## Programming languages

### SQL

#### How can you connect your application to a database server? What are the possible ways?
- First we create the sql file we want to insert into the database
- Then we type in the terminal 'psql' to enter the sql part
- After that we create a database, 'CREATE DATABASE series;'
- Then we connect to the db, '\connect series'
- Then we insert the file we created at the start into the DB, '\i data/data_inserter.py'
- After that we set up a data connection file in our application, 
this will get the environment variables we type in to set up a connection
- And we have to connect to the new database with our IDE as well

#### When do you use the DISTINCT keyword in SQL?
When you wish to filter out duplicates from the values. For example there are students’ addresses, and you would like to get a list (actually a set, cause it will have no duplicates) of the cities where students are from.


The distinct clause also treats NULL as a value so if you have multiple NULL values this will only appear once.
#### Talk about the behavior/goal of these base SQL clauses: WHERE, GROUP BY, HAVING, ORDER BY?
li>WHERE clause allows filtering certain records that exactly match a specified condition. It helps us to fetch only the necessary data from the database that satisfies the given expressional conditions. The WHERE clause is used with SELECT statement as well as with UPDATE, DELETE type statements and aggregate functions to restrict the no. of records to be retrieved by the table.
<li>ORDER BY clause is used in SQL for sorting records. It is used to arrange the result set either in ascending or descending order. When we query using SELECT statement the result is not in an ordered form. Hence, the result rows can be sorted when we combine the SELECT statement with the ORDER BY clause.
<li>GROUP BY clause is used to group rows that have the same values in the result set. This clause is generally used with aggregate functions that allow grouping the query result rows by multiple columns. The aggregate functions are COUNT, MAX, MIN, SUM, AVG, etc.
<li>Actually, this clause is introduced to apply functions in the query with the WHERE clause. In SQL, the HAVING clause was added because the WHERE clause could not be applied with aggregate functions.

#### What are aggregate functions in SQL? Give 3 examples.
They are functions that generate (aggregate) a single value out of multiple rows’ values. Eg.: COUNT(), SUM(), MIN(), MAX(), AVG()

#### What kind of JOIN types do you know in SQL? Could you give examples?
(INNER) JOIN: Gives back the rows from table “A” and “B” which have related data in both. Eg.: you want the list the users who are shopping in your webshop with their shopping carts.
LEFT JOIN: Gives back all rows from table “A” and the rows form “B” relating to them is there is one. Eg.: you want a list of all users and their shopping carts if they have one.
RIGHT JOIN: Gives back rows from table “A” which have a relating one in table “B” and all the rows from “B”. Eg.: you want all shopping carts, even the ones’ which user haven’t been registered yet (they are just anonymously shopping).                                         
FULL JOIN: Gives back everything from everywhere. Eg.: You want everything from everywhere.

#### What are the constraints in sql?
SQL constraints are used to specify rules for the data in a table.
NOT NULL - Ensures that a column cannot have a null value.
UNIQUE - Ensures that all values in a column are different.
PRIMARY KEY - A combination of a NOT NULL and UNIQUE. Uniquely identifies each row in a table.
FOREIGN KEY - Uniquely identifies a row/record in another table.
CHECK - Ensures that all values in a column satisfies a specific condition.
DEFAULT - Sets a default value for a column when no value is specified.
INDEX - Used to create and retrieve data from the database very quickly.

#### What is a cursor in SQL? Why would you use one?
A database cursor is an object that enables traversal over the rows of a result set. It allows to process individual row returned by a query. It can be thought of as a pointer to a specific row within a query result.  The pointer can be moved from one row to the next. With other words it is a memory area used to store and manipulate the retrieved data. The active set is the set of rows the cursor holds. The cursor in fact an iterator.
The reason you need to use a database cursor is that you need to perform actions on individual rows.

#### What are database indexes? When to use?
A database index is a data structure that improves the speed of data retrieval operations on a database table at the cost of additional writes and storage space to maintain the index data structure. Indexes are used to quickly locate data without having to search every row in a database table. They can be created using one or more columns of a database table, providing the basis for both rapid random lookups and efficient access of ordered records.

#### What are database transactions? When to use?
- A transaction is a unit of work that you want to treat as "a whole." It has to either happen in full or not at all
- No matter what happens, the data you work with will be in a sensible state
- They guarantee that there will NOT be a situation where money is withdrawn from one account, but not deposited to another


The most important concepts of transactions are summarized by the ACID abbreviation:


   - atomic: all or nothing
   - consistent: follow the constraints of the database
   - isolated: no effect on other transactions
   - durable: written on persistent storage, committed transactions are stored permanently
#### What kind of database relations do you know? How to define them?
One-to-One: A row in table “A” can have at most 1 related row in table “B” and vice versa. It’s not very common, because 1 table would be also enough to  store data  in such relation, but there could be just too many columns then, or maybe it’s sensitive data, and we want to have different restrictions for it’s table.
        One-to-Many / Many-to-One: A row in table “A” can have multiple related rows in table “B”, but each row in “B”, can have only 1 related row in “A”. Eg.: clans and players, a clan can have multiple players in itself, but each player can have only 1 clan.
        Many-to-Many: Guess what: A row in table “A” can have multiple related rows in table “B”, and vice versa. Like in good ol’ webshop, a shopping cart can have multiple products, and each product can be in multiple shopping carts.
#### You have a table with an “address” field which contains data like “3525, Miskolc, Régiposta 9.” (postcode, city, street name and address). How would you query all records related to Miskolc?
SELECT * FROM <tablename> WHERE address LIKE '%Miskolc%’
#### How would you keep track of what kind of data has changed after an UPDATE or DELETE operation in a table?
hen we run an UPDATE or DELETE query on our database, the cursor does not contain anything at the end as default. It is a good habit however, to send some feedback to the backend after the query was executed (eg. for redirection or other purposes). It is a common situation for example, when we register a new user (run an INSERT statement) and wish to use the freshly generated user id immediately.




UPDATE products SET price = price * 1.10
       WHERE price <= 99.99
       RETURNING name, price AS new_price;

### HTML & CSS

#### What’s the difference between XML, XHTML and HTML?
- HTML(HyperText Markup Language) is a markup language to display and structure web pages
- XML(Extensible Markup Language) is also a markup language, but entirely different, 
it is designed to carry or store data
- XHTML(XML-based HTML) It serves the same function as HTML, but with the same rules as XML documents. 
These rules deal with the structure of the markup

#### How to include a JavaScript file in a webpage?
- <script src="" defer></script>


<li>You can include JavaScript in your HTML in two ways:
<ul>Writing the code in your HTML</ul>
  
   <script type="text/javascript">
     alert("This alert box was called with the onload event");
   </script>
  
<ul>Including it as a link to an external file</ul>


   <script type="text/javascript" src="path-to-javascript-file.js"></script>


   async: script is downloaded asynchronously and parsing is only blocked when running the JS
   defer: script is downloaded asynchronously and is run when parsing has finished; usually the prefered way

#### How to include a CSS file in a webpage?
	Use a link tag in the head section for an external file.
<link rel="stylesheet" type="text/css" href="mystyle.css">
<li>You can include CSS in yor HTML in two ways:
<ul>Writing the code in your HTML</ul>


   <p style="color:olive;font-size:24px;">HTML Styles with CSS</p>


<ul>Including it as a link to an external file</ul>


   <link rel="stylesheet" type="text/css" href="stylesheet.css" media="screen"/>
#### How to select an element using its id in CSS?
#elementIdName {
    /*CSS code here;*/
#### How to select elements using their class in CSS?
	.elementClassName {
    /*CSS code here;*/
}
#### How to select elements which have the ‘alpha’ and ‘beta’ classes in CSS?
.elementAlphaClassName.elementBetaClassName {
    /*CSS code here;*/
} 
#### How to select all list items in all ordered lists on the page in CSS?
ol  li { 
}
#### How to select elements using their attributes in CSS?
a[attribute="example"] {
   background-color: yellow;
}


a[attribute] {                          ------------> only if it has the given attribute with any value
   background-color: yellow;
}
#### What are UX and UI?
- User experience (UX) is the interaction and experience users have with a company's products and services
 - User interface (UI) is the specific asset users interact with.  
 For example, UI can deal with traditional concepts like visual design elements such as colors and typography
#### Please list some points that an application should fulfill to have good UX.
Useful – Content should be original and fulfill a need.
Usable – The site must be easy to find.
Desirable – Design elements bring about emotion and appreciation.
Findable – Content needs to be locatable and navigable offsite and onsite.
Accessible – Content needs to be accessible to people with disabilities.
Credible – Users must believe and trust what you tell them.
#### What is XML, XSLT, DTD?
- XML stands for eXtensible Markup Language. XML is a markup language much like HTML. 
XML was designed to store and transport data.
- XSLT (Extensible Stylesheet Language Transformations) is a language for transforming XML documents into other XML documents, or other formats such as HTML for web pages, plain text or XSL Formatting Objects, which may subsequently be converted to other formats, such as PDF, PostScript and PNG
- Document Type Definition (DTD) defines the structure and the legal elements and attributes of an XML document
#### What is the difference between HTML and XML?
- XML was designed to carry data - with focus on what data is
- HTML was designed to display data - with focus on how data looks
- XML tags are not predefined like HTML tags are

### Javascript

#### What is javascript?
JavaScript is an object-oriented programming language mainly used in front-end environment but it is more and more usual to use JS for building backend servers eg. The most common running environment of JavaScript is in the client-side browser. It is imported into HTML files in script elements and sent to the user via request-response based HTTP communication. The browser downloads and runs the script making websites more interactive and user friendly.


#### When to use AJAX? Bring examples of its usage.
AJAX (Asynchronous JavaScript and XML) is for "action on a page". Reducing server load, "good looking", user friendly.
Form validation (faster than go to back-end, then back with the "wrong" answer)
Comments (immediate appearance, can change often)
Filtering, sorting (fast, and the page act more like Excel)
Surveys and polls (click, and see the result)
Captcha


- let response = await fetch(url, options); // resolves with response headers 
let result = await response.json();
- fetch(url, options) 
 .then(response => response.json()) 
 .then(result => /* process result */)

#### What is DOM and how to manipulate it from Javascript?
- The Document Object Model is a way to manipulate the structure and style of an HTML page. It represents the internals of the page as the browser sees it, and allows the developer to alter it with JavaScript. Getting an Element: By ID, By Tag Name, By Class Name, By CSS Selector.


#### What are events and how/why to use them in Javascript?

An HTML event can be something the browser does or something a user does. From a click to page loading. You can add event listeners to DOM element(s). When the event occurs, it fires the code provided through the listener.
#### What is event bubbling/capturing? How would you use it?
What is event bubbling/capturing? How would you use it?
- Bubbling: when an event happens on an element, it first runs the handlers on it, 
then on its parent, then all the way up on other ancestors
- Capturing: the event first goes through the ancestors chain down to the element (capturing phase), then it reaches the target and triggers there


   If we would like to prevent further bubbling we can call one of the following functions:


       event.stopPropagation
           - prevents the further bubbling of the event (parent nodes' handlers will not be called)


       event.stopImmediatePropagation
           - if there are more listeners on an element for the same event type they run in the order they were defined
           - calling this function prevents all other event handlers attached to this element from running
           - also calls event.stopPropagation implicitly preventing further bubbling


#### What is JSON and how do we use it?
- JavaScript Object Notation
 - JSON is a lightweight format for storing and transporting data
 - Sending data to server
   - If you have data stored in a JavaScript object, you can convert the object into JSON, and send it to a server
   - JSON.stringify(myObj);
 - Receiving Data
   - If you receive data in JSON format, you can convert it into a JavaScript object
   - JSON.parse(myJSON);


## Software engineering

### Version control

#### What type of branching strategy would you use?
Types Of Branching Strategies:
Feature Branching (Task Branching), Feature Flag Branching for Continuous Delivery, Release Branching

#### What would you do if you find a bug on the production code (master branch)?
Hotfix, or consult with my teammates/project manager about the hotfix.

#### How can you move changes from one branch to another in GIT?
git merge, git rebase, git cherry-pick
#### How does a VCS help with code reviews?
Before merging into the develop branch we can create pull requests. When a pull request is made everyone who has access gets a notifying email. They can then review the code by adding comments, line comments etc.


When the review is over and the pull request is accepted, the changes can finally be merged into the develop branch.


- You can see all the commits and see what has been changed

#### What is your favorite git command? Why?
git status
#### What does remote/local mean in Git? 
Local repository takes place usually on your computer, this is where you commit your changes.
Remote repository is often in the cloud (example on GitHub), and teammates or other people can access it, push their changes there, and I can download the project from that location or the latest version to merge with my work, and push it back to others who could access the new version.
### DevOps

#### Why is it good to use a package manager software?
- A package manager is a programming language’s tool to create project environments 
and easily import external dependencies
- Python uses the pip package manager
- You don’t have to reinvent the wheel and are able to make the most of the tools at your disposal

#### Why is it good to use a virtual environment for a project?
A project could require multiple software versions. To prevent errors, and set up the best environment for the project, especially if you work (worked) on multiple projects, it is highly recommended to use virtual environments.

### Networks

#### What kind of HTTP status codes do you know?
Class 1xx – Informational: If an HTTP status code 1xx is transmitted, the server informs the client that the request is in motion. This class combines codes that are responsible for delivering information to the client during the request.


Class 2xx – Success: A 2xx code announces a successful operation. If this code is transmitted, it means that the client’s request was received by the server, understood, and accepted.


Class 3xx – Redirection: A 3xx code shows that the server’s request was received.3xx codes appear during redirections and forwardings.


Class 4xx – Client error: If a 4xx code appears then there’s been a client error. The server has received the request, but cannot perform it.


Class 5xx – Server error: A 5xx code is shown when the server has failed to perform the request. These server error codes report that the request cannot be performed at present or is not possible at all, which then leads to an HTML error page.  

#### What is a API?
- API stands for Application Programming Interface
- It allows two applications to talk to each other
- Each time you use an app like Facebook, send an instant message, or check the weather on your phone, you’re using an API
Application Program Interface (API) acts as a layer between your application and external service. It defines interactions, the kinds of calls or requests that can be made, how to make them, the data formats that should be used, the conventions to follow, etc.
It is like a waiter in the restaurant: our application sends the orders and the waiter retrieves all the necessary information (the food in the example) for the customer.

#### What is REST API?
REST stands for REpresentational State Transfer, meaning when a REST API is called, the server will transfer a representation of the requested resource’s state to the client.
A RESTful API uses HTTP requests for communication with web services.


#### What is JSON? When to use?
#### What is TCP/IP? What layers does it define, what are they responsible for?
It is a set of protocols that define how two or more computers can communicate with each other. The protocol is effectively a set of rules that describe how the data is passed between the computers.
“Host” means a computer.
The “process” means a running software program, such as web browser.
The “link” means “router”.
Application layer (process-to-process): Application layer are protocols that focus communication from a high-level perspective, the application's perspective. Such as send/receive the data. The format of the data. For example, {HTTP (web), SMTP (email), DHCP (automatic host config)} are protocols at this level.


Transport layer (host-to-host): provides end-to-end communication services for applications. Two most used protocols in this layer are TCP and UDP.


Internet layer (internetworking): The internet layer is about exchanging datagrams across machines. The primary example is the IP (Internet Protocol), which defines IP addresses. Its function in routing is to send datagrams to the next router that is closer to the destination IP address.


Link layer: This layer is pretty much about physical connection technology. That is, translating packets to various electric or optical wire signals, or wireless by radio waves or satellite transmission. The Ethernet, it's cable, is considered a standard of the link layer.

#### What’s the difference between TCP and UDP?
TCP/IP is a suite of protocols used by devices to communicate over the Internet and most local networks. Transmission Control Protocol (TCP) provides apps a way to deliver (and receive) an ordered and error-checked stream of information packets over the network. The User Datagram Protocol (UDP) is used by apps to deliver a faster stream of information without any error-checking.The sender doesn’t wait to make sure the recipient received the packets.




TCP:
-Transmission Control Protocol
-Connection-oriented protocol
-connection must be established before transmitting data and connection should close after this
-Guarantees delivery
-sequencing data - packages arrive in-order at receiver
-It is slower


UDP:
-User Datagram Protocol
-Datagram oriented protocol
-No overhead for opening, maintaining, or closing a connection
-Fast
-No guarantee of data being received/sent
-Does not sequence data

#### How does an HTTP Request look like? What are the most relevant HTTP header fields?
HTTP request has three sections, Start line, Headers, Body. These sections contain plain text based information, sometimes the body contains binary data for example an image.
Start line: contains the request method, the URI, and the http version.
Headers: has name: value pairs, these pairs store some informations and rules. There could be lot of these pairs.
Body:  message body is optional but most HTTP requests with bodies use POST or PUT request method.

#### How does an HTTP Response look like? What are the most relevant HTTP header fields?
HTTP response has three sections, Start line, Headers, Body. These sections contain plain text based information, sometimes the body contains binary data for example an image.
Start line: contains the http version and a status code.
Headers: has name: value pairs, these pairs store some informations and rules. There could be lot of from these pairs.
Body: contains the requested file, for example login.html.

#### What is DNS? How does it work?
DNS is for Domain Name System. DNS is like a directory which matches names with numbers. In this case names are website URLs, and numbers are IP addresses. DNS were created, because for most people it is easier to remember words instead of specific sets of numbers.


The DNS directory is not stored in one place, this is a distributed system. It is stored on domain name servers all around the world, which are communicating with each other. In fact, some sites have hundreds or more IP addresses that correspond with a single domain name. For example, the server your computer reaches for  is likely completely different from the server that someone in another country would reach by typing the same site name into their browser. Another reason for the distributed nature, is the amount of time it would take a user to get a response.

#### What is a web server?
A web server is server software, (or hardware dedicated to running this software,) that can satisfy client requests on the World Wide Web. A web server can contain one or more websites. A web server processes incoming network requests over HTTP and several other related protocols.

#### Explain the client-server architecture.
Explain the client-server architecture.
Client-Server Architecture is a computing model in which the server hosts, delivers and manages most of the resources and services to the client. This type of architecture has one or more client computers connected to a central server over a network or internet connection. Client-server architecture is also known as a networking computing model or network because all the requests and services are delivered over a network.

#### What would you use a session for?
To store data across page loads. Example: information about the logged-in user(s activity).
This data stored until the user is logged in.


The session object can be thought of as a huge dictionary where the keys are the session ids and the values are further dictionaries. In Flask when we use the session variable name we refer to the 'smaller' dictionary which is related to the current client only. In these session objects we can store any data we would like to. It is not advised to store too much data in it however, as with the increasing amount of users the occupied memory gets even larger.


As a result session data is often stored in a database. When the user logs in a session id is generated which is sent via a cookie to the client. The client sends this cookie back with each request to authenticate themselves. The server checks whether the session id sent by the cookie is still valid and if it is so, send the response.

#### What would you use a cookie for?
- For example at online shopping, when you give your personal information, you don't have to do it next time because it is stored, just like items in your shopping cart
- Servers can use cookies to provide personalized web pages, like changing to dark theme


Cookies expire when the browser is closed as default (these are session cookies; the session itself also ends) but it is also possible to set a custom expiration date (these are persistent cookies). In this case the next time we open the website in our browser this cookie will automatically be sent along with our request. This behaviour can be utilized to keep the user logged in after the browser is closed and also to track browsing habits (that is why they are also often referred to as tracking cookies).


## Software Development Methodologies

#### What kind of software development methodologies do you know? What are the main features of these?
Waterfall Model
Considered as the traditional method of explaining the software development process in software engineering, waterfall model happens to clarify the process into a linear flow with a specified sequence to let the users understand that further level is made progressive on completion of the previous one.
Moreover, this methodology also talks about the fact that going back to deal with the changes is not possible.
Pros:
1.        Easy to understand and functional
2.        Simple enough to handle as model is rigid
3.        Saves significant amount of time
4.        Allows for easy testing and analysis
Cons:
1.        Only matches precise needs
2.        Not applicable for maintenance projects
3.        No option to know possible outcome of a project
4.        Not excellent for long and ongoing projects

#### What are the SCRUM roles?
3 Scrum Roles:


Product Owner: “Holder of Product Value”, he determines what has to be done, sets priorities in work (to deliver the highest value).


ScrumMaster: He’s monitoring the team’s Scrum process. He is not the team leader, he is rather an advisor, who is observing if the team works by the rules and values of Scrum. Manages the process of how information is exchanged. Works on an ideal working environment.


Development Team: Works on the product (on specific features (user stories)). Development team has autonomy, they plan the workflow, they decide which member works on which user story.

#### What are the SCRUM ceremonies?
4 Scrum ceremonies:


Daily Scrum Meeting (aka: daily stand-up): Each day at the same time, the team members exchange the vital information to sync. Usually, there are 3 main questions: What did you do yesterday? What will you do today? What is getting in your way?


Sprint Planning Meeting: The entire Scrum team plans the next sprint, checking the product backlog and the business values of user stories.


Sprint Review/Demo: A meeting where the team demonstrates their achievements in the sprint, and they can get feedback from the product owner and project stakeholders.


Sprint Retrospective: After review, the team reviews their own work and workflow: what did go well, what did go wrong? The team wants to define how they can improve in the next sprint.

#### What are the SCRUM artifacts?
3-4 Scrum Artifacts:
1. Product Backlog: An ordered list of all the features that the end product can have. All the features are prioritized by the product owner, and most time, it gives detailed requirements and estimated time about them.


2. Sprint Backlog: The features which are selected from the product backlog for one sprint. It determines the specific tasks and goals of the sprint.


3. Increment: The sum of all completed item from the product backlog. At the end of the sprint, a new increment must be “done”: it must be in an usable condition, regardless of whether it’s about to be released or not. The “Done” status may vary significantly per Scrum Team.


4 Sprint Burn-Down Chart (Some sources name it as an artifact, some don’t): A practice for monitoring the Sprint progress towards the Sprint Goal. The team tracks the total work remaining in the Sprint backlog. This way the team can manage it’s progress and workflow.

#### What is the main goal of a retrospective meeting?
To discuss what worked, what didn't work during team work and what to do to improve in the future
#### Explain, when would you recommend to use the waterfall methodology?
Projects with clear objectives and stable requirements can best use the waterfall method. Less experienced teams, as well as teams whose composition changes frequently, may benefit from using it.


* Requirements are very well documented, clear and fixed
* Product definition is stable
* Technology is understood and is not dynamic
* There are no ambiguous requirements
* Ample resources with required expertise are available to support the product
* The project is short
The Waterfall methodology prevails when the project is constrained by cost and/or time, and the requirements and scope are well understood.
