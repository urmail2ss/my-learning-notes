**Elementary Sorts** are simple algorithms used for sorting collections of data. They are typically easy to understand and implement but may not be the most efficient for large datasets. Here’s a brief overview of some common elementary sorting algorithms:

### 1. **Selection Sort**
- **Concept**: Repeatedly find the minimum element from the unsorted part of the array and move it to the beginning.
- **Steps**:
  1. Find the smallest element in the array.
  2. Swap it with the first element.
  3. Move to the next element and repeat the process for the remaining unsorted part of the array.
- **Time Complexity**: \(O(n^2)\) for all cases.
- **Space Complexity**: \(O(1)\) (in-place).

          import java.util.Arrays;
        
          public class SelectionSort {
            public static void selectionSort(int[] array) {
                int n = array.length;
                for (int i = 0; i < n - 1; i++) {
                    int minIndex = i;
                    for (int j = i + 1; j < n; j++) {
                        if (array[j] < array[minIndex]) {
                            minIndex = j;
                        }
                    }
                    if (minIndex != i) {
                        swap(array, i, minIndex);
                    }
                }
            }
        
            private static void swap(int[] array, int i, int j) {
                int temp = array[i];
                array[i] = array[j];
                array[j] = temp;
            }
        
            public static void main(String[] args) {
                int[] array = {64, 25, 12, 22, 11};
                selectionSort(array);
                System.out.println("Sorted array: " + Arrays.toString(array));
            }
        }


### 2. **Insertion Sort**
- **Concept**: Builds the final sorted array one item at a time by repeatedly picking the next item and inserting it into the correct position.
- **Steps**:
  1. Start with the first element, considering it as sorted.
  2. Pick the next element and compare it with the sorted part, shifting elements as needed.
  3. Insert the picked element in its correct position.
  4. Repeat the process until the entire array is sorted.
- **Time Complexity**: 
  - Best case: \(O(n)\) (when the array is already sorted).
  - Average and Worst case: \(O(n^2)\).
- **Space Complexity**: \(O(1)\) (in-place).

        import java.util.Arrays;
    
        public class InsertionSort {
            public static void insertionSort(int[] array) {
                int n = array.length;
                for (int i = 1; i < n; i++) {
                    int key = array[i];
                    int j = i - 1;
        
                    // Move elements of array[0..i-1], that are greater than key, to one position ahead
                    // of their current position
                    while (j >= 0 && array[j] > key) {
                        array[j + 1] = array[j];
                        j = j - 1;
                    }
                    array[j + 1] = key;
                }
            }
        
            public static void main(String[] args) {
                int[] array = {12, 11, 13, 5, 6};
                insertionSort(array);
                System.out.println("Sorted array: " + Arrays.toString(array));
            }
        }


### 3. **Bubble Sort**
- **Concept**: Repeatedly swap adjacent elements if they are in the wrong order, "bubbling" the largest unsorted element to its correct position.
- **Steps**:
  1. Compare each pair of adjacent elements.
  2. Swap them if they are in the wrong order.
  3. Repeat the process for the remaining unsorted elements.
  4. Continue until no swaps are needed.
- **Time Complexity**: 
  - Best case: \(O(n)\) (when the array is already sorted).
  - Average and Worst case: \(O(n^2)\).
- **Space Complexity**: \(O(1)\) (in-place).

        import java.util.Arrays;
    
        public class BubbleSort {
            public static void bubbleSort(int[] array) {
                int n = array.length;
                for (int i = 0; i < n - 1; i++) {
                    boolean swapped = false;
                    for (int j = 0; j < n - i - 1; j++) {
                        if (array[j] > array[j + 1]) {
                            swap(array, j, j + 1);
                            swapped = true;
                        }
                    }
                    // If no elements were swapped in the inner loop, the array is already sorted
                    if (!swapped) break;
                }
            }
        
            private static void swap(int[] array, int i, int j) {
                int temp = array[i];
                array[i] = array[j];
                array[j] = temp;
            }
        
            public static void main(String[] args) {
                int[] array = {5, 1, 4, 2, 8};
                bubbleSort(array);
                System.out.println("Sorted array: " + Arrays.toString(array));
            }
        }


### 4. **Shell Sort**
- **Concept**: A generalization of insertion sort, Shell sort allows the exchange of items that are far apart. The gap between elements to be compared is gradually decreased, eventually leading to an insertion sort.
- **Steps**:
  1. Start with a large gap and compare elements that are far apart.
  2. Perform an insertion sort on elements that are spaced apart by the gap.
  3. Reduce the gap and repeat the process.
  4. Continue until the gap is 1, where the process becomes a standard insertion sort.
- **Time Complexity**: Depends on the gap sequence, generally better than \(O(n^2)\).
- **Space Complexity**: \(O(1)\) (in-place).

        import java.util.Arrays;
        
        public class ShellSort {
            public static void shellSort(int[] array) {
                int n = array.length;
        
                // Start with a large gap, then reduce the gap
                for (int gap = n / 2; gap > 0; gap /= 2) {
                    for (int i = gap; i < n; i++) {
                        int temp = array[i];
                        int j;
                        for (j = i; j >= gap && array[j - gap] > temp; j -= gap) {
                            array[j] = array[j - gap];
                        }
                        array[j] = temp;
                    }
                }
            }
        
            public static void main(String[] args) {
                int[] array = {12, 34, 54, 2, 3};
                shellSort(array);
                System.out.println("Sorted array: " + Arrays.toString(array));
            }
        }
    

### Summary
Elementary sorts are educational tools for understanding the basics of sorting algorithms. They work well for small or nearly sorted datasets but are generally inefficient for large datasets due to their \(O(n^2)\) time complexity.
