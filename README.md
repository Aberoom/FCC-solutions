# FCC-solutions
## Some solutions I coded for the Free Code Camp challenges. 

I write my own code, and sometimes it even looks clean!

If you have any constructive criticism or coding tips I'm always glad to get some feedback. 

Happy coding =)

## _Basic Algorithm Scripting_  
### Challenge "Mutations"  
_Goal_: Return true if the string in the first element of the array contains all of the letters of the string in the second element of the array.

function mutation(arr) {  
  strArr = arr[0].toLowerCase();   
  searchArr = arr[1].toLowerCase();  
  for (var i = 0; i < searchArr.length; i++) {  
    if (strArr.indexOf(searchArr.charAt(i)) == -1) {    
      return false;  
    }  
    return true;  
  }  
}  

### Challenge "Slasher Flick"  
_Goal_: Return the remaining elements of an array after chopping off n elements from the head.  

function slasher(arr, howMany) {  
  var sliceArr = arr.splice(0, howMany);  
  return arr;  
}  

_That was easy... too easy..._


### Challenge "Title Case a Sentence"
_Goal_: Return the provided string with the first letter of each word capitalized. Make sure the rest of the word is in lower case. 

function titleCase(str) {  
  var lowStr = str.toLowerCase();  
  var arrStr = lowStr.split(" ");  
  var strCap = arrStr.map(function(string){  
        return string.charAt(0).toUpperCase() + string.slice(1);  
  });  
  
  strCap = strCap.join(" ");  
  return strCap;  
}  
_First time using a .map() function. Is there a better way?_


### Challenge "Find the Longest Word in a String"
_Goal_: Return the length of the longest word in the provided sentence. Your response should be a number.  

function findLongestWord(str) {  
 var strLength = [];  
 var splitStr = str.split(" ");  
  for (var i = 0; i < splitStr.length; i++) {  
    strLength.push(splitStr[i].length);  
  }  
  strLength.sort(function(a,b){return b-a;});  
  return strLength[0];  
}  


### Challenge "Seek and Destroy"
_Goal_: You will be provided with an initial array (the first argument in the destroyer function), followed by one or more arguments. Remove all elements from the initial array that are of the same value as these arguments.

function destroyer(arr) {  
  var bullet = [];  
  for (var i = 1; i < arguments.length; i++) {  
    bullet.push(arguments[i]);  
  }  
  return arr.filter(function (value) {  
    return bullet.indexOf(value) < 0;  
 });  
}  

### Challenge "Where do I belong"
_Goal_: Return the lowest index at which a value (second argument) should be inserted into an array (first argument) once it has been sorted. The returned value should be a number.

function getIndexToIns(arr, num) {  
  arr.push(num);  
  arr.sort(function (a,b) {  
   return a - b;  
  });  
  return arr.indexOf(num);  
}  

### Challenge "Caesars Cipher"
_Goal_: Write a function which takes a ROT13 encoded string as input and returns a decoded string. All letters will be uppercase. Do not transform any non-alphabetic character (i.e. spaces, punctuation), but do pass them on.

function rot13(str) { // LBH QVQ VG!  
var charCode = "";  
var charCodeArr = [];  
var decoded = "";  
    for (var j = 0; j < str.length; j++) {  
      if (str.charCodeAt(j) < 65) {  
        charCode = str.charCodeAt(j);  
        charCodeArr.push(charCode);  
        } else if (str.charCodeAt(j) < 78) {  
          charCode = 92 - (66 - (str.charCodeAt(j) - 13));  
          charCodeArr.push(charCode);  
      } else {   
      charCode = str.charCodeAt(j) - 13;  
      charCodeArr.push(charCode);      
     }  
    }  
  return String.fromCharCode.apply(0, charCodeArr);   
}  

## Intermediate Algorithm Scripting ##
### Challenge "Sum All Numbers in a Range"  
_Goal_: We'll pass you an array of two numbers. Return the sum of those two numbers and all numbers between them.
The lowest number will not always come first.

function sumAll(arr) {  
  arr.sort(function (a,b) {  
    return a-b;  
  });  
  var sum = 0;  
  var dif = arr[1]-arr[0];  
  for (var i = 1; i < dif; i++){  
    arr.push(arr[1]-i);     
  }  
  for (var j = 0; j < arr.length; j++) {  
    sum += arr[j];  
  }   
  return sum;  
}  

### Challenge "Diff Two Arrays"
_Goal_: Compare two arrays and return a new array with any items only found in one of the two given arrays, but not both. In other words, return the symmetric difference of the two arrays.

Solution 1:
function diffArray(arr1, arr2) {  
  var newArr = [];  
  var theLength = 0;  
  if (arr1.length < arr2.length) {  
  theLength = arr2.length;  
  } else {  
  theLength = arr1.length;  
  }  
  for (var i = 0; i < arr1.length; i++) {  
    for (var j = 0; j < arr2.length; j++) {  
      if (arr1[i] === arr2[j]) {  
        arr1.unshift(arr1[i]);  
        arr2.unshift(arr2[j]);  
        arr1.splice(i + 1, 1);  
        arr2.splice(j + 1, 1);       
      }  
    }  
  }  
  for (var k = 0; k < theLength; k++) {    
      if (arr1[k] !== arr2[k]) {  
        var n = 0;  
        var m = 0;  
        for (n += k; n < arr1.length; n++) {  
          newArr.push(arr1[n]);  
        }  
        for (m += k; m < arr2.length; m++) {  
          newArr.push(arr2[m]);  
        }  
      }  
    }  
  return newArr;  
}  
_//This baby should work with any set of two arrays, no matter the content I could come up with_

Solution 2:  
function diffArray(arr1, arr2) {  
  var nuArr = $(arr2).not(arr1).get();  
  var nuhArr = $(arr1).not(arr2).get();  
  var newArr = nuArr.concat(nuhArr);    
  return newArr;  
}  
_//Wow I can't believe I could have solved that in six lines of code instead of 36..._

### Challenge "Roman Numeral Converter"  
_Goal_: Convert the given number into a roman numeral.   
  
function convertToRoman(num) {  
var tablet = [  
  ["IX", "V", "IV", "I"],  
  ["XC", "L", "XL", "X"],  
  ["CM", "D", "CD", "C"],  
  ["0", "0", "0","M"]   
];  
var scroll = [];  
var scale = String(num).split("").length;  

  for (var j = 0; j < scale; j++) {  
  var div = 1;  
  switch (j) {
    case 0:  
      div = 1;  
      break;  
    case 1:  
      div = 10;  
      break;  
    case 2:  
      div = 100;  
      break;  
    case 3:  
      div = 1000;  
      break;  
  }  
  var remainder = Math.floor((num/div)%10);  
  if (remainder === 9) {  
       scroll.unshift(tablet[j][0]);  
  } else if (remainder >= 5) {  
       remainder %= 5;  
    for (var n = 0; n < remainder; n++) {  
    scroll.unshift(tablet[j][3]);  
  } scroll.unshift(tablet[j][1]);  
  } else if (remainder === 4) {  
       scroll.unshift(tablet[j][2]);  
  } else if (remainder > 0) {  
      for (var i = 0; i < remainder; i++) {  
    scroll.unshift(tablet[j][3]);  
  }  
  }  
  }  

  return scroll.join("");  
}  
_Proud of this one_
 ### Wherefore Art Thou WORK IN PROGRESS
 _Goal_ Make a function that looks through an array of objects (first argument) and returns an array of all objects that have matching property and value pairs (second argument). Each property and value pair of the source object has to be present in the object from the collection if it is to be included in the returned array.
 
   var propSource = Object.keys(source);
  var propColl = [];
   for (var i = 0; i < collection.length; i++) {
     propColl.push(Object.keys(collection[i]));
    for (var j = 0; j < propSource.length; j++) {
      if (propColl[j] == propSource[i]) {
        switch (propSource[i]) {
          case "a":
           
            break;
          case "b":
            
            break;
          case "c":
            
            break;
          case "first":
            
            break;
          case "last":
            
            break;
        }
      }
    }
   }

### Search and Replace
_Goal_ Perform a search and replace on the sentence using the arguments provided and return the new sentence.  
First argument is the sentence to perform the search and replace on.  
Second argument is the word that you will be replacing (before).  
Third argument is what you will be replacing the second argument with (after).  
NOTE: Preserve the case of the original word when you are replacing it. For example if you mean to replace the word "Book" with the word "dog", it should be replaced as "Dog" 

function myReplace(str, before, after) {  
  var splitStr = str.split(" ");  
  for (var i = 0; i<splitStr.length; i++) {  
    if (splitStr[i] == before) {  
      if (splitStr[i][0] == splitStr[i][0].toUpperCase()) {  
        after = after[0].toUpperCase() + after.slice(1);  
      }  
      splitStr.splice(i, 1, after);  
      str = splitStr.join(" ");  
    }  
  }  
  return str;  
}  
