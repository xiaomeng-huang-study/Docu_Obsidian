```c++
int* arrayConcat(int* arr1,int length1, int* arr2, int length2)
{
    int arrlength = length1 + length2;

    int* arr = NULL;
    //in C
    //arr = (int*) malloc(sizeof(int)*arrlength);
    //in C++
    arr = new int[arrlength];
    memset(arr,0,sizeof(int)*arrlength);//alles auf 0 setzen <string.h>

    memcpy(arr,arr1,sizeof(int)*length1);
    memcpy((arr+length1),arr2,sizeof(int)*length2);
    return arr;
}
```
