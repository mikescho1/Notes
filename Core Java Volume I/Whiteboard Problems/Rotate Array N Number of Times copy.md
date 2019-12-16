#### Rotate Array  N Number of Times:
###### Given an int array of size x, rotate n number of times to left:  

public int[] rotLeftVersion1(int[] a, int n) {
    int[] result = new int[origArr.length];
    for(int i = 0; i < a; i++) {
        if(i >= n)
        result[i-n] = origArr[i];
        else
        result[i-n+origArr.length] = origArr[i];
    }
    for(int n: result)
    System.out.print(n + " ");
}
// d rotations to the left
public int[] rotLeftVersion2(int[] a, int d) {
int[] result = new int[a.length];
for(int i = 0; i < a.length; i++) {
    if(i < a.length - d)
        result[i] = a[i+d];
    else
        result[i] = a[i+d-a.length];
}
return result;
}
//---------------------------------------------------------//
// n rotations to the right
public int[] rotateRightVersion1(int[] a, int n) {
    int[] result = new int[a.length];
    for(int i = 0; i < a.length; i++) {
        if(i < a.length-n)
        result[i+n] = a[i];
        else
        result[i+n-length] = a[i];
    }
    for(int n: result)
    System.out.print(n + " ");
}
// d rotations to the right
public int[] rotRightVersion2(int[] a, int d) {
    int[] result = new int[a.length];
    for(int i = 0; i < a.length; i++) {
        if(i >= d)
            result[i] = a[i-d];
        else
            result[i] = a[i-d+a.length];
    }
    return result;
}
