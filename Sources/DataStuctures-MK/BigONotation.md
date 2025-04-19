# 📊 Big O Notation in Swift

Big O Notation is a way to describe the **performance** or **complexity** of an algorithm. It helps us understand how an algorithm scales with input size. This document explains Big O with practical examples in Swift 🚀

---

## ⏱️ Time Complexity

Time complexity describes how the runtime grows relative to the input.

### O(1) - Constant Time

```swift
func getFirstElement(from array: [Int]) -> Int? {
    return array.first
}
```

✅ No matter the size of the array, it takes the same amount of time.

```swift
func printAllElements(_ array: [Int]) {
    for item in array {
        print(item)
    }
}
```

### O(n) - Linear Time

```swift
func printAllElements(_ array: [Int]) {
    for item in array {
        print(item)
    }
}
```

✅ Time increases linearly with the number of elements.

### O(n²) - Quadratic Time

```swift
func printPairs(_ array: [Int]) {
    for i in array {
        for j in array {
            print("(\(i), \(j))")
        }
    }
}
```

⚠️ Gets expensive fast. Avoid for large n.

### O(log n) - Logarithmic Time

```swift
func binarySearch(_ array: [Int], target: Int) -> Int? {
    var left = 0
    var right = array.count - 1
    
    while left <= right {
        let mid = (left + right) / 2
        if array[mid] == target {
            return mid
        } else if array[mid] < target {
            left = mid + 1
        } else {
            right = mid - 1
        }
    }
    return nil
}
```

✅ Efficient for sorted data.

### O(n log n) - Linearithmic Time

```swift
func mergeSort(_ array: [Int]) -> [Int] {
    guard array.count > 1 else { return array }
    
    let mid = array.count / 2
    let left = mergeSort(Array(array[0..<mid]))
    let right = mergeSort(Array(array[mid..<array.count]))
    
    return merge(left, right)
}
```

```swift
func merge(_ left: [Int], _ right: [Int]) -> [Int] {
    var merged: [Int] = []
    var i = 0, j = 0
    
    while i < left.count && j < right.count {
        if left[i] < right[j] {
            merged.append(left[i])
            i += 1
        } else {
            merged.append(right[j])
            j += 1
        }
    }
    
    return merged + left[i...] + right[j...]
}
```
## 📦 Space Complexity

Space complexity refers to the memory used by the algorithm.


### O(1) Space

```swift
func sum(_ array: [Int]) -> Int {
    var total = 0
    for num in array {
        total += num
    }
    return total
}
```

✅ Uses constant extra space.

### O(n) Space

```swift
func duplicateArray(_ array: [Int]) -> [Int] {
    var result: [Int] = []
    for num in array {
        result.append(num)
    }
    return result
}
```

⚠️ Uses memory proportional to input size.

🧠 Quick Reference

Complexity | Name | Example
O(1) | Constant | Accessing array element
O(n) | Linear | Loop through array
O(n²) | Quadratic | Nested loops
O(log n) | Logarithmic | Binary Search
O(n log n) | Linearithmic | Merge Sort
O(2ⁿ) | Exponential | Recursive Fibonacci
O(n!) | Factorial | Traveling Salesman (Brute Force)

🎯 Why It Matters
Understanding time and space complexity helps you:

Write more efficient code

Prepare for technical interviews

Optimize real-world applications

🧩 Contributions
Want to add your own Swift examples or diagrams? Open a pull request! 💡
