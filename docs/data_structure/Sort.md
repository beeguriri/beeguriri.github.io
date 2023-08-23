---
layout: default
title: 정렬
nav_order: 3
parent: Data Structure
---



## 📑 버블 정렬

- i번째 원소와 i+1번째 원소 비교

```c
void BubbleSort(int arr[], int n) {
    int i, j;
    int temp;
    
    for(i=0; i<n-1; i++){
        for(j=0; j<n-1-i; j++) {
            if(arr[j]>arr[j+1]){
                temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }
        }
    }
}
```



## 📑 선택 정렬

- i번째 원소와 i+1 ~ n 까지의 원소 중 최소값 찾아서 i번째와 교환

```c
void SelectionSort(int arr[], int n) {
    int i, j;
    int minIdx;
    int temp;
    
    for(i=0; i<n-1; i++) {
		minIdx = i;
        
        //i번째 이후 배열에서 최소값 찾아서
        for(j=i+1; j<n; j++)
            if(arr[j]<arr[minIdx])
                minIdx = j;
        
        //i번째와 교환
        temp = arr[i];
        arr[i] = arr[minIdx];
        arr[minIdx] = temp;
    }
}
```



## 📑 삽입 정렬

- 배열의 1번째 부터 끝까지 반복
- target을 선택하고, 삽입 위치를 찾음
- 부분 정렬이 되어 있을 경우 효율이 좋음

```c
void InsertionSort(int [] arr, n) {
    
    int i, j;
    int target;
    
    for(i=1; i<n; i++) {
        target = arr[i];
		
        for(j=i-1; j>=0; j--) {
            if(arr[j]>target)
                arr[j+1] = arr[j];
            else
                break;
        }
        arr[j+1] = target;
    }
}
```



## 📑 셸 정렬

- 삽입정렬과 유사하나 셸정렬은 특정 범위만큼 이동하면서 target 비교
  - 삽입정렬은 1씩 이동하며 target비교

```c
void ShellSort(int [] arr, n) {
    
    int i, j;
    int h;
    int target;
    
    h = n/2;
    
    while(h>0) {
        for(i=h; i<n; i++) {
            target = arr[i];

            for(j=i-h; j>=0; j-=h) {
                if(arr[j]>target)
                    arr[j+h] = arr[j];
                else
                    break;
            }
            arr[j+h] = target;
        }
        h /= 2;
    }
}
```



## 📑 힙 정렬

- 오름차순 정렬일 때, 최대힙 사용
- 완전이진트리에 데이터 배치 후 힙으로 형성하고,
- 최댓값 제외 후
- 다시 힙으로 재구성 하는 과정 반복

```c
int swap(int* a, int* b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

void heapSort(int array[], int n) {
    // 최대 힙(Max Heap) 구성
    for (int i = (n/2)-1; i >= 0; i--)
        heapify(array, n, i);

    // Root에 위치한 최대값을 마지막 노드와 바꿔가며 Heap 재구성
    // Heap의 크기를 줄여가며 값이 큰 원소를 차례로 가져옴
    for (int i = n - 1; i > 0; i--) {
        swap(&array[0], &array[i]);
        heapify(array, i, 0);
    }
}

void heapify(int array[], int n, int i) {
    int parent = i;
    int leftChild = i*2+1;
    int rightChild = i*2+2;

    // 왼쪽 자식 노드가 존재하면서 부모노드와 값 비교.
    if (leftChild < n && array[parent] < array[leftChild]) 
        parent = leftChild;
    
    // 오른쪽 자식 노드가 존재하면서 부모노드와 값 비교.
    if (rightChild < n && array[parent] < array[rightChild])
        parent = rightChild;
    
    // 왼쪽 or 오른쪽 자식 노드 중 부모 노드보다 큰 값이 존재한 경우
    if (i != parent) {
        swap(&array[parent], &array[i]);
        // 초기 부모노드가 제자리를 찾을 때까지 내려감
        heapify(array, n, parent);
    }
}
```



## 📑 병합 정렬

- 분할 정복 알고리즘에 근거
- 배열을 나눌 수 있을 때 까지 나눈 후
- 병합 하면서 정렬

```c
void MergeSort(int arr[], int left, int right) {

    if(left>=right)
        return;

    int mid; 

    mid = (left+right)/2;

    //둘로 나눌수 있을때 까지 나눈 후
    MergeSort(arr, left, mid);
    MergeSort(arr, mid+1, right);

    //정렬된 두 배열 병합
    MergeArray(arr, left, mid, right);
}

void MergeArray(int arr[], int left, int mid, int right) {

    int pl = left;
    int pr = mid+1;
    int idx = left;

    int i;

    //임시배열 생성
    int *sortArr = (int*)malloc(sizeof(int)*(right+1));

    while(pl<=mid && pr<=right) {

        if(arr[pl]<=arr[pr])
            sortArr[idx++] = arr[pl++];
        else
            sortArr[idx++] = arr[pr++];
    }

    //오른쪽만 남음
    if(pl>mid)
        while(pr<=right)
            sortArr[idx++] = arr[pr++];
    //왼쪽만 남음
    else
        while(pl<=mid)
            sortArr[idx++] = arr[pl++];

    //정렬된 결과를 원래 배열에 반영
    for(i=left; i<=right; i++)
        arr[i] = sortArr[i];
}
```



## 📑 퀵 정렬

- 분할 정복 알고리즘에 근거
- 피벗을 기준으로 피벗보다 작은 값, 피벗보다 큰 값으로 나눔
