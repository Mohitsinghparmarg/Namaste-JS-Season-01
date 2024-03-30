javaScript_EP_01 

    How JavaScript works?
    Ans-Everything in JavaScript happens inside an "execution context".
    Execution context has two component
    1. memory component[variable environment] -This is the place where all variables and functions are stored    as key value pairs. eg-{key: value || n:2;}
    2. code component[Thread of execution] -This is the place where code is executed one line at a time.
    Note- *JavaScript is a synchronous single-threaded language -Single threaded means JavaScript can execute one command at a time.
    -Synchronous single-threaded that means JavaScript can execute one command at a time in a specific order.


 How JavaScript Code is executed? ❤️& Call Stack | Namaste JavaScript Ep. 2 

         1. When JavaScript code is executed, Execution Context is created and it is called Global Execution Context. 
        2. JavaScript program is executed in TWO PHASES inside Execution Context 
          a. MEMORY ALLOCATION PHASE - JavaScript program goes throughout the program and allocate memory of    Variables and Functions declared in program. 
          b. CODE EXECUTION PHASE - JavaScript program now goes throughout the code line by line and execute the code. 
        3. A Function is invoked when it is called and it acts as another MINI PROGRAM and creates its own     Execution Context.
        4. Return keyword return the Control back to the PREVIOUS Execution-Context where the Function is called and Execution  Context of the Function is DELETED. 
        5. CALL STACK maintains the ORDER of execution of Execution Contexts. It CREATES Execution Context whenever a Program starts or a Function is invoked and it pops out the Execution Context when a Function or Program ENDS.

        Call stack 
        Execution control stack
        Program stack
        Control stack
        Runtime stack
        Machine stack

 Hoisting in JavaScript 🔥(variables & functions) | Namaste JavaScript Ep. 3 
 
    1. In JS, before the code is executed, the variables get initialized to undefined. 
    2.  Arrow functions enact as variables and get "undefined" during the memory creation phase while functions actually get run.
    3.  Hoisting: Mechanism in JS where the variable declarations are moved to the top of the scope before execution. Therefore it is possible to call a function before initializing it. 
       
           declarations are hoisted, not the initializations. 

           console.log(x); // undefined
           var x = 5;
           console.log(x); // 5

    4. Whenever a JS program is run, a global execution block is created, which comprises of : Memory creation and Code execution.
    5.  Variable declarations are scanned and are made undefined .
    6.  Function declarations are scanned and are made available



  How functions work in JS ❤️ & Variable Environment | Namaste JavaScript Ep. 4 

    1.We learnt how functions work in JS.
    2.At first a global execution context is created, which consists of Memory and code and has 2 phases: Memory allocation phase and code execution phase. 
    3.In the first phase, the variables are assigned "undefined" while functions have their own code. 
    4.Whenever there is a function declaration in the code, a separate local execution context gets created  having its own phases and is pushed into the call stack. 
    5.Once the function ends, the EC is removed from the call stack. 
    When the program ends, even the global EC is pulled out of the call stack.  


  SHORTEST JS Program 🔥window & this keyword | Namaste JavaScript Ep. 5  

  1.  Shortest Program in JS: Empty file. Still, browsers make global EC and global space along with Window   object. 
  2.  Global Space: Anything that is not in a function, is in the global space. 
  3.  Variables present in a global space can be accessed by a "window" object. (like window.a) 
       In global space, (this === window) object.  

  undefined vs not defined in JS 🤔 | Namaste JavaScript Ep. 6  

   1. Undefined is a Special Placeholder which is used to reserve memory for the variables in the memory creation phase. Even before a single line of code is executed JS engine assigns undefined to the variables. 
   2. Not Defined means if we try to console or access any variable which is not declared in the code then we get Not Defined error. 
   3. JS is a loosely typed language or weakly typed language means it does not attaches its variables to specific data types like in C++ and java.
   4. Remember undefined !== not defined.

  The Scope Chain, 🔥Scope & Lexical Environment | Namaste JavaScript Ep. 7  

    1.Lexical environment = EC's Local Memory + Reference to Lexical Environment of its parent. 
    2.Lexical Environment of its parent is the scope where a function is physically present or defined. So, suppose a function x(), is defined and invoked in the GEC, when function x()'s EC is pushed in the call stack, it stores a reference to its parent's lexical environment i.e. the GEC's memory. 
    3. Whenever a new Execution Context is pushed in the Call Stack it holds a reference to the Lexical Environment of its parent, i.e. the EC's memory from where it was invoked. 
    4.  Global execution context holds reference to null. 
    5. JavaScript engine first looks for the variable/function being accessed in the local scope of the function, and if not found, it keeps on searching the lexical environment of its parent until it finds the variable/function being accessed.
    6.  The mechanism mentioned in point 4 above is called SCOPE CHAIN. 
    7. If the variable accessed is not found in the Scope Chain, then you will get the variable is not defined error in the browser's console.

 let & const in JS 🔥Temporal Dead Zone | | Namaste JavaScript Ep. 8  

     temporal dead zone refers to the period between the entering of the scope and the actual declaration of a variable using let or const.
     -> attempting to access the variable will result in a ReferenceError.
     
     ->  let and const are hoisted. we can not use them before initialization is result of "temporal dead zone". It is not applied on var .
     ->  js use different memory than global execution context to store let and cost. which is reason behind "temporal dead zone" 
     ->  level of strictness ... var<<let<<const.
     -> let , const variables are stored in block scope.
      ->  var //no temporal dead zone, can redeclare and re-initialize, stored in GES 
     -> Let
       //use TDZ, can't re-declare, can re-initialize, stored in separate memory 
     -> Const
       //use TDZ, can't re-declare, can't re-initialize, stored in separate memory 
     ->  syntax error is similar to compile error. while type and reference error falls under run time error. 
     ->  syntax error -> violation of JS syntax 
     type error ->while trying to re-initialize const variable 
     reference error -> while trying to access variable which is not there in global memory.

  BLOCK SCOPE & Shadowing in JS 🔥| Namaste JavaScript 🙏 Ep. 9

        Code inside curly bracket is called block. 
        2.  Multiple statements are grouped inside a block so it can be written where JS expects single statements like in if, else, loop, function etc. 
        3.  Block values are stored inside separate memory than global. They are stored in block. (the reason let and const are called block scope) 
        4.  Shadowing of variables using var, let and const. 
        5.  The shadow should not cross the scope of original otherwise it will give error.
        6.  shadowing with let datatype to var datatype is illegal shadowing and gives error.
        7.  var value is stored in nearest outer function or global scope and hence can be accessed outside the block as well whereas same is not the case with 
            let and const.
       …………………………………………………………………………………………………….
       
       Block :-  It is used to combine multiple statement into one statement so that we can use it at those places where JavaScript expects to have single 
               statement. 
       
       Scope :-  scope of a variable or a function is the place where these are accessible. 
       
       Block scope :-  The variables and function present within the scope of a block section. And block follows the lexical scope chain pattern while accessing 
            the variable.
       
        Shadowing :-  Providing same name to the variable as of those variable which are present in outer scope. 
       Local variable has much precedency as compare to the global variable in a function.
       

   Closures in JS 🔥 | Namaste JavaScript Episode 10  

       Q. What is closure?
        A. The function bundled with its lexical environment closed to that function 
       simply function + Lexical environment and closures have very special place in runtime environment .
       
       The fun in JavaScript is you can assign a variable for a function and also you can pass function as a parameter even you can return the function in 
       JavaScript!! 
       
        Q. What does the closure do in my JavaScript programs?
       
        A. Whenever I call a function in JavaScript the closure maintains its values(lexical env.) and function in its own runtime and when that specific function 
          executed, it returns with own environment even the variable vanished after its execution .
       : as variable value is changed before executing the return (the function) Value will be 100 In closures, values in variable are 'pass by reference' hence 
         there values can be changed, and whenever comes the closure inside closure(multilevel one) we can see the function refers the 'parent' variable 
       
       function x()
       {
             var a=10;
             function y()
               {
                   console.log(a);
               }
               return y;
       }
       var z= x();
       
       console.log(z);
       
       z();
       
       Output of this is 10
       
       
       function x()
       {
             var a=10;
             return  function y()
               {
                   console.log(a);
               }
       }
       var z= x();
       console.log(z);
       z();
       
       Both will give the same output which is 10
       
       
       function z()
       {
             var a=100;
             function x()
           {
               var b=200;
             function y()
               {
                   console.log(a,b);
               }
               y();
           }
           x();
       }
       z();
        
        Output is 100 200

uses of closure ->
          -> Module Design pattern.
          -> Currying.
          -> Functions Like Once.
          -> Memoize.
          -> Maintaining  State as async World.
          -> setTimeouts.
          -> Iterators.
          




 setTimeout + Closures Interview Question 🔥 | Namaste 🙏 JavaScript Ep. 11 

           1. setTimeout stores the function in a different place and attached a timer to it, when the timer is finished it rejoins the call stack and executed.
           2.  Without closure the var reference gives the latest value as it does not retain the original value but rather has the reference so any update in value after timeout will be shown. 
           3.  If we use let/const because they have block scope, every time a new copy of variable is attached, thus this can be done without closure.
       
       
       function x()
       {
         
          for(var i=1;i<=5;i++){
           function close(i){
           setTimeout(function (){
              console.log(i);
           },i*1000); 
         }
            close(i);
          }
           console.log("hii");
       }
       x();
       
       Output : hii
                   1
                   2
                   3
                   4
                   5 
       
       function x()
       {
         
          for(let i=1;i<=5;i++){
           setTimeout(function (){
              console.log(i);
           },i*1000); 
          }
           console.log("hii");
       }
       x();
       
       Will give the same output as above
 
CRAZY JS INTERVIEW 🤯ft. Closures | Namaste 🙏 JavaScript Ep. 12  
  
        1.  An inner function can be directly called using two parenthesis ()() .
        2. Even parameters can be passed this way (Remember that the function needs to be returned to do this) .
        3. Closures can also be used for data hiding and encapsulation. So other code cannot access this value.
        4.  Unused variables are automatically deleted in High Level Programming language by garbage collector.
     Closures allocate a lot of memory which cannot be deleted so this acts as a disadvantage. 
        5. Some browsers now have smart garbage collectors that automatically deletes variables that are not used outside closures.
    
    
    
    function Counter()
    {
       var count=0;
       this.incrementCount=function ()
         {
          count++;
          console.log(count);
         }
         this.decrementCount=function ()
         {
          count--;
          console.log(count);
         }
    }
    var counter1=new Counter();
    counter1.incrementCount();
    counter1.decrementCount();
    
 FIRST CLASS FUNCTIONS 🔥ft. Anonymous Functions | Namaste JavaScript Ep. 13  

   1. What is Function Statement ? 
   
    A normal function that we create using Naming convention. & By this we can do the Hoisting. For Ex -  function xyz()
    { 
         console.log("Function Statement"); 
    }
   2. What is Function Expression ? 
   
     When we assign a function into a variable that is Function Expression. & We can not do Hoisting by this becz it acts like variable. For Ex - 
    var a = function()
    { 
        console.log("Function Expression"); 
    } 
   3. What is Anonymous Function ? 
   
     A Function without the name is known as Anonymous Function. & It is used in a place where function are treated as value. For Ex - 
      function()
         {
    
         } 
   4. What is Named Function Expression ? 
   
    A function with a name is known as Named Function Expression. For Ex - 
      var a = function xyx()
    { 
          console.log("Names Function Expression"); 
    } 
    5. Difference b/w Parameters and Arguments ?
   
       When we create a function & put some variabels in this ( ) that is our Parameters. For Ex -
     function ab( param1, param2 )
    {
       console.log(" ")
    } 
    & When we call this function & pass a variabel in this ( ) that is our Arguments For Ex - ab( 4, 5 ); 
    6. What is First Class Function Or First class citizens?
     
     The Ability of use function as value, 
    * Can be passed as an Argument, 
    * Can be executed inside a closured function & 
    * Can be taken as return form. For Ex - 
    var b = function(param)
    { return function xyz(){ 
       console.log(" F C F "); 
      } 
    } 
   
    7. Function are heart of JS. 
    They are called first class citizens or first class functions because they have the ability to be stored in the variables, passed as parameters and arguments.
     They can also be returned in the function.

  Callback Functions in JS ft. Event Listeners 🔥| Namaste JavaScript Ep. 14 

    1.Function that is passed on as argument to another function is called callback function. 
    2.setTimeout helps turn JS which is singlethreaded and synchronous into asynchronous. 
    3.Event listeners can also invoke closures with scope. 
       Event listeners consume a lot of memory which can potentially slow down the website therefore it is good practice to remove if it is not used. 


 Asynchronous JavaScript & EVENT LOOP from scratch 🔥 | Namaste JavaScript Ep.15   

        1. When does the event loop actually start?

         - Event loop, as the name suggests, is a single-thread, loop that is     almost infinite`. It's
           always running and doing its job. 

        2.  Are only asynchronous web API callbacks are registered in the web API environment? -

           YES, 
            the synchronous callback functions like what we pass inside map,     
            filter, and reduce aren't registered in the Web API environment. It's just those async callback functions that go through all this.

     3.  Does the web API environment stores only the callback function and pushes the same callback to queue/microtask queue?

       - Yes,
         the callback functions are stored, and a reference is scheduled in the queues. Moreover, in the case of event listeners(for example click handlers), the original callbacks stay in the web API environment forever, that's why it's advised to explicitly remove the listeners when not in use so that the garbage collector does its job. 

        4.  How does it matter if we delay for setTimeout would be 0ms. Then callback will move to queue  without any wait?
         No,
          there are trust issues with setTimeout() 
    
    .   The callback function needs to wait until the Call Stack is empty. So the 0 ms callback might have to   wait for 100ms also if the stack is busy. It's a very beautiful concept, and I've covered this in detail in the next episode of Namaste JavaScript. 
     
      1. WebAPIs
         window
        - Global Object 
        - setTimeout
        - DOM APIs 
        - console 
        - fetch() 
        - localStorage 
        - location 
        2.  Event loops - continuously watches Call stack and CallbackQueue till the queue and stack are empty 
        3.  Why we need "Callback Queue" - when user clicks continuously so it needs to be queued somewhere 
        4.  Micro task queue - Higher priority of execution for call stack - fetch() APIs - promises, network  calls - mutation observers 
        5.  First CALL STACK -> MICRO TASK QUEUE -> CALLBACK QUEUE - This is the order of execution of tasks 
        6.  Starvation - when micro task queue is again and again generating micro tasks because of which call back queue tasks are not getting chance to get executed
    
   JS Engine EXPOSED 🔥 Google's V8 Architecture 🚀 | Namaste JavaScript Ep. 16   

        JS runtime environment contains all elements required to run JS.
         2.  It contains JS engine, set of API's, callback queue, microtask queue, event loop.
         3.  JS engine is a piece of code. 
        4. Process includes Parsing ---> Compilation -----> Execution.
         5.  Parsing breaks code into tokens and converts it into AST(Abstract Syntax Tree). 
        6. Modern JS engine follows JIT(just in time) compilation, it interprets while it optimises code as much as it can. 
        7. Execution and Compilation are done together. 
        8.  Execution has Garbage collector and other optimisation such as inlining, copy elusion, inline caching etc.  

        inline in js
        copy elision in js
       inline caching in js  

 TRUST ISSUES with setTimeout() | Namaste JavaScript Ep.17  

     The setTimeout function stores it in the callback queue which is executed only after call stack is empty, even if setTimeout is set to 0ms. 
     setTimeout ensures that minimum it will take the time mentioned because it may be paused due to call stack not empty. 

 Higher-Order Functions ft. Functional Programming | Namaste JavaScript Ep. 18 

    Follow DRY(Don't Repeat Yourself) principle while coding.
    2.  Use function to stop writing repeating line of codes. 
    3.  Function that takes another function as argument(callback function) is known as Higher order functions. 
    4. It is this ability that function can be stored, passed and returned, they are called first class citizens. 
   If we use Array.property.function-name. This function is accessible to any array in your code. 

map, filter & reduce 🙏 Namaste JavaScript Ep. 19 🔥

    1. map method is used when we want transformation of whole array. 
    2.  filter is used when we want to filter the array to obtain required value.
    3.  reduce is used when we want to reduce the array to single value eg (max, min, avg, sum, difference etc). 
    4.  reduce passes two arguments one function(which includes accumulator and initial value as argument itself) and another initial value of current array.
    5.  Homework: const output = user.reduce(function(acc, curr)
                       { 
                             if (curr.age < 30)
                                {  
                                     acc.push(curr.firstName); 
                                 }
                        return acc; 
                         }, [ ])
            console.log(output);
