# javaScript_EP_01 #####

    How JavaScript works?
    Ans-Everything in JavaScript happens inside an "execution context".
    Execution context has two component
    1. memory component[variable environment] -This is the place where all variables and functions are stored    as key value pairs. eg-{key: value || n:2;}
    2. code component[Thread of execution] -This is the place where code is executed one line at a time.
    Note- *JavaScript is a synchronous single-threaded language -Single threaded means JavaScript can execute one command at a time.
    -Synchronous single-threaded that means JavaScript can execute one command at a time in a specific order.


### How JavaScript Code is executed? ❤️& Call Stack | Namaste JavaScript Ep. 2 ###

         1. When JavaScript code is executed, Execution Context is created and it is called Global Execution Context. 
        2. JavaScript program is executed in TWO PHASES inside Execution Context 
          a. MEMORY ALLOCATION PHASE - JavaScript program goes throughout the program and allocate memory of Variables and Functions declared in program. 
          b. CODE EXECUTION PHASE - JavaScript program now goes throughout the code line by line and execute the code. 
        3. A Function is invoked when it is called and it acts as another MINI PROGRAM and creates its own Execution Context.
        4. Return keyword return the Control back to the PREVIOUS Execution-Context where the Function is called and Execution  Context of the Function is DELETED. 
        5. CALL STACK maintains the ORDER of Execution of Execution Contexts. It CREATES Execution Context whenever a Program starts or a Function is invoked and it pops out the Execution Context when a Function or Program ENDS.

        Call stack 
        Execution control stack
        Program stack
        Control stack
        Runtime stack
        Machine stack

######
###### Hoisting in JavaScript 🔥(variables & functions) | Namaste JavaScript Ep. 3  ####
 
    1.  In JS, before the code is executed, the variables get initialized to undefined. 
    2.  Arrow functions Enact as variables and get "undefined" during the memory creation phase while functions actually get run.
    3.  Hoisting: Mechanism in JS where the variable declarations are moved to the top of the scope before execution. Therefore it is possible to call a function before initializing it. 
       
           declarations are hoisted, not the initializations. 

           console.log(x); // undefined
           var x = 5;
           console.log(x); // 5

          ..............

            getName();
            getName2(); // Type Error ,because it is working as an variable

            console.log(x);

            var x = 10;

            function getName(){
                      console.log("getName function");
            }

            var getName2 = () => {
                      console.log("getName2 function");
            }

    4.  Whenever a JS program is run, a global execution block is created, which comprises of : Memory creation and Code execution.
    5.  Variable declarations are scanned and are made undefined.
    6.  Function declarations are scanned and are made available.


######
 ##### How functions work in JS ❤️ & Variable Environment | Namaste JavaScript Ep. 4  #####

    1.We learnt how functions work in JS.
    2.At first a global execution context is created, which consists of Memory and code and has 2 phases: Memory allocation phase and code execution phase. 
    3.In the first phase, the variables are assigned "undefined" while functions have their own code. 
    4.Whenever there is a function declaration in the code, a separate local execution context gets created  having its own phases and is pushed into the call stack. 
    5.Once the function ends, the EC is removed from the call stack. 
    When the program ends, even the global EC is pulled out of the call stack.  

            var x = 10;
            a();
            b();
            console.log(x);

            function a(){
                  var x = 10;
                  console.log(x);
            }

            function b(){
                  var x = 100;
                  console.log(x);
            }




######
######  SHORTEST JS Program 🔥window & this keyword | Namaste JavaScript Ep. 5   #####

  1.  Shortest Program in JS: Empty file. Still, browsers make global EC and global space along with Window object. 
  2.  Global Space: Anything that is not in a function, is in the global space. 
  3.  Variables present in a global space can be accessed by a "window" object. (like window.a) 
       In global space, (this === window) object.  

        getName();
        var x = 10;
        console.log(x);

        function getName(){
                  
                var x = 200;
                console.log(x);
        }

#####
  #####  undefined vs not defined in JS 🤔 | Namaste JavaScript Ep. 6   #####

   1. Undefined is a Special Placeholder which is used to reserve memory for the variables in the memory creation phase,
      Even before a single line of code is executed JS engine assigns undefined to the variables. 
   2. Not Defined means if we try to console or access any variable which is not declared in the code then we get Not Defined error. 
   3. JS is a loosely typed language or weakly typed language means it does not attaches its variables to specific data types like in C++ and java.
   4. Remember undefined !== not defined.
          
         console.log(a) // Refrence Error
          console.log(x); // undefined
          var x = 10;
          console.log(x); // 10

            if(x === undefined){
                  console.log("x is undefined");
          }
          else{
                console.log("x is not undefined");
          }



#####
   ######   The Scope Chain, 🔥Scope & Lexical(hierarchy) Environment | Namaste JavaScript Ep. 7   #####

    1.Lexical environment = EC's Local Memory + Reference to Lexical Environment of its parent. 
    2.Lexical Environment of its parent is the scope where a function is physically present or defined. So, suppose a function x(), is defined and invoked in the GEC, when function x()'s EC is pushed in the call stack, it stores a reference to its parent's lexical environment i.e. the GEC's memory. 
    3. Whenever a new Execution Context is pushed in the Call Stack it holds a reference to the Lexical Environment of its parent, i.e. the EC's memory from where it was invoked. 
    4.  Global execution context holds reference to null. 
    5. JavaScript engine first looks for the variable/function being accessed in the local scope of the function, and if not found, it keeps on searching the lexical environment of its parent until it finds the variable/function being accessed.
    6.  The mechanism mentioned in point 4 above is called SCOPE CHAIN. 
    7. If the variable accessed is not found in the Scope Chain, then you will get the variable is not defined error in the browser's console.
         
      function a(){
         var x = 10;
         c();
      function c(){
            console.log(x);
        }
     }
   a();

######
 #####  let & const in JS 🔥Temporal Dead Zone | | Namaste JavaScript Ep. 8   #######

     temporal dead zone refers to the period between the entering of the scope and the actual declaration of a variable using let or const.
     -> attempting to access the variable will result in a ReferenceError.
     
     ->  let and const are hoisted. we can not use them before initialization, is result of "temporal dead zone". It is not applied on var .
     ->  js use different memory than global execution context to store let and cost. which is reason behind "temporal dead zone" 
     ->  level of strictness ... var<<let<<const.
     -> let , const variables are stored in block scope.
      ->  var //no temporal dead zone, can redeclare and re-initialize, stored in GES 
     -> Let
       //use TDZ, can't re-declare, can re-initialize, stored in separate memory which is called script and block.
     -> Const
       //use TDZ, can't re-declare, can't re-initialize, stored in separate memory which is called script and block.
     ->  syntax error is similar to compile error. while type and reference error falls under run time error. 
     ->  syntax error -> violation of JS syntax 
     type error ->while trying to re-initialize const variable 
     reference error -> while trying to access variable which is not there in global memory.

        ..................
           
           let a = 20; // stored in script which is different memory location
           console.log(a);
           var b = 30; // stored in global
        ....................
           console.log(x); // ReferenceError,can not access before initialization
           let x = 10;
        ...................
           let x = 10;
           let x = 20;  //  SyntaxError: Identifier 'x' has already been declared
        ....................
           let x = 10;
           var x = 20;  //  SyntaxError: Identifier 'x' has already been declared
        ....................
            var y = 20;
            var y = 30;
            console.log(y); // successfully Executed,can do in var
        .....................
              let a;
              a = 20;
              console.log(a);  // I can do this in let.
            but in const
          const b;  //  SyntaxError: Missing initializer in const declaration 
        ....................
           const b = 10;
           b = 20;  // TypeError: Assignment to constant variable.
        ...................
           console.log(y); // ReferenceError: y is not defined


    priorities to use var,let and const : const>let>var



#####
######   BLOCK SCOPE & Shadowing in JS 🔥| Namaste JavaScript 🙏 Ep. 9   ######

        Code inside curly bracket is called block. 
        2.  Multiple statements are grouped inside a block so it can be written where JS expects single statements like in if, else, loop, function etc. 
        3.  Block values are stored inside separate memory than global. They are stored in block. (the reason let and const are called block scope) 
        4.  Shadowing of variables using var, let and const. 
        5.  The shadow should not cross the scope of original otherwise it will give error.
        6.  shadowing with let datatype to var datatype is illegal shadowing and gives error.
        7.  var value is stored in nearest outer function or global scope and hence can be accessed outside the block as well whereas same is not the case with let and const.
       …………………………………………………………………………………………………….
       
       Block :-  It is used to combine multiple statement into one statement so that we can use it at those places where JavaScript expects to have single statement. 
       
       Scope :-  scope of a variable or a function is the place where these are accessible. 
       
       Block scope :-  The variables and function present within the scope of a block section. And block follows the lexical scope chain pattern while accessing the variable.
                 const a = 20;
                  {
                      const a = 30;
                      {
                          const a = 40;
                          console.log(a);
                      }
                      console.log(a);
                  }
                  console.log(a);
       
        Shadowing :-  Providing same name to the variable as of those variable which are present in outer scope. 
       Local variable has much precedency as compare to the global variable in a function.

           var a = 100;
           {
                var x = 10;
                let y = 20;
                const z = 30;
        
            console.log(x); // 10   // Shadowing
            console.log(y);
            console.log(z);
          }
            console.log(x); // 10    // Shadowing
            console.log(y); // ReferenceError
            console.log(z);

  .............................
         let a = 100;
          {
            let a = 10;
            let b = 20;
            const c = 30;
        
            console.log(a);  // 10  block space( Memory Scope)
            console.log(b);
            console.log(c);
          }
            console.log(a); // 100  script scope (Memory Scope)

-- this same thing will happen in const case....

........................................
  -- Illegal Shadowing
  let a = 10;
  {
     var a = 20;  // crossing the Boundaries...   5. The shadow should not cross the scope of original otherwise it will give error.
                 // shadowing with let datatype to var datatype is illegal shadowing and gives error.
  }
.......................
  -- valid
      let a = 10;
      {
          let a = 20;
          console.log(a)
      }
      console.log(a)
....................
this is also perfectly valid
var a = 10;
  {
    let a = 20;
    console.log(a)
  }
console.log(a)
       

#####
######   Closures in JS 🔥 | Namaste JavaScript Episode 10   ######

       Q. What is closure?
        A. The function bundled with its lexical environment closed to that function 
       simply function + Lexical environment and closures have very special place in runtime environment .
       
       The fun in JavaScript is that you can assign a variable for a function and also you can pass function as a parameter even you can return the function in JavaScript!! 
       
        Q. What does the closure do in my JavaScript programs?
       
        A. Whenever I call a function in JavaScript the closure maintains its values(lexical env.) and function in its own runtime and when that specific function executed, it returns with own environment even the variable vanished after its execution .
       : as variable value is changed before executing the return (the function) Value will be 100 In closures, values in variable are 'pass by reference' hence there values can be changed, and whenever comes the closure inside closure(multilevel one) we can see the function refers the 'parent' variable 
       
          function x(){
              var a = 20;
              function y(){
                  console.log(a);
              }
            return y;
          }
          var z = x();
          console.log(z)  // y() function
          z() // 20

      .................................................
       Another way of writing 

               function x(){
                  var a = 20;
                  return function y(){
                      console.log(a);
                }
              
              }
              var z = x();

              console.log(z) // y() function
              z()  // 20



      .......................................................
       
       
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


## Note Point : you also have to go through deep dive in these below concepts also , ohk 
  - Use of Closures :   
     - Module Design Pattern
     - Currying
     - Function like once
     - memoize
     - maintaining state in async world
     - setTimeouts
     - Iterators

####
### setTimeout + Closures Interview Question 🔥 | Namaste 🙏 JavaScript Ep. 11  ####

           1. setTimeout stores the function in a different place and attached a timer to it, when the timer is finished it rejoins the call stack and executed.
           2.  Without closure the var reference gives the latest value as it does not retain the original value but rather has the reference so any update in value after timeout will be shown. 
           3.  If we use let/const because they have block scope, every time a new copy of variable is attached, thus this can be done without closure.
       
      // best way:
       function x()
       {
         
          for(var i=1;i<=5;i++){
           function close(i){
           setTimeout(function (){
              console.log(i);
           },i*1000); 
         }
            close(i);  // it makes the new copy everytime for i value and pass into the function...
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
     
######
  ### CRAZY JS INTERVIEW 🤯ft. Closures | Namaste 🙏 JavaScript Ep. 12   ###
  
        1.  An inner function can be directly called using two parenthesis ()() .
        2. Even parameters can be passed this way (Remember that the function needs to be returned to do this) .
        3. Closures can also be used for data hiding and encapsulation. So other code cannot access this value.
        4.  Unused variables are automatically deleted in High Level Programming language by garbage collector.
     Closures allocate a lot of memory which cannot be deleted so this acts as a disadvantage. 
        5. Some browsers now have smart garbage collectors that automatically deletes variables that are not used outside closures.
    
    -
                function parent(){
                    var a = 10;
                  function child(){
                          console.log(a);
                  }
                child();
             }
           parent(); 

-
          function parent(){
            var a = 10;
           function child(){
                  console.log(a);
           }
           return child;
        }
         var b = parent();
         b();
         console.log(b);


-
        function parent(y){
              var z = 100;
           function child(y){
            let a = 10;
                  console.log(a,z,y);
           }
           
           return child;
        }
        
         var b = parent();
         console.log(b);
         b(1000);

-    
         function parentOfParent(){
                  var c = 55      
            function parent(y){
                var z = 100;
            function child(){
              let a = 10;
                    console.log(a,c,z,y);
            }
            
            return child;
          }
          return parent;
    }

 var b = (parentOfParent())("hii mohit");
 b();





-    
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

  ## DisAdvantage of closures: 
     - Over Consumption of Memory because those variables are not Garbage collected untill or unless the program is end...
     - Memory Leak

  ## Relationship between closures and garbage collection
        function x(){
          var a = 10;
          return function y(){
              console.log(a);
          }
      }
    var z = x();
    z();
  ## smart garbage colletion in V8
         function x(){
            var a = 10, b = 60;
            return function y(){
                console.log(a);
            }
         }
  var z = x();
  z();

  this is very interesting , if I put debugger on console.log(a) and then if I check whether the memory has been allocated to b or not 
  I will get that no , b to define hi nhi h ....
     
    
#####
   ### FIRST CLASS FUNCTIONS 🔥ft. Anonymous Functions | Namaste JavaScript Ep. 13   ###

   1. What is Function Statement ? 
   
    A normal function that we create using Naming convention. & By this we can do the Hoisting. For Ex - 

    function xyz()
       { 
         console.log("Function Statement"); 
       }
   2. What is Function Expression ? 
   
     When we assign a function into a variable that is Function Expression. & We can not do Hoisting by this becz it acts like variable. For Ex - 

     a();
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
   
    A function with a name is known as Named Function Expression. 
    in this xyz is in the local space which can be accessed inside the xyz function
    For Ex - 
     var c = function xyz(){
                console.log(xyz);
             }
         c();
    5. Difference b/w Parameters and Arguments ?
   
       When we create a function & put some variabels in this ( ) that is our Parameters. For Ex -
    function ab( param1, param2 )
     {
       console.log("hii this mohit ")
     } 
    ab(agr1,arg2)
    & When we call this function & pass a variabel in this ( ) that is our Arguments For Ex - ab( 4, 5 ); 

    6. What is First Class Function Or First class citizens?
     
     The Ability of use function as value, 
    * Can be passed as an Argument, 
    * Can be executed inside a closured function & 
    * Can be taken as return form. For Ex - 
-
        var b = function(param)
        { 
           return function xyz(){ 
           console.log(" F C F "); 
          } 
        } 
 - another example:

    var i = function(params1){
      return function abcd(){
             console.log("this is mohit........")
      }
    }
   console.log(i())
   
    7. Function are heart of JS. 
    They are called first class citizens or first class functions because they have the ability to be stored in the variables, passed as parameters and arguments.
     They can also be returned in the function.

######
   ###  Callback Functions in JS ft. Event Listeners 🔥| Namaste JavaScript Ep. 14   ###

    1.Function that is passed on as argument to another function is called callback function. 

   -
        setTimeout(function(){
               console.log("setTimeOut is called successfully!!!...")
           },5000);
      function x(y){
            console.log("it is function x...");
            y();
         }
      x(function y(){
            console.log("it is function y...")
      })

    2.setTimeout helps turn JS which is singlethreaded and synchronous into asynchronous. 
    3.Event listeners can also invoke closures with scope. 
       Event listeners consume a lot of memory which can potentially slow down the website therefore it is good practice to remove if it is not used. 
   -
            function attachEventListener(){
                  let count = 0;
                  document.getElementById("clickMe").addEventListener("click",function xyz(){
                  console.log("button has been Clicked!!!...",++count);
               })}
        attachEventListener();


######
   ###  Asynchronous JavaScript & EVENT LOOP from scratch 🔥 | Namaste JavaScript Ep.15   ###

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

     -Microtask Queue=> Mutation observer-> Microtask Queue m ye waale function aate hain these guys get more priority-> promises and mutation observers
     but sometimes there is a bad thing about it which is starvation 
         https://developer.mozilla.org/en-US/docs/Web/API/MutationObserver

      -Task Queue -> callback Queue  m ye sb aaye hain->  window
        - Global Object 
        - setTimeout
        - DOM APIs 
        - console 
        - fetch() 
        - localStorage 
        - location 



    
 ######
  ###   JS Engine EXPOSED 🔥 Google's V8 Architecture 🚀 | Namaste JavaScript Ep. 16   ###

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
      in memory heap , variables and functions are assigned memory 

    - garbage collector - orrinoco,oilpan and others...
 ## 
     https://stackoverflow.com/questions/60354194/understanding-mark-and-sweep-algorithm-in-javascript

## 
    https://astexplorer.net/

######
  ### TRUST ISSUES with setTimeout() | Namaste JavaScript Ep.17  ####

     The setTimeout function stores it in the callback queue which is executed only after call stack is empty, even if setTimeout is set to 0ms. 
     setTimeout ensures that minimum it will take the time mentioned because it may be paused due to call stack not empty. 
           
            console.log("start");

            setTimeout(function a(){
                    console.log("callaback function is called")
            }, 5000);

            // fetch("https://web.whatsapp.com/")
            //   .then(function b(){
            //           console.log("fetch is called")
            //   })

            console.log("End");

            let startDate = new Date().getTime();
            let endDate = startDate;
              
            while(endDate < startDate + 10000){
                    endDate = new Date().getTime();
            }
            console.log("while expires ")

....................................................................
          console.log("start");
          setTimeout(function a(){
                  console.log("callaback function is called")
          }, 0);
          console.log("End"); 
          
#####
 #### Higher-Order Functions ft. Functional Programming | Namaste JavaScript Ep. 18 ####

    Follow DRY(Don't Repeat Yourself) principle while coding.
    2.  Use function to stop writing repeating line of codes. 
    3.  Function that takes another function as argument(callback function) is known as Higher order functions. 
    4. It is this ability that function can be stored, passed and returned, they are called first class citizens. 
   If we use Array.property.function-name. This function is accessible to any array in your code. 

######
  ##### map, filter & reduce 🙏 Namaste JavaScript Ep. 19 🔥####

    1. map method is used when we want the transformation of whole array. 
    2.  filter is used when we want to filter the array to obtain required value.
    3.  reduce is used when we want to reduce the array to single value eg (max, min, avg, sum, difference etc). 
    4.  reduce passes two arguments one function(which includes accumulator and initial value as argument itself) and another initial value of current array.
         

      const arr = [10,20,30,40,50];

      const ans = arr.map((x) => x*2);

      const filterAns = arr.filter((x) => x > 10)

      const findSum = arr.reduce(function(acc,sum){
                acc += sum;
              return acc;
      },0);

      const findmax = arr.reduce(function(acc,curr) {
                if(curr > acc){
                      acc = curr;
                }
              return acc;
      },0)


      console.log(ans);
      console.log(filterAns);
      console.log(findSum);
      console.log(findmax);


      const arr2 = [
                
                      {firstName : "mohit",lastName : "parmar",age : 22},
                      {firstName : "rahul",lastName : "kumar",age : 25},
                      {firstName : "rohit",lastName : "singh",age : 24},
                      {firstName : "naman",lastName : "singh parmar",age : 22}

                
      ]

      const output = arr2.map((x) => x.firstName + " " + x.lastName);
      console.log(output)

      const findAge = arr2.reduce(function(acc,curr){
                      
                if(acc[curr.age]){
                      acc[curr.age]++;
                    }
                else{
                      acc[curr.age] = 1;
                    }
              return acc;
                    
      },{})

      console.log(findAge);

      const output2 = arr2.filter((x) => x.age < 25).map((x) => x.firstName);
      console.log(output2);

      const output3 = arr2.reduce(function(acc, curr){ 
                                  if (curr.age < 25)
                                      {  
                                        acc.push(curr.firstName); 
                                      }
                              return acc; 
                              }, [ ])
      console.log(output3);


  ##  Callback Hell | Ep 01 Season 02 - Namaste JavaScript
  
     -- http://callbackhell.com/
     
    Two issues while using callbacks

      1 - Callback hell
      When a function is passed as an argument to another function, it becomes a callback function. This process continues and there are many callbacks inside another's Callback function.
      This grows the code horizontally instead of vertically. That mechanism is known as callback hell. 
      
     - this type of structure is also known as PYRAMID OF DOOM

           const cart = ["shoes","pants","kurta"];
              api.createOrder(cart,function (){
                      api.proceedToPayment(function (){
                            api.showOrderSummary(
                                    function (){
                                      api.updateWallet()
                                    }
                                  )
                            })
                         })

      2 - Inversion of control
      The callback function is passed to another callback, this way we lose the control of our code. We don't know what is happening behind the scene and the program becomes very difficult to maintain. 
      That process is called inversion of control. 
 


## Promises | Ep 02 Season 02 - Namaste JavaScript
   
     -- https://javascript.info/promise-basics

    1. Before promise we used to depend on callback functions which would result in 
        1. Callback Hell (Pyramid of doom) 
             const cart = ["shoes","pants","kurta"];
                api.createOrder(cart,function (){
                        api.proceedToPayment(function (){
                              api.showOrderSummary(
                                      function (){
                                        api.updateWallet()
                                      }
                                    )
                        })
                })
        2. Inversion of control
    2. Inversion of control is overcome by using promise.
      2.1 A promise is an object that represents eventual completion/failure of an asynchronous operation.
      2.2 A promise has 3 states: pending | fulfilled | rejected.
      2.3  As soon as promise is fulfilled/rejected => It updates the empty object which is assigned undefined in pending state.
      2.4 A promise resolves only once and it is immutable. 
      2.5 Using .then() we can control when we call the cb(callback) function.

    3. To avoid callback hell (Pyramid of doom) => We use promise chaining. This way our code expands vertically instead of horizontally. Chaining is done using '.then()'
    4. A very common mistake that developers do is not returning a value during chaining of promises. Always remember to return a value. This returned value will be used by the next .then()


## Creating a Promise, Chaining & Error Handling | Ep 03 Season 02 Namaste JavaScript

      1. Promise can be created using a new Promise() constructor function.
      2. This constructor function takes a callback function as argument. 
      3. The callback function has 2 arguments named 'resolve' and 'reject'. Resolve and reject are the keywords provided by JS.
      4. We can only resolve or reject a promise. Nothing else can be done.
      5. An error can also be created using new Error('error message').
      6. There is also .catch() which is used to attach a failure callback function that handles any error that pops up during the execution of promise chain.
      7. .catch only handles error of .then() that are present above it. If there is any .then() below it, catch will not handle any error for that, also that ,then will get executed no matter what.
      8. It can be useful in a way if we want to catch error for a particular portion of a chain.
      9. We can have multiple catch based on requirement and then a general catch at the end.
      10. Always remember to return a value in the promise chain for the next .then to use .
      11. If it returns a value => It will be  used as an argument in next function. If it is a promise then the next .then in the promise chain is attached to the promise returned by the current callback function.
   
                const WhatsAppAPI = "https://web.whatsapp.com/"
                const promise= fetch(WhatsAppAPI);
                console.log(promise);

                promise.then(function(data){ 
                      console.log(data);
                })
..........................................................
      const cart = ['shoes', 'pants', 'kurta'];

        createOrder(cart)
          .then(function(orderId) {
            console.log(orderId);
            return orderId;
          })
          .then(function(orderID) {
            return proceedToPayment(orderID)
          })
          .then(function({ message, amt }) {
            console.log(message, 'of amount:', amt);
            return showOrderSummary(message, amt);
          })
          .then(function({ message, amt }) {
            console.log('Your wallet has beed debited by:', amt);
          })
          .catch(function(err) {
            console.log(err.message);
          })
          .then(function() {
            console.log('No matter what happens, I will get executed');
          });



        function createOrder(cart) {
          const pr = new Promise(function(resolve, reject) {
            // create order
            // Validate Cart
            // orderId
            if (!validateCart(cart)) {
              const err = new Error('Cart is not valid!');
              reject(err);
            }
            // logic for createOrder
            const orderId = '12345';
            if (orderId) {
              setTimeout(function() {
                resolve(orderId);
              }, 5000)
            }
          });

          return pr;
        }

      function proceedToPayment(orderID) {
        // Logic for handling payment.
        // This function returns a promise
        return new Promise(function(resolve, reject) {
          // logic
          resolve({ message: `Payment Successful for order id: ${orderID}`, amt: 2500 });
        })
      }

      function showOrderSummary(paymentInfo, amt) {
        return new Promise(function(resolve, reject) {
          // console.log(amt);
          if (amt >= 2000) {
            resolve({ message: 'You have ordered items that cost ${amt} RS', amt });
          } else {
            reject(new Error('Please buy more for discount'));
          }
        })
      }

      function validateCart(cart) {
        // code to validate cart.
        return true;
        // return false;
      }

