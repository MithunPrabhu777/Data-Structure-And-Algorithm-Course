# Data-Structure-And-Algorithm-Course

22hrs course 
Reference by COLT STEELE

20 minutes per day 
1hr of completion in 3 days
10hr in 30days
20hr in 60days
2hr in 6days
total on an average 3 months journey

Day - 1 

what we are covering in this course

Big O notation
Analyzing performance of arrays and objects
problem solving approach/patterns
Recursion
searching algorithms
sorting algorithms - bubble sort,selection sort,insertion sort,merge sort,quick sort,radix sort
Intro to data structures-singly linked list,doubly linked list,stacks and queues,binary search trees,tree traversal,binary heaps,hash tables,graphs,graph traversal
dijkstra's algorithm

A note on js snippets
open google chrome click ctrl+shift+i      // js bin , codepen you can use not a issue
go to sources     
on left top corner open snippets and write code
created folder called demo_snippet
console.log("hello from snippet"); //for output go down and hit play
//output is string and undefined

    CHAPTER-1

    1.Big-O Notation


    WARNING THIS SECTION CONTAINS SOME MATHS DONT WORRY ,WE'LL SURVIVE.
    
    objectives:
    motivate need for something like big o notation
    describe,simplify,define and evaluate time-complexity, space-complexity
    describe what logarithm is.
    
    
    IDEA: We can have multiple implementations of same function.
    
    which is best??
    
    write a function that accepts a string input and returns a reversed copy.
    
    //Stack Overflow
    you will get 10 different implementations in javascript and all are different
    so which one is best????????????????????????
    
    Why does is matter??? i.e Performance
    
    If u are working with great dataset which could save an hour with best code, bootcamp ,codecamp is required.
    

  Day -2 

//one approach for above problem   //all code are in chrome console //created as snippet.
function addup(n){
	let total = 0;
	for(i=1;i<=n;i++){
	total+= i;
	}
	return total;
}

console.log(addup(6));

//One more approach for this problem

function addup(n){                      ////how it works     6 * (7) / 2  -----  3.5 * 6  ----- 21  ////is it better code than previous one????? ///doesnt depend on code length 
return n * (n+1) / 2;                  ////depends on code performance.  //// or less-memoery used /// more readable  //// ?????
}                                      ///performance of this code better compared above code.!!!
console.log(addup(6));

to check ceck performance for each code use performance.now();  ////crazy right......its in code snippet

Problem with time
1.different machines will record different times.
2.same machines will record different times
3.for fast algorithms,,speed measurements may not be precise enough.

rather than counting seconds lets count number of simple operations computer has to perform.         //////  Great right!!!!!!!

counting operations

function addup(n){                       
return n * (n+1) / 2;                  //// 1.multiplication 2.addition 3. division    ///no. of opeartions 3
}        



function addup(n){
	let total = 0;
	for(i=1;i<=n;i++){
	total+= i;
	}                              //////  1.for loop with + opeator   ////its huge if u give 5 ,,, 5 number of operations ,,,, if 10000000 ---- 1000000 no. of 
	return total;                                opearions,,,coollll!!!!!!!    counting is hard here /// grows proportinaolyy with n.
}


Day - 3

Introducing....Big O

It allows us to talk formally about how the runtime of an algorithm grows as the input grow.

Definition: O(f(n)) if number of simple operations computer has to do is eventually less than a constant times f(n),as n increases

f(n) could be linear = n
f(n) could be quadratic = n^2
f(n) could be constant = 1
f(n) could be something different.

Above example second code having 3 operations which won't change if value of n increases so u can consider this as O(1) ---- constant
First code number of operations will increase as n increases in linear format so u can consider this as O(n)  ----- Linear

Another Example

function countUpAndDown(n){
    console.log("Going Up!!!");
    for(let i=0;i<n;i++){                              //////   O(n)
        console.log(i);
    }                                                                                     O(2n)  eventually  2 doesn't matter so will take it as O(n)
    console.log("At the top!\n Going down...");
    for(let j= n-1; j>=0;j--){                       ///////   O(n)   
        console.log(j);
    }
    console.log("Back down.Bye!");
}

countUpAndDown(10);

OMG MOAR EXAMPLEZ

function printAllPairs(n){
for(var i=0;i<n;i++){                 //// O(n)    nested inside for loop so O(n^2)  
    for(var j=0;j<n;j++){             //// O(n)            
        console.log(i,j);
    }
}
}

printAllPairs(10);

Simplifying Big O Expressions

when determining time complexity of algorithm, there are some helpful rule of thumbs for big O expressions

These rules of thumb are consequences of definition of big O notation.
1.Constants don't matter  ----  O(2n) = O(n)  ---- O(500) = O(1)
2.Smaller Terms don't matter ----- O(n+10) = O(n)  ,  O(1000n + 50 ) = O(n) ,,,,,,     O(n^2 + 5n + 8) = O(n^2)

Big O shorthands
1.Arithematic operations are constant
2.variable assignment is constant
3.accessing elements in array(by index) or object (by key) is constant.
4.In a loop, complexity is length of loop times complexity of whatever happens inside loop.

One more example

function logAtLeast5(n){
 for(var i=1;i<=Math.max(5,n); i++){        /////  O(n) time complexity
     console.log(i); 
 }
}

logAtLeast5(10);


function logAtMost5(n){
 for(var i=1;i<=Math.min(5,n); i++){        /////  O(5) === O(1)-- constant time complexity
     console.log(i); 
 }
}

logAtMost5(10);

Day - 4

Space Complexity

so far, we have been focusing on time complexity: how can we analyze runtime of an algorithm as size of the inputs increases?
we can also use big O notation to analyze space complexity:how much additional memory do we need to allocate in order to run code in our algorithm??

what about inputs???

sometimes we hear term auxillary space complexity to refer to space requried by algorithm, not including space taken up inputs.

Space complexity in JS(Rules of thumb)
1. Most primitives (booleans,numbers,undefined,null) are constant space.
2. Strings require O(n) space (n is string length)
3. Refrence types are generally O(n), where n is length (for arrays) or number of keys(for objects)

An Example

function sum(arr){
    let total = 0;                             ////Now we are talking about space complexity i.e here we have only 2 numbers total and i  ---- have constant space --
    for(let i=0;i<arr.length;i++){           ///  even if u give million of elements in array it wont take much space in total.
        total+=arr[i];
    }
return total;
}

sum([2,4,5,1,3]);

Another Example

function double(arr){                      ///// new Array   its getting longer as number of input increases,,, as array size increases. O(n) space --- n numbers.
let newArray = [];
for(let i=0; i< arr.length;i++){
    newArray.push(2 * arr[i]);
}
return newArray;
}

double([2,3,4,5,6,7,8,9,0]);

LOGARITHMS

common complexities are O(1),O(n),O(n^2).
some have complex mathematical expressions.

What's a log again???

It's a inverse of exponentiation.   -------  log2(8) = 3  -------   which means that base 2 to the power of 3 is 8.

log2(value) = exponent -------->  2^exponent = value

we'll omit the 2  ----->     log === log2

What??????

This isn't a amth coure,so here's a rule of thumb.

The logarithm of a number roughly measures the number of times you can divide that number by 2 before you get a value that's less than or equal to one.

Logarithm Examples: 8 is the value ----  8/2 - 4,  4/2 - 2 , 2/2 - 1 ,,3 times divided the number 8 so log of 8  is 3.

find the log of 25  ------   25/2=12.5  ---  12.5/2 ---- 6.25/2 --- 3.125/2 --- 1.5625/2 ---- 0.78125  SO log of 25 is inbetween 1.5625 - 0.78125 i.e 4.64.

Logarithmic time complexity is great!!!!!

Who Cares???

Certain searching algorithms have logarithmic time complexity.
Efficient sorting algorithms involve logarithms.
Recursion sometimes involves logarithmic space complexity.

BUILT IN DATA STRUCTURES through lens of Big-O

Let's spend a couple of minutes analyzing things we do all time in JS:Working with Arrays,Objects and built-in methods.

Objectives:
1.Understand how objects and arrays work, through the lens of Big-O
2.Explain why adding elements to beginning of array is costly.
3.Compare and Contrast runtime for arrays and objects,as well as built-in methods.

OBJECTS(unordered,key value pairs!!!)

let instructor = {
firstName:"kelly",
isInstructor:true,
favoriteNumbers:[1,2,3,4]
}

When to use objects:
1.when you don't need order
2.when you need fast access/insertion and removal.

Big-O of Objects ---- When you don't need any ordering,objects are an excellent choice!!!

Insertion - O(1)
Removal - O(1)
Searching - O(N)
Access - O(1)

Big O of Object Methods
1.Object.keys - O(N)
2.Object.values - O(N)
3.Object.entries - O(N)
4.hasOwnProperty - O(1)

ARRAYS ------ Ordered lists!!!

let names = ["Michael","Melissa","Andrea"];

let values = [true,{},[],2,"awesome"];

when to use arrays 
1.when you need order
2.when you need fast access/insertion and removal(sort of.....)

Big O of Arrays
Insertion - It depends...
Removal - It depends....
Searching - O(N)
Access - O(1)

Accessing elements in arrays is constant task
Inserting element at the end is not a big issue
but inserting element at the begining is big task because ,,, u have to again assign index to each and every elements in array.
Same Deleting also.

Big O Array Operations
1.push - O(1)
2.pop - O(1)
3.shift - O(N)
4.unshift - O(N)
5.concat - O(N)
6.slice - O(N)
7.splice - O(N)
8.sort - O(N*log N)
9.forEach/map/filter/reduce/etc - O(N)

For more details -------    https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat

ALGORITHMS And PROBLEM SOLVING PATTERNS

OBjectives
1.Define what algorithm is
2.Devise plan to solve algorithms
3.Compare and contrast problem solving patterns including frequency counters,two pointer problems and divide and conquer.

What is an algorithm??  -----  A process or set of steps to accomplish a certain task.

Why do I need to know this???
Almost everything that you do in programming involves some kind of algorithm!!
It is foundation for being a successful problem solving developer.

How Do You Improve????????????????????????????
1.Devise a plan for solving problems.
2.Master common problem solving patterns.

Problem Solving Strategies:
1.Understand the problem
2.Explore Concrete Examples
3.Break It Down
4.Solve/Simplify
5.Look Back and Refactor

	1.Understand the Problem:
	1.Can I restate the problem in my own words?
	2.What are the inputs that go into the problem??
	3.What are the outputs that should come from solution to problem?
	4.Can the outputs be determined from the inputs?? In other words, do I have enough information to solve problem?
	5.How should I label important pieces of data that are part of problem??

	Write function which takes two numbers and returns their sum.
	1.Implementing addition of two numbers
	2.Inputs may be in Integer,Float,Double,String
	3.Output may result in Float,Double or iNteger
	4.Yes 
	5.Num1 and Num2 as input ,,, function is called as sum ,,, output will be returned.

2.Explore Examples
	1.Start with simple examples
	2.Progress to more complex examples
	3.Explore Examples with empty inputs
	4.Explore examples with invalid inputs

Write a function which takes in a string and returns counts of each character in string.

function stringLength(str){
count = 0;
for(let i=0;i<str.length;i++){
  count+=1                              //// this is solution for length of string and is wrong solution for above question so what is the solution?????
}
return count;
}
stringLength("mithun is great");


////check all these in the snippet section in chrome browser.

3.Break it Down

	1.Explicitly write out the steps you need tot take.
	2.This forces you to think about code you will write before you write it, and helps you to catch any lingering conceptual issues or misunderstandings before you dive in and have to worry about details.(language syntax as well).





