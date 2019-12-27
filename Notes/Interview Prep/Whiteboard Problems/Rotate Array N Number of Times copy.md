# Rotate Array Challenge:

### Rotate Left Michael's Way:
public  int [  ] rotateLeftMichael (int[  ] orig, int shift) {  

int[  ] result = new int[orig.length];  

    for(int i = 0; i < orig.length; i++)  
        if(i < orig.length-shift) 
        result[i] = orig[i+shift];  
    else  
        result[i] = orig[i+shift-orig.length];  
    return result;  
<br>  

___  




### Rotate Left Kievina's Way:
public  int [  ] rotateLeftKievina (int [  ] orig, int shift)  {  

int[  ] result = new int [orig.length]; 

    for(int i = 0; i < orig.length; i++)       
        if(i >= shift)          
        result[i-shift] = orig[i]  
    else  
        result[i-shift+orig.length] = orig[i];  
    return result;  
<br>  

___  



## Rotate to The Right:

### Rotate Right Michael's Way:
 
public  int [  ] rotateRightMichael (int [  ] orig, int shift) {  

int[  ] result = new int[orig.length];  

    for(int i = 0; i < orig.length; i++) 
        if(i >= d)  
        result[i] = orig[i-shift];  
    else  
        result[i] = orig[i-shift+orig.length];  
    return result;  
<br>  

___  



### Rotate Right Kievina's Way:

public  int [  ] rotateRightKievina (int [  ] orig, int shift)  

int[  ] result = new int[orig.length];  


    for(int i = 0; i < orig.length; i++)  
        if(i < orig.length-shift)  
        result[i+shift] = orig[i];  
    else  
        result[i+shift-orig.length] = orig[i];  
    return result;



