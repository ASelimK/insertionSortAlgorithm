# insertionSortAlgorithm
Basic insertion sort algorithm
#include <stdio.h>
#include <stdlib.h>



void insertionSort(int array[]){
    int length = 17;//sizeof(array)/sizeof(int); //Neden çalýþmadýðýný anlamadým size of arrayi 4 olarak alýyor.
    printf("sizes: %d  %d\n", sizeof(array), sizeof(int));

    for (int j = 1; j < length; j++){
        int key = array[j];
        int i = j - 1;
        while( i > 0 && array[i]> key){
            array[i+1] = array[i];
            i--;
        }
        array[i+1] = key;
    }

int main()
{
    ///---------------GETTING INPUT AND PUTTING IT INTO ARRAY-----------------
    FILE *input;
    char fileName[50];
    int data = 0;
    int dataArrayLength = 0;

    printf("Enter the data file (abc.txt): ");
    scanf("%s", fileName);
    input = fopen(fileName,"r");
    int r = 0;

    for(fscanf(input,"%d", &data);!feof(input);fscanf(input,"%d", &data)){
        dataArrayLength++;
    }

    fseek(input, 0, SEEK_SET);//Move the cursor (,,x) beginning of the file and move (,x,)0 byte from the file (x,,) input.
    int dataArray[dataArrayLength];
    int length = dataArrayLength;

    for(fscanf(input,"%d", &data);!feof(input);fscanf(input,"%d", &data)){
        dataArray[dataArrayLength-length] = data;
        printf("dataArrayLength: %d - %d: length | data: %d\n", dataArrayLength, length, data);
        length--;
    }

    fscanf(input,"%d", &data);

    printf("sizeofArray is %d\n ", sizeof(dataArray));
    printf("-----OLD------\n");
    for(int i = 0; i< dataArrayLength; i++){
        printf("%d) %d\n", i, dataArray[i]);
    }
    printf("-----NEW------\n");
    ///--------------------------------------------------------------------
    insertionSort(dataArray);

    for(int i = 0; i< dataArrayLength; i++){
        printf("%d) %d\n", i, dataArray[i]);
    }
    printf("-----------\n");

    return 0;
}
