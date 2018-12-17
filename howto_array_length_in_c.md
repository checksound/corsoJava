# Come calcolare la lunghezza di un array in C

Il paragone con un linguaggio come Java, mostra quanto è più laboriosa la medesima operazione.

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{
    int arr[] = {1,2,3,4,5};
    int length = sizeof(arr)/sizeof(int); //length of an integer array.
    printf("length = %d",length);
}
```