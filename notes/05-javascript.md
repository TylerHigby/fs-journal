# JavaScript

Don't use link to include javascript
<script src="app.js"></script>
load scripts at the bottom of the body because it loads last.

creating variables
<!-- primitive data type -->
<!-- numbers -->
let x = 1
let y = -1
let z = 1.1

<!-- strings(' ' or " ") -->
let greeting = 'hello'
let othergreeting = "Jeremy's lie was that he has 6 cats"

<!-- booleans -->
let boolean = true
let otherboolean = false

<!-- truthy falsey -->
let falseNumber = 0
let trueNumber = (any other number)

let falseString = ''(nothing between the quotes)
let trueString = ''(any string with any character becomes true)

let moreFalse = undefined
let anotherFalse = null

let moreTrue = [] (even if an array is empty they are seen as true)
let anotherTrue = {} ()

<!-- no values -->
let noValue (undefined, I don't know there's no value)
DO NOT DO let unknown value = undefined
Let KnownNothing = null (I know theres is no value)

<!-- //SECTION - reference data types -->
let arr = ['jack sparrow' , 'Black Beard' , 'Luffy']
(arr[0] = jack sparrow)
let nums = [1,3,6,8]
let mixed = ['howdy' , 589 , true]

<!-- Object store data using Key : VALUE pairs (order is irrelevant)-->
let obj = {
  dog: 'Dipper';
  cat: 'Georgie';
  bird: 'Kevin';
  weasel: 'Briggs';
}

<!-- //!SECTION functions -->
<!-- functions are blocks of code to store and run later -->
function sayHello(){
  console.log('hello there')
}

<!-- Parameters -->
<!-- temporary variables accessible to only this function while it's executing -->
function addNumber(x , y){
  console.log(x , y)
  console.log(x + y)
  return x + y
}

<!-- //SECTION - App Time -->
function clickButton(){
  console.log('clicked button')
}

link bootstrap,style,mdi
script app.js

const creates a variable that can't be changed.

control + ~ toggles terminal


