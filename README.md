# python-sorting-algorithms

# Python program to implement Merge Sort, Selection Sort, and Insertion Sort

# -------------------- MERGE SORT --------------------
def merge(arr, l, m, r):
    n1 = m - l + 1
    n2 = r - m

    # Create temp arrays
    L = [0] * n1
    R = [0] * n2

    # Copy data to temp arrays L[] and R[]
    for i in range(n1):
        L[i] = arr[l + i]
    for j in range(n2):
        R[j] = arr[m + 1 + j]

    # Merge the temp arrays back into arr[l..r]
    i = 0
    j = 0
    k = l

    while i < n1 and j < n2:
        if L[i] <= R[j]:
            arr[k] = L[i]
            i += 1
        else:
            arr[k] = R[j]
            j += 1
        k += 1

    # Copy remaining elements of L[]
    while i < n1:
        arr[k] = L[i]
        i += 1
        k += 1

    # Copy remaining elements of R[]
    while j < n2:
        arr[k] = R[j]
        j += 1
        k += 1

def mergeSort(arr, l, r):
    if l < r:
        m = (l + (r - 1)) // 2
        mergeSort(arr, l, m)
        mergeSort(arr, m + 1, r)
        merge(arr, l, m, r)

# -------------------- SELECTION SORT --------------------
def selectionSort(arr):
    n = len(arr)
    for i in range(n):
        min_idx = i
        for j in range(i+1, n):
            if arr[j] < arr[min_idx]:
                min_idx = j
        arr[i], arr[min_idx] = arr[min_idx], arr[i]

# -------------------- INSERTION SORT --------------------
def insertionSort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1
        while j >= 0 and arr[j] > key:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key

# -------------------- DRIVER CODE --------------------
arr = [12, 11, 13, 5, 6, 7]

print("Original array:")
print(arr)

# Merge Sort
merge_arr = arr.copy()
mergeSort(merge_arr, 0, len(merge_arr) - 1)
print("\nMerge Sorted array:")
print(merge_arr)

# Selection Sort
selection_arr = arr.copy()
selectionSort(selection_arr)
print("\nSelection Sorted array:")
print(selection_arr)

# Insertion Sort
insertion_arr = arr.copy()
insertionSort(insertion_arr)
print("\nInsertion Sorted array:")
print(insertion_arr)


OUTPUT:


Original array:
[12, 11, 13, 5, 6, 7]

Merge Sorted array:
[5, 6, 7, 11, 12, 13]

Selection Sorted array:
[5, 6, 7, 11, 12, 13]

Insertion Sorted array:
[5, 6, 7, 11, 12, 13]
