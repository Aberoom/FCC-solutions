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
