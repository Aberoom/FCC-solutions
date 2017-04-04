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
_//This baby should work with any set of two arrays, no matter the content I could come up with
