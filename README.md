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
