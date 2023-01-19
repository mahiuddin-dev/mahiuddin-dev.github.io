---
title: "Binary Search Algorithm"
date: 2023-01-19T21:04:50+06:00
draft: false
github_link: "https://github.com/mahiuddin-dev/"
author: "Mahiuddin"
# image: /images/blogs/
slug: binary-search-algorithm
tags:
  - Python
  - Javascript
  - Cpp
  - Algorithm

description: "Binary search is an efficient algorithm for finding an item from a sorted list of items"
toc: 
---

Binary search is an efficient algorithm for finding an item from a sorted list of items. It works by repeatedly dividing the search interval in half. The idea is to determine, in logarithmic time, whether the item you are searching for is in the lower or upper half of the interval. If it is in the lower half, you repeat the process on that half; if it is in the upper half, you repeat the process on that half. This process continues until the item is found or the search interval is empty.
<!--more-->

Here is an example of a binary search algorithm implemented in Python, JavaScript and C++.

## Python

```
def binary_search(arr, target):
    left = 0
    right = len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1

arr = [1, 2, 3, 4, 5, 6, 7, 8, 9]
target = 6
result = binary_search(arr, target)
if result != -1:
    print(f'Element found at index {result}')
else:
    print('Element not found in array')

```

## JavaScript

```
function binarySearch(list, item) {
    let low = 0;
    let high = list.length - 1;

    while (low <= high) {
        let mid = Math.floor((low + high) / 2);
        let guess = list[mid];
        if (guess === item) {
            return mid;
        }
        if (guess > item) {
            high = mid - 1;
        } else {
            low = mid + 1;
        }
    }
    return null;
}

let myList = [1, 3, 5, 7, 9];

console.log(binarySearch(myList, 3)); // Output: 1
console.log(binarySearch(myList, -1)); // Output: null


```
## C++

```
#include <iostream>
using namespace std;

int binarySearch(int list[], int item, int low, int high) {
    if (low <= high) {
        int mid = low + (high - low) / 2;
        if (list[mid] == item) {
            return mid;
        }
        if (list[mid] > item) {
            return binarySearch(list, item, low, mid - 1);
        }
        return binarySearch(list, item, mid + 1, high);
    }
    return -1;
}

int main() {
    int myList[] = {1, 3, 5, 7, 9};
    int n = sizeof(myList) / sizeof(myList[0]);

    cout << binarySearch(myList, 3, 0, n - 1) << endl; // Output: 1
    cout << binarySearch(myList, -1, 0, n - 1) << endl; // Output: -1
    return 0;
}

```

In this example, we define a function called binary_search() that takes in two parameters: an array and a target element. The function uses a while loop to repeatedly divide the array in half until the target element is found or the array is exhausted. The loop starts by setting two pointers, left and right, to the first and last elements of the array, respectively. The pointer mid is set to the middle of the array by taking the average of left and right. If the element at the mid index is equal to the target element, the function returns the index of the target element. If the element at the mid index is less than the target element, the left pointer is set to one position to the right of mid. If the element at the mid index is greater than the target element, the right pointer is set to one position to the left of mid. The loop continues until the left pointer is greater than the right pointer, at which point the function returns -1 to indicate that the target element was not found in the array. It's important to note that the array should be sorted to be able to use binary search. In the example above, the array is sorted in ascending order. Binary search has a time complexity of O(log n) which is faster than linear search (O(n)), which makes it suitable for large datasets.
