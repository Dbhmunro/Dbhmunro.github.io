---
layout: post
title:      "Starting into Two-Pointer Technique for Algorithms"
date:       2020-12-17 01:51:17 +0000
permalink:  starting_into_two-pointer_technique_for_algorithms
---


I have been working on strengthening my understanding of how to approach and solve algorithms. Not only are they helpful for those ever so common interview questions, but they also help add new tools to your code problem solving for whatever new thing you wish to build or fix you are trying to implement. This past week I attended a coder meetup, where we were exploring data structures and algorithms and started into the two-pointer technique.

Though there are many resources explaining the two-pointer technique, I find that sharing concepts that I have explored with others always helps strengthen my own understanding. And there is always a chance that my explanation may just be what you needed to help make this concept click.


The first thing that is important to know when deciding whether the two pointer technique fits is that the starting arrays are already sorted. This is important because your decisions on how to shift the pointers as you progress depend on knowing the organization of the arrays.


# Starting on either end

An example that, if you have been working with algorithms, have almost definitely come across is the Two Sum challenge. Given an array of integers that is already sorted in ascending order, find two numbers such that they add up to a specific target number.

The brute force method for this is through nested for loops, although it works, it is not very time efficient with a time complexity of O(n^2).
Instead we can begin with assigning pointers to either end of the original array and finding their sum:
-if the sum matches the target, then you have found your answer
-if the sum is smaller than your target, you can increment your leftmost pointer, which now points to a larger value
-and if the sum is larger than your target, you can decrement the rightmost pointer, which will now point to a smaller value

This description may be easier to see in code though:

```
var twoSum = function(numbers, target) {
    let left = 0
    let right = numbers.length-1
    
    while (left<right){
        const currSum = numbers[left] + numbers [right]
        if ( currSum < target) {
            left++
        } else if (currSum > target) {
            right--
        } else {
            return [left+1, right+1]
        }
    }
    
    return false
};
```

Because we only iterate over the original array at most 1 time, the time complexity of this solution is O(n), being a faster function than the original brute force solution.


# A potential third pointer

Building off of this approach of starting on either end, there are also instances that can necessitate the use of a third pointer. An example problem that can use this is the Squares of a Sorted Array.

The third pointer in this case is used for the results array to be able to insert items into a particular location in the array you wish to return. 

The description of the Squares of a Sorted Array is:
Given an integer array nums sorted in non-decreasing order, return an array of the squares of each number sorted in non-decreasing order.

Below is the code, using the same concept of a pointer at either end of the initial array, with a results pointer to track where we want to inject the squared value into the answer.

```
var sortedSquares = function(nums) {
    let leftPointer = 0
    let rightPointer = nums.length - 1
    const results = []
    let resultsPointer = nums.length - 1
    
    while (resultsPointer >= 0){
        let leftPointerSquare = nums[leftPointer]**2
        let rightPointerSquare = nums[rightPointer]**2
        
        if (leftPointerSquare > rightPointerSquare) {
            results[resultsPointer] = leftPointerSquare
            leftPointer++
        } else {
            results[resultsPointer] = rightPointerSquare
            rightPointer--
        }
        resultsPointer--
        
//         condensed lines of code example

//         let largerSquare = Math.max(leftPointerSquare, rightPointerSquare)
//         results[resultsPointer] = largerSquare
//         resultsPointer--
//         largerSquare === leftPointerSquare ? leftPointer++ : rightPointer--
    }
    
    return results
};
```


This approach again allows us to go from a time complexity of O(n^2) for a brute force approach to O(n).

