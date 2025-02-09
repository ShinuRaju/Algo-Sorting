 
```javascript
// Sorting Algorithms

// Function to perform Bubble Sort on the given array
function bubbleSort(arr) {
  // If the array has 0 or 1 element, it's already sorted, so return it as is
  if (arr.length <= 1) return arr;

  // Outer loop to control the number of passes through the array
  for (let i = 0; i < arr.length; i++) {
    // Flag to track if any swaps occurred during this pass
    let swapped = false;

    // Inner loop to compare and swap adjacent elements in the unsorted portion
    // The inner loop goes up to (arr.length - 1 - i) because after each pass,
    // the last 'i' elements are already sorted and can be ignored
    for (let j = 0; j < arr.length - 1 - i; j++) {
      // Compare the current element with the next one
      if (arr[j] > arr[j + 1]) {
        // If the current element is greater than the next, swap them
        [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];

        // Set the 'swapped' flag to true since a swap occurred
        swapped = true;
      }
    }

    // If no swaps were made in the inner loop, the array is already sorted
    // Break out of the loop early to optimize performance
    if (!swapped) break;
  }

  // Return the sorted array
  return arr;
}

console.log(bubbleSort([34, 7, 23, 32, 5, 62])); // Output: [5, 7, 23, 32, 34, 62]

// Function to perform Selection Sort on an array
function selectionSort(arr) {
  // If the array has 0 or 1 element, it's already sorted, so return it.
  if (arr.length <= 1) return arr;

  // Outer loop to iterate through the entire array
  for (let i = 0; i < arr.length - 1; i++) {
    // Assume the first unsorted element is the minimum
    let minIndex = i;

    // Inner loop to find the smallest element in the unsorted part of the array
    for (let j = i + 1; j < arr.length; j++) {
      // If a smaller element is found, update minIndex
      if (arr[j] < arr[minIndex]) {
        minIndex = j;
      }
    }

    // If the smallest element found is not already at position i, swap it
    if (minIndex !== i) {
      // Swap the current element with the smallest element found
      [arr[i], arr[minIndex]] = [arr[minIndex], arr[i]];
    }
  }

  // Return the sorted array
  return arr;
}

console.log(selectionSort([34, 7, 23, 32, 5, 62])); // Output: [5, 7, 23, 32, 34, 62]

// Function to perform Insertion Sort on an array
function insertionSort(arr) {
  // Loop through each element in the array starting from the second element
  for (let i = 1; i < arr.length; i++) {
    // The element to be inserted into the sorted portion of the array
    let currentElement = arr[i]; 
    // Index of the last element in the sorted portion
    let j = i - 1; 

    // Move elements of arr[0..i-1] that are greater than currentElement to one position ahead of their current position
    // This creates a space for the currentElement to be inserted
    while (j >= 0 && arr[j] > currentElement) {
      // Shift the larger element one position to the right
      arr[j + 1] = arr[j]; 
      // Move to the next element in the sorted portion
      j--; 
    }

    // Insert the currentElement into its correct position
    arr[j + 1] = currentElement; // Place currentElement at the position found
  }

  // Return the sorted array
  return arr;
}

// Example usage
console.log(insertionSort([34, 7, 23, 32, 5, 62])); // Output: [5, 7, 23, 32, 34, 62]

// Function to perform Merge Sort on an array
function mergeSort(arr) {
  // Base case: If the array has 1 or 0 elements, it's already sorted
  if (arr.length <= 1) return arr;

  // Find the middle index to divide the array into two halves
  let mid = Math.floor(arr.length / 2);
  
  // Recursively sort the left half of the array
  let sortLeft = mergeSort(arr.slice(0, mid));
  
  // Recursively sort the right half of the array
  let sortRight = mergeSort(arr.slice(mid));

  // Merge the two sorted halves and return the sorted array
  return merge(sortLeft, sortRight);
}

// Helper function to merge two sorted arrays
function merge(arrLeft, arrRight) {
  // Create an empty array to hold the merged result
  let result = [];
  let leftIndex = 0; // Pointer for the left array
  let rightIndex = 0; // Pointer for the right array

  // Compare elements from both arrays and merge them in sorted order
  while (leftIndex < arrLeft.length && rightIndex < arrRight.length) {
    // If the current element in the left array is smaller
    if (arrLeft[leftIndex] < arrRight[rightIndex]) {
      // Add it to the result and move the left pointer to the right
      result.push(arrLeft[leftIndex]); 
      leftIndex++; 
    } else {
      // Otherwise, add the right element and move the right pointer to the right
      result.push(arrRight[rightIndex]); 
      rightIndex++; 
    }
  }

  // Concatenate any remaining elements from the left or right array
  // If any elements remain in the left array, add them to the result
  // If any elements remain in the right array, add them to the result
  return result.concat(arrLeft.slice(leftIndex)).concat(arrRight.slice(rightIndex));
}

// Example usage
console.log(mergeSort([34, 7, 23, 32, 5, 62])); // Output: [5, 7, 23, 32, 34, 62]

// Function to perform Quick Sort on an array
function quickSort(arr) {
  // Base case: If the array has 0 or 1 elements, it is already sorted
  if (arr.length <= 1) return arr;

  // Choose the pivot element (last element of the array)
  let pivot = arr[arr.length - 1];

  // Initialize empty arrays for elements less than and greater than the pivot
  let left = [];  // Array to hold elements less than the pivot
  let right = []; // Array to hold elements greater than or equal to the pivot

  // Loop through all elements except the pivot (from 0 to second last element)
  for (let i = 0; i < arr.length - 1; i++) {
    // Compare each element with the pivot
    if (arr[i] < pivot) {
      // If the current element is less than the pivot, push it to the left array
      left.push(arr[i]);
    } else {
      // If the current element is greater than or equal to the pivot, push it to the right array
      right.push(arr[i]);
    }
  }

  // Recursively sort the left and right arrays and concatenate the results
  // The sorted left array, the pivot, and the sorted right array are combined
  return [...quickSort(left), pivot, ...quickSort(right)];
}

// Example usage: Sorting an array
console.log(quickSort([34, 7, 23, 32, 5, 62])); // Output: [5, 7, 23, 32, 34, 62]
```


Here's a table summarizing the time and space complexities for the Bubble Sort, Selection Sort, Insertion Sort, Merge Sort, and Quick Sort algorithms:

| **Sorting Algorithm** | **Best Case Time Complexity** | **Average Case Time Complexity** | **Worst Case Time Complexity** | **Space Complexity**  |
|-----------------------|-------------------------------|----------------------------------|-------------------------------|------------------------|
| **Bubble Sort**       | O(n)                          | O(n²)                            | O(n²)                        | O(1)                   |
| **Selection Sort**    | O(n²)                         | O(n²)                            | O(n²)                        | O(1)                   |
| **Insertion Sort**    | O(n)                          | O(n²)                            | O(n²)                        | O(1)                   |
| **Merge Sort**        | O(n log n)                   | O(n log n)                       | O(n log n)                   | O(n)                  |
| **Quick Sort**        | O(n log n)                   | O(n log n)                       | O(n²)                        | O(log n)              |


