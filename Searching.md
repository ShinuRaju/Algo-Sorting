 
```javascript
// SEARCHING

// Function to perform linear search
function linearSearch(arr, target) {
  // Iterate through each element in the array
  for (let i = 0; i < arr.length; i++) {
    // Check if the current element is equal to the target value
    if (arr[i] === target) {
      return i; // If found, return the index of the target element
    }
  }
  return -1; // If the target is not found in the array, return -1
}

// Example usage of linear search:
const arr = [10, 20, 30, 40, 50]; // Sample array
const target = 30; // Target value to search for

const result = linearSearch(arr, target); // Call linearSearch function
if (result !== -1) {
  console.log(`Element found at index: ${result}`); // If found, log the index
} else {
  console.log("Element not found in the array."); // If not found, log the message
}

// Function to perform binary search using an iterative approach
function binarySearchIterative(arr, target) {
  let left = 0; // Initialize the left index
  let right = arr.length - 1; // Initialize the right index

  // Continue searching while the left index is less than or equal to the right index
  while (left <= right) {
    const mid = Math.floor((left + right) / 2); // Calculate the middle index

    // Check if the middle element is equal to the target
    if (arr[mid] === target) {
      return mid; // If found, return the index of the target
    } else if (arr[mid] < target) {
      left = mid + 1; // If the middle element is less than the target, search the right half
    } else {
      right = mid - 1; // If the middle element is greater than the target, search the left half
    }
  }

  return -1; // If the target is not found, return -1
}

// Example usage of binary search (iterative):
const arr2 = [10, 20, 30, 40, 50, 60, 70, 80, 90, 100]; // Sorted sample array
const target2 = 60; // Target value to search for

const result2 = binarySearchIterative(arr2, target2); // Call binarySearchIterative function
if (result2 !== -1) {
  console.log(`Element found at index: ${result2}`); // If found, log the index
} else {
  console.log("Element not found in the array."); // If not found, log the message
}

// Function to perform binary search using a recursive approach
function binarySearchRecursive(arr, target, left = 0, right = arr.length - 1) {
  // Base case: if left index exceeds right index, target is not found
  if (left > right) {
    return -1; // Return -1 if the target is not found
  }

  const mid = Math.floor((left + right) / 2); // Calculate the middle index

  // Check if the middle element is equal to the target
  if (arr[mid] === target) {
    return mid; // If found, return the index of the target
  } else if (arr[mid] < target) {
    // If the middle element is less than the target, search the right half recursively
    return binarySearchRecursive(arr, target, mid + 1, right);
  } else {
    // If the middle element is greater than the target, search the left half recursively
    return binarySearchRecursive(arr, target, left, mid - 1);
  }
}

// Example usage of binary search (recursive):
const arr3 = [10, 20, 30, 40, 50, 60, 70, 80, 90, 100]; // Sorted sample array
const target3 = 40; // Target value to search for

const result3 = binarySearchRecursive(arr3, target3); // Call binarySearchRecursive function
if (result3 !== -1) {
  console.log(`Element found at index: ${result3}`); // If found, log the index
} else {
  console.log("Element not found in the array."); // If not found, log the message
}
```


Here's a table summarizing the time and space complexities for linear search, binary search (iterative), and binary search (recursive) in their best, average, and worst-case scenarios:

| **Algorithm**               | **Best Case**   | **Average Case**   | **Worst Case**   | **Space Complexity**   |
|-----------------------------|------------------|---------------------|-------------------|------------------------|
| **Linear Search**           | O(1)             | O(n)                | O(n)              | O(1)                   |
| **Binary Search (Iterative)** | O(1)             | O(log n)            | O(log n)          | O(1)                   |
| **Binary Search (Recursive)** | O(1)             | O(log n)            | O(log n)          | O(log n)               |

 
