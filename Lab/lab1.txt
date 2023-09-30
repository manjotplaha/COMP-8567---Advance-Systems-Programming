#include <stdio.h>
#include <stdlib.h>

// for highest between both
int mp_maxnum(int *mp_n1, int *mp_n2) {     //passing variables for comaprison
    if (*mp_n1 > *mp_n2) {                  //checkinng for condition
        return *mp_n1;
    } else {
        return *mp_n2;
    }
}

// for highest in array
int mp_maxarr(int *mp_ar) {                 //passing the array
    int mp_maximum = mp_ar[0];
    while (*mp_ar != '\0') {                //looping until the end of the array
        if (*mp_ar > mp_maximum) {
            mp_maximum = *mp_ar;
        }
        mp_ar++;
    }
    return mp_maximum;
}

int prod(int (*mp_maxnum1)(int *, int *), int (*mp_maxarr1)(int *), int *parameter3, int *parameter4, int *parameter5) {    //passing functions as parameters
    int max1 = mp_maxnum1(parameter3, parameter4);                  //finding maximum between thw two for multiplication
    int max2 = mp_maxarr1(parameter5);                              //passing the dynamic array to max array funciton which returns the highest number
    return max1 * max2;
}

void main() {
    int mp_num1 = 5;
    int mp_num2 = 8;

    int mp_userIp;
    printf("Enter the number of elements for the array: ");
    scanf("%d", &mp_userIp);

    int *dynar = (int *)malloc(mp_userIp * sizeof(int));        //allocating the memory to array using malloc dynamically
    if (dynar == NULL) {
        printf("Failed to allocate memory.\n");
        return 1;
    }

    printf("Enter %d elements for the array:\n", mp_userIp);
    for (int i = 0; i < mp_userIp; i++) {
        scanf("%d", &dynar[i]);
    }


    printf("Array in reverse order:\n");
    for (int i = mp_userIp - 1; i >= 0; i--) {      //looping on array elements in reverse order
        printf("%d ", *(dynar + i));                //deferencing the dynar for mp_ar values
    }
    printf("\n");

    int mp_result = prod(mp_maxnum, mp_maxarr, &mp_num1, &mp_num2, dynar);
    printf("The output of  requirement is: %d\n", mp_result);
}