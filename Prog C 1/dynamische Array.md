```c++
int* arrayConcat(int* arr1,int length1, int* arr2, int length2)
{
    int arrLength = length1 + length2;

    int* newArr = NULL;
    if(env == c)
    {
	    newArr = (int*) malloc(arrLength*sizeof(int));
    }
    if(env == cpp)
    {
	    newArr = new int[arrlength];
    }
    //memset(newArr,0,sizeof(int)*arrLength);
	    //alles auf 0 setzen <string.h>
	
    //memcpy(newArr,arr1,sizeof(int)*length1);
    //memcpy((newArr+length1),arr2,sizeof(int)*length2);
    for(int i = 0; i<length1; i++)
    {
	    newArr[i] = arr1[i];
    }
    for(int i =0; i<length2; i++)
    {
	    newArr[i+length1] = arr2[i];
    }
    return newArr;
}
```
