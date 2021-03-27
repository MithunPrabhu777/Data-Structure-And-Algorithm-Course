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

	1.Explicitly write out the steps you need to take.
	2.This forces you to think about code you will write before you write it, and helps you to catch any lingering conceptual issues or misunderstandings before you dive in and have to worry about details.(language syntax as well).

Day - 5

Write a function which takes in a string and returns counts of each character in string.

Every changes or pseudo code written in browser snippet

4.SOLVE THE PROBLEM ---- if you cannot Solve a simpler problem.

SIMPLIFY
1.Find core difficulty in what you are trying to do
2.Temporarily ignore that difficulty
3.write a simplified solution
4.then incorporate difficulty back in

Step 5: Look Back and Refactor
1.Can you check the result?
2.can you derive result differently??
3.can u understand it at a glance??
4.can you use result or method for some other problem?
5.can you improve performance of your solution??
6.can you think of other ways to refactor??
7.How other people solved this problem??

Day - 6

All the things mentioned in snippet.

/*function charCount(str){
 let obj = {};
 for(let i=0;i<str.length;i++){
     let char = str[i].toLowerCase();
     if(/[a-z0-9]/.test(char)){
         if(obj[char] > 0){
             obj[char]++;
         }else{
             obj[char] = 1;
         }
     }
 }
 return obj;
}

charCount('Hello 1223jdj');
*/
//If you are not a fan of for loop ,,,you can use this....

/*function charCount(str){
 let obj = {};
 for(let char of str){
     char = char.toLowerCase();
     if(/[a-z0-9]/.test(char)){
         if(obj[char] > 0){
             obj[char]++;
         }else{
             obj[char] = 1;
         }
     }
 }
 return obj;
}

charCount('Hello 1223jdj');

*/

/*
function charCount(str){
 let obj = {};
 for(let char of str){
     char = char.toLowerCase();
     if(/[a-z0-9]/.test(char)){
         obj[char] = ++obj[char]  || 1;
     }
 }
 return obj;
}

charCount('Hello 1223jdj');

*/

//if u use regular expressions in code then performace will be reduced.so below one is better code for performancebut it is lengthier one.
function charCount(str){
 let obj = {};
 for(let char of str){
     char = char.toLowerCase();
     if(isAlphaNumeric(char)){
         obj[char] = ++obj[char]  || 1;
     }
 }
 return obj;
}


function isAlphaNumeric(char){
    let code = char.charCodeAt(0);
    if(!(code > 47 && code < 50) && !(code>64 && code <91) && !(code >96 && code <123)){
        return false
    }
    return true
}

charCount('Hello 1223jdj');

HOW DO YOU IMPROVE????

1.Devise a plan for solving problems
2.Master common problem solving patterns

Problem Solving Patterns

some patterns:
1. frequency counter
2. multiple pointers
3. sliding window
4. divide and conquer
5. dynamic programming
6. greedy algorithm
7. backtracking
8. many more!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

1.Frequency Counters
This pattern uses objects or sets to collect values/frequencies of values.
This can often avoid need for nested loops or O(N^2) operations with arrays/strings

AN Example

Day -7
 
Write function called same, which accepts two arrays. function should return true if every value in array has it's corresponsing value squared in second array. frequency of values must be same.

same([1,2,3],[4,1,9]) //true
same([1,2,3],[1,9]) //false
same([1,2,1],[4,4,1])  // false

function same(arr1,arr2){
    if(arr1.length !== arr2.length){
        return false
    }
    for(let i=0; i < arr1.length;i++){
        let correctIndex = arr2.indexOf(arr1[i] ** 2);
        if(correctIndex === -1){
            return false;
        }
        arr2.splice(correctIndex,1);
    }
    return true
}


same([1,2,3,1],[4,9,1,1]);  //Time Complexity - N^2  // indexOf is considered as one more loop. ///It is called Naive approach.

Another approach is refactored(Time Complexity --- O(n))

function same(arr1,arr2){
    if(arr1.length !== arr2.length){
        return false;
    }
    let frequencycounter1 = {};
    let frequencycounter2 = {};
    for (let val of arr1){
       frequencycounter1[val] = (frequencycounter1[val] || 0) + 1;
       console.log(frequencycounter1[val]);
    }
    for(let val of arr2){
        frequencycounter2[val] = (frequencycounter2[val] || 0) + 1;
        console.log(frequencycounter2[val]);
    }
    console.log(frequencycounter1);
    console.log(frequencycounter2);
    for(let key in frequencycounter1){
        if (!(key ** 2 in frequencycounter2)){
            return false;
        }
        if(frequencycounter2[key ** 2] !== frequencycounter1[key]){
            return false;
        }
    }
return true;
}


                                   // It's effienciency very high compared to previous example O(n)

same([1,2,3],[1,4,9]);

----------********************-----------------------

ANAGRAMS
Given Two stringss, write function to determine if second string is anagram of first. anagram is word,phrase or name formed by rearrangingletters of another such as cinema,formed from iceman.

validAnagram('','') //true
validAnagram('aaz','zza')  //false
validAnagram('anagram','nagaram')  //true
validAnagram('rat','car')   //false
validAnagram('awesome','awesom') //false
validAnagram('qwerty','qeywrt') // true
validAnagram('texttwisttime','timetwisttext') //true


--------------------************************-------------------------------------------

Day - 8

Every code in code snippet

function validAnagram(str1,str2){
if(str1.length !== str2.length){
    return false
}

let lookup = {};

for (let i=0; i<str1.length;i++){
     let letter = str1[i];
     lookup[letter] ? lookup[letter]+=1 : lookup[letter] = 1;
}

for(let i=0;i<str2.length;i++){
    let letter = str1[i];
    if(!lookup[letter]){
        return false;
    }
    else {
        lookup[letter] -= 1;
    }
}
return true;
}

validAnagram("anagram","nagaram")


--------------*******************--------------

Multiple Pointers

Creating pointers or values that correspond to index or position and move towards beginning,end or middle based on on a certain consition.
very efficient for solving problems with minimal space complexity as well

An Example:

Write function called sumZero which accepts a sorted array of integers. function should find first pair where sum is 0. return array that includes both values sum to zero or undefined if pair does not exist.

sumZero([-3,-2,-1,0,1,2,3])  //[-3,3]
sumZero([-2,0,1,3]) //undefined

function sumZero(arr){
for(let i=0;i<arr.length;i++){
    for(let j=i+1;j<arr.length;j++){
        if(arr[i] + arr[j] === 0){
            return [arr[i],arr[j]];
        }

    }
    console.log([arr[i],arr[j]])
}
}

sumZero([-2,1,2,3]);

//time complexity O(n^2)
//space complexity O(1)

REFACTOR----------------

function sumZero(arr){
    let left = 0;
    let right = arr.length - 1;
    while(left < right){
        let sum = arr[left] + arr[right];
        if(sum === 0){
            return [arr[left],arr[right]];
        }
        else if(sum > 0 ){
            right--;
        }
        else{
            left++;
        }
    }

}                                         //Refactored

sumZero([-4,-3,-1,1,3,3]);


-----countUniqueValues----

Implement function called countUniqueValues which accepts sorted array, and counts unique values in array. there can be negative numbers in array, but it will alwasys be sorted.

countUniqueValues([1,1,1,1,1,2]);  //2
countUniqueValues([1,2,3,4,4,7,7,12,12]); //6

Day - 9

function countUniqueValues(arr){
    let i = 0;
    for(let j =1;j<arr.length;j++){
        if(arr[i] !== arr[j]){
            i+=1;
            arr[i] = arr[j];
        }
        console.log(arr[i],arr[j]);
    }
    return i+1;
}

countUniqueValues([1,1,2,3,3,4,5,6,6,7]);

------------------------------************************--------------------------

SLIDING WINDOW::

This pattern involves creating a window which can either be array or number from one position to another

Depending on certain condition, window either increases or closes

very useful for keeping track of subset of data in array/string etc.

An Example::

Write a function called maxSubarraySum which accepts array of integers and number called n. function should calculate maximum sum of n consecutive elemets in array.

maxSubarraySum([1,2,5,2,8,1,5],2);  // 10
maxSubarraySum([1,2,5,2,8,1,5],4);  // 10
maxSubarraySum([],4);  //null

function maxSubarraySum(arr,num){
if(num > arr.length){
    return null;
}
let max = -Infinity;
for(i=0;i<arr.length-num+1;i++){
    let temp = 0;
    for(let j=0;j<num;j++){
        temp+=arr[i + j];
    }
    console.log(temp,max);
    if(temp > max){
         max = temp
    }
}                                         // Very bad approach of solving problem O(n^2)
return max;
}

maxSubarraySum([2,6,9,2,1,8,5,6,3],3);


------------------Refactor::::::::::::::::

Same question with better solution -----------  O(n)

function maxSubArraySum(arr,num){
let maxSum = 0;
let tempSum = 0;
if(arr.length < num){
    return null
}
for(let i=0;i<num;i++){
    maxSum +=arr[i];
}

tempSum = maxSum
for(let i=num;i<arr.length;i++){
    tempSum = tempSum - arr[i-num] + arr[i];
    maxSum = Math.max(maxSum,tempSum);
}
return maxSum;
}

maxSubArraySum([1,2,3,2,3,1,2,3,4,3,1],3);

------------------------**********************------------------------

Divide and Conquer:::

This pattern involves dividing data set into smaller chunks and then repeating process with subset of data.
This pattern can tremendously decrease time complexity.

search([1,2,3,4,5,6],4)  // 3
search([1,2,3,4,5,6],6)  //5
search([1,2,3,4,5,6],11) // -1

-----------------------------*********************------------------------

Day - 10

Normal Code::::

function search(arr,num){
    for(let i=0;i<arr.length;i++){
        if(num == arr[i]){
            return i;
        }
    }
}

search([1,5,3,4,7,8],7);

-------------------************---------------

Refactor::::

Binary Search:::

Time Complexity:::: log(N)

function search(array,val){
let min = 0;
let max = array.length - 1;

while(min<=max){
    let middle = Math.floor((min+max)/2);
    let currentElement = array[middle];

    if(currentElement < val){
         min = middle + 1;
    }
    else if (currentElement > val){
        max = middle - 1;
    }
    else{
        return middle;
    }
}
return -1
}


search([2,3,4,5,6,7,8,9,10,11,12,14,15,17,19],14);

----------------------------*********************--------------

Recursion::::

Objectives----

1.Define what recursion is and how it can be used
2.understand two essential components of recursive function
3.visualize call stack to better debug and understand ecursive functions.
4.use helper method recursion and pure reciursion to solve more difficult problems.

what is recursion???

A process (a function in our case) that calls itself.

1.JSON.parse/JSON.stringify
2.document.getElementById and DOM traversal algorithms
3.Object Traversal
4.we will see it with more complex data structures.
5.It is sometimes cleaner alternative to iteration.

But let's talk about functions
In almost all program languages,there is built in DS that manages what happens when functions are invoked.Javascript calls THE CALL STACK.

The Call Stack
It is stack data structure- we will talk about that later!!!
Any time function is invoked it is placed(pushed) on top of call stack
When javascript sees return keyword or when function ends, compliler will remove(pop).

function takeShower(){
    return "Showering"
}

function eatBreakfast(){
    let meal = cookFood();
    return `Eating ${meal}`
}

function cookFood(){
    let items = ["Oatmeal","Eggs","Protein Shake"]
    return items[Math.floor(Math.random()*items.length)];
}

function wakeUp(){
    takeShower();
    eatBreakfast();
    console.log("OK ready to go to work!!!")
}

wakeUp()

Day - 11

//Just go to browser console and hit the break point you want and see what happens in call stack. NOTE:Run Code before checking call stack. --- ctrl+Enter

Why do I care for recursion???

1.You're used to functions being pushed on call stack and popped off when they are done.
2.When we write recursive functions,we keep pushing new functions onto call stack.

How recursive functions work???
Invoke same function with a different input until you reach your base case!!!

This is most important concept to understand.

Two esssential parts of recursive funtion!!!!
1.Base case
2.Different Inputs

Our first recursive function.

function countDown(num){
if(num <= 0){
    console.log("ALL DONE!!!");
    return;
}
console.log(num);
num--;
countDown(num);
}

countDown(5);

Another code with different approach!!!

function countDown(num){
for(let i = num;i>0;i--){
    console.log(i);
}
console.log("All Done");
}

countDown(5);
 ------------------**************----------------------
 
Our second recursive function

can you spot base case???
Do you notice different input???
What would happen if we didn't return???

function sumRange(num){
if(num === 1) return 1;
return num + sumRange(num-1);
}

sumRange(4);

Day-12 and Day-13 leave

-----------------*******************-----------------------

Day -14

Now about factorial recursion

function factorial(num){
if(num === 1) return 1;
return num * factorial(num-1);
}

factorial(4);

------------------**************---------

factorial normal code

function factorial(num){
let total = 1;
for(let i=num; i>=1;i--){
    total*=i;
}
return total;
}

Where things go wrong

1.No Base.
2.Forgetting to return or returning the wrong thing.
3.STACK OVERFLOW -------    I.E     using console.log instead of return //maximum call stack exceedded

-------------------****************---------------------

HELPER METHOD RECURSION
Helper method recursion will be used in storing value in form of array.

Another Example

Let's try to collect all of odd values in array.

function collectOddValues(arr){
let result = [];

function helper(helperInput){
if(helperInput.length === 0){
    return
}

if(helperInput[0] % 2 !== 0){
    result.push(helperInput[0])
}

helper(helperInput.slice(1))
}

helper(arr)

return result;

}

collectOddValues([1,2,3,4,5,6,7,8,9]);

---------------------************************---------------------------

PURE RECURSION:::::::::::

Pure Recursion Tips:  
1.For arrays, use methods like slice,spread operator and concat that make copies of arrays so you don not mutate them.
2.Remember that strings are immutable so you will need to use methods like slice,substr or substring to malke copies of strings.
3.To make copies of objects use Object.assign or spread operator.

function collectOddValues(arr){
let newArray = [];

if (arr.length === 0){
    return newArray;
}

if(arr[0] % 2 !== 0){
    newArray.push(arr[0]);
}

newArray = newArray.concat(collectOddValues(arr.slice(1)));
return newArray;
}


collectOddValues([1,2,3,4,5,6,7,8,9]);

-----------------------------************************----------------------------------

Searching Algorithms------

var usernames = ["tommy","mithun","manoj","palli","cricketta"]

usernames.indexOf('palli'); //3

usernames.indexOf('madhav') //-1

Objectives----

1.Describe what searching algorithm is
2.Implement linear search on arrays
3.Implement binary search on sorted arrays
4.Implement naive string searching algorithm
5.Implement KMP string searching algorithm.

How do we search???

Given an array, simplest way to search for value is to look at every element in array and check if it is value we want.

Javascript has search!!!

There are many different search methods on arrays in javascript:
1.indexOf
2.includes
3.find
4.findIndex

But how do these functions work???

usernames.includes('mithun') //true

Linear Search PseudoCode
1.This function accepts array and value
2.Loop through array check if current array element is equal to value
3.if it is,return index of elemnt at which it is found
4.I fvalue is never found ,return -1

function linearSearch(arr,num){
for(let i=0;i<arr.length;i++){
    if(arr[i] === num){
        return i
    }
    continue
}
    return -1;
}

linearSearch([6,4,8,1,0,3],5);

----------------------

Linear Search Big O
--------------------
O(1) ---- Best
O(n) ---- Worst
O(n) ---- Average

Binary Search
--------------
1.Binary search is much faster form of search
2.Rather than eliminaating one element at a time,you can eliminate half of the remaining elements at atime.
3.Binary search only works on sorted arrays!!!

Concept behind binary searching is divide and conquer method.

Divide And Conquer
--------------------

Binary Search Pseudocode
-------------------------
1.this function accepts a sorted array and a value
2.Create a left pointer at start of array and a right pointer at end of array.
3.While left pointer comes before the right pointer.
    1.Create a pointer in middle
    2.If you find value you want,return index
    3.If value is too small,move left pointer up
    4.If value is too large,move right pointer down.
4.If you never find the value,return -1.


function search(array,val){
let min = 0;
let max = array.length - 1;

while(min<=max){
    let middle = Math.floor((min+max)/2);
    let currentElement = array[middle];

    if(currentElement < val){
         min = middle + 1;
    }
    else if (currentElement > val){
        max = middle - 1;
    }
    else{
        return middle;
    }
}
return -1
}


search([2,3,4,5,6,7,8,9,10,11,12,14,15,17,19],14);

Day - 15

Binary Search ---  worst anfd average case O(logn) 
                   best case O(1)
		   
Suppose we are searching for element in array of length 16 but element not in the array 

16 elements = 4 steps

To add another "step", we needto double number of elements

total 32 elements = 5 steps

-------------------------**********---------------

Naive String Search
-------------------

Long String: wowomgzomg              Short String: omg

wowomgzomg  ---- count 2

Suppose you want to count number of times substring enccountered in main string


Pseudocode:
1.Loop over longer string
2.Loop over shorter string
3.If characters do not match,break out of inner loop.
4.If characters do match,break out of inner loop
5.If you complete inner loop and find match,increment count of matches
6.return count.

function naiveSearch(long,short){
    let count = 0;
    for(let i=0;i<long.length;i++){
        for(j = 0;j<short.length;j++){
            console.log(long[i+j],short[j]);
            if(short[j] !== long[i+j]) break; 
            if(j === short.length - 1) count++;
        }
    }
    return count;
}

naiveSearch("lolie loled","lol");

ELementary Sorting Algorithms:
------------------------------

Sorting is process of rearraging items in collection (e.g array) so that items are in some kind of order.

Examples:
1.Sorting numbers from smallest to largest
2.sorting names alphabetically
3.Sorting movies based on release date.

Why do we need to learn this???
1.Sorting is incredibly common task,so it is good to know how it works
2.There are many different ways to sort things, and different tehniques have their own dvantages and disadvantages.

Objectives::
1.Implement bubble sort
2.Implement selection sort
3.implement insertion sort
4.Understaand why it is important to learn these simpler sorting algorithms.

Javascript has a sort method...
-------------------------------

Yes,it does!!!!
...but it doesn't always work the way you expect

['sttele',"colt","DS","Algorithms"].sort();

//It will give back sorted array

[6,4,15,10].sort();

//[10,15,4,6]  /// Not properly sorted.//unicode represents string so every item is converted into string. then it is sorted so it is bizarre.

Telling Javascript how to sort
------------------------------
1.Built-in sort method accepts optional comparator function
2.you can use this comparator function to tell javascript how you want it to sort.
3.comparator looks at pairs of elements (a and b),determines their sort order based on return value.
       1.If it returns negative number,a should come before b.
       2.If it returns a positive number, ashould come after b.
       3.If it returns 0,a and b are same as far as sort is concerned.

Telling Javascript how to sort

Examples::
-----------

function numberCompare(num1,num2){
return num1 - num2;
}

[6,4,15,10].sort(numberCompare)    // [4,6,10,15]

-----------------------------------

function compareByLen(str1,str2){
return str2.length - str1.length;
}

["Steele","Colt","DS","Algo"].sort(compareByLen)       //ordering it by length of string.

BUBBLESORT
-----------

A sorting algorithm where largest values bubble up to top!!!

