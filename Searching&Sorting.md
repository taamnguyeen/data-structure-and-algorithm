# Searching&Sorting
## Searching
**Binary Search** can take many alternate forms and might not always be as straight forward as searching for a specific value. Sometimes you will have to apply a specific condition or rule to determine which side (left or right) to search next.
**Advantages**: fast
**Cons**: need to be pre-arranged
**Time Complexity**: O(log(N))
### Code Binary Search 
```c++
bool binary_search(int a[], int l, int r, int x){
    if(1 > r) return false;
    int m = (l + r)/2;
    if(a[m] == x) return true;
    else if(a[m] < x) return binary_search(a, m+1, r, x);
    else return binary_search(a, l, m-1, x);
}
```
## Sorting
**Slection sort** sotr the elements in the array by finding the smallest element and change to the head of array is sorted
**Time Complexity**: O(N^2)
#### Code Slection sort 
```c++
void selection_sort(int arr[], int n){
    for (int i = 0; i < n; ++i) {
        int min_pos = i;
        for (int j = i+1; j < n; ++j) {
            if(arr[j] < arr[min_pos]){
                min_pos = j;
            }
        }
        swap(arr[i], arr[min_pos]);
    }
}
```
<hr>

**Bubble sort** sort two consecutive elements in the array until the array is sorted.
**Time Complexity**: O(N^2)
#### Code Bubble sort 
```c++
void bubble_sort(int arr[], int n){
    for (int i = 0; i < n; ++i) {
        for (int j = 0; j < n - i - 1; ++j) {
            if(arr[j] > arr[j+1]){
                swap(arr[j], arr[j+1]);
            }
        }
    }
}
```
<hr>

**Insertion sort** traverse each element in unsorted array and sort it to sorted array
**Time Complexity**: O(N^2)
#### Code Insertion sort 
```c++
void insertion_sort(int arr[], int n){
    for(int i = 1; i < n; i++){
        int x = arr[i], pos = i-1;
        while(pos >= 0 && x < arr[pos]){
            arr[pos + 1] = arr[pos];
            pos--;
        }
        arr[pos + 1] = x;
    }
}
```
<hr>

**Counting sort** count the number of elements which have the same value to create the counter. Then sort all element in earch counter from min to max or max to min. 
**Time Complexity**: O(N + max number)
#### Code Counting sort 
```c++
void counting_sort(int arr[], int n){ //o(n+max){

    int output[n];
    int max = arr[0];
    int min = arr[0];

    for(int i = 1; i < n; i++){
        if(arr[i] > max)
            max = arr[i];
        else if(arr[i] < min)
            min = arr[i];
    }

    int k = max - min + 1;

    int count_array[k];
    fill_n(count_array, k, 0);

    for(int i = 0; i < n; i++)
        count_array[arr[i] - min]++;

    for(int i = 1; i < k; i++)
        count_array[i] += count_array[i - 1];

    for(int i = 0; i < n; i++){
        output[count_array[arr[i] - min] - 1] = arr[i];
        count_array[arr[i] - min]--;
    }


    for(int i = 0; i < n; i++)
        arr[i] = output[i];
}

```
<hr>

**Merge sort** divide array into 2 parts until there are lots of arrays have 1 element (void merge_sort) and then merge again after sorted (void merge).
**Time Complexity**: O(nlogn)
#### Code Merge sort 
```c++
void merge(int arr[], int l, int m, int r){
    int i, j, k;
    int n1 = m - l + 1;
    int n2 =  r - m;

    int L[n1], R[n2];

    for (i = 0; i < n1; i++)
        L[i] = arr[l + i];
    for (j = 0; j < n2; j++)
        R[j] = arr[m + 1+ j];

    i = 0;
    j = 0;
    k = l;
    while (i < n1 && j < n2){
        if (L[i] <= R[j]){
            arr[k] = L[i];
            i++;
        }
        else{
            arr[k] = R[j];
            j++;
        }
        k++;
    }

    while (i < n1){
        arr[k] = L[i];
        i++;
        k++;
    }

    while (j < n2){
        arr[k] = R[j];
        j++;
        k++;
    }
}

void merge_sort(int arr[], int l, int r){
    if (l < r){
        int m = l+(r-l)/2;
        merge_sort(arr, l, m);
        merge_sort(arr, m+1, r);
        merge(arr, l, m, r);
    }
}
```
<hr>
