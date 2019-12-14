#### Rotate Array to Left N Number of Times:
###### Given an int array of size x, rotate n number of times to left:  
Logic:  
if i is greater than or equal to n:  
* result[i] = arr[i - n]  

if i is less than n:  
* result[i] = arr[arr.length - (n+i)]  
