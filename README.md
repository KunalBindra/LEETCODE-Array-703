# LEETCODE-Array-703
Let's dry run the `KthLargest` class to see how it works.

### Initialization

Consider the following example:
- k = 3 (we want to find the 3rd largest number)
- nums = [4, 5, 8, 2]

```java
KthLargest obj = new KthLargest(3, [4, 5, 8, 2]);
```

### Step 1: Constructor

The constructor initializes the class by iterating through the `nums` array and adding elements to the min-heap.

#### Iteration 1: num = 4
- The `heapify(4)` method is called.
  - The value `4` is added to the `minHeap`.
  - The `minHeap` now contains: `[4]`.

#### Iteration 2: num = 5
- The `heapify(5)` method is called.
  - The value `5` is added to the `minHeap`.
  - The `minHeap` now contains: `[4, 5]`.

#### Iteration 3: num = 8
- The `heapify(8)` method is called.
  - The value `8` is added to the `minHeap`.
  - The `minHeap` now contains: `[4, 5, 8]`.

#### Iteration 4: num = 2
- The `heapify(2)` method is called.
  - The value `2` is added to the `minHeap`.
  - The `minHeap` now contains: `[2, 4, 8, 5]`.
  - Since the heap size exceeds `k` (which is 3), the smallest element (`2`) is removed.
  - The `minHeap` now contains: `[4, 5, 8]`.

At the end of the constructor, the `minHeap` contains `[4, 5, 8]`, which represents the three largest elements in the array, with the smallest of those three being the 3rd largest overall.

### Step 2: Adding a New Element

Next, let's add a new element and see how it updates the `minHeap`.

#### Example 1: Adding 3
```java
obj.add(3);
```
- The `heapify(3)` method is called.
  - The value `3` is added to the `minHeap`.
  - The `minHeap` now contains: `[3, 4, 8, 5]`.
  - Since the heap size exceeds `k`, the smallest element (`3`) is removed.
  - The `minHeap` now contains: `[4, 5, 8]`.
- The method returns `4`, which is the 3rd largest element.

#### Example 2: Adding 10
```java
obj.add(10);
```
- The `heapify(10)` method is called.
  - The value `10` is added to the `minHeap`.
  - The `minHeap` now contains: `[4, 5, 8, 10]`.
  - Since the heap size exceeds `k`, the smallest element (`4`) is removed.
  - The `minHeap` now contains: `[5, 10, 8]`.
- The method returns `5`, which is the 3rd largest element.

#### Example 3: Adding 9
```java
obj.add(9);
```
- The `heapify(9)` method is called.
  - The value `9` is added to the `minHeap`.
  - The `minHeap` now contains: `[5, 9, 8, 10]`.
  - Since the heap size exceeds `k`, the smallest element (`5`) is removed.
  - The `minHeap` now contains: `[8, 9, 10]`.
- The method returns `8`, which is the 3rd largest element.

### Summary

- The `minHeap` keeps track of the top `k` largest elements, with the smallest element in the heap being the `k`th largest overall.
- When a new element is added, it is inserted into the heap, and if the heap size exceeds `k`, the smallest element is removed.
- The `peek()` method of the `PriorityQueue` (min-heap) always returns the smallest element, which corresponds to the `k`th largest element in the list.
