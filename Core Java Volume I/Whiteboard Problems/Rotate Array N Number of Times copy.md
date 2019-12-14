#### Rotate Array  N Number of Times:
###### Given an int array of size x, rotate n number of times to left:  
Logic:  
if i is greater than or equal to n:  
* result[i-n]   

else
if i is less than n:  
* result[i-n + length] 


###### Given an int array of size x, rotate n number of times to right:  
Logic:    

if(i\<length-n):  
* result[i+n]
  
else
* result[i+n-length]
