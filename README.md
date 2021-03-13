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



