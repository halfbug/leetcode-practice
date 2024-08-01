# 169. Majority Element

**Easy**

## Topics
- Array
- Divide and Conquer
- Bit Manipulation

## Problem Statement
Given an array `nums` of size `n`, return the majority element.

The majority element is the element that appears more than `⌊n / 2⌋` times. You may assume that the majority element always exists in the array.

### Example 1:
**Input**: `nums = [3, 2, 3]`

**Output**: `3`

### Example 2:
**Input**: `nums = [2, 2, 1, 1, 1, 2, 2]`

**Output**: `2`

## Constraints:
- `n == nums.length`
- `1 <= n < 5 * 10^4`
- `-10^9 < nums[i] <= 10^9`

## Follow-up
Could you solve the problem in linear time and in `O(1)` space?

---

## Dry Run of the Boyer-Moore Voting Algorithm

Let's dry run the Boyer-Moore Voting Algorithm step by step using an example array. We'll use the JavaScript solution, but the logic is the same for Python.

### Example: `nums = [2, 2, 1, 1, 1, 2, 2]`

#### Initial State
- `count = 0`
- `candidate = null`

#### Iteration 1: `num = 2`
- `count` is 0, so `candidate` becomes `2`
- `count` is incremented to `1` because `num` is equal to `candidate`
- Current state: `candidate = 2`, `count = 1`

#### Iteration 2: `num = 2`
- `num` is equal to `candidate`
- `count` is incremented to `2`
- Current state: `candidate = 2`, `count = 2`

#### Iteration 3: `num = 1`
- `num` is not equal to `candidate`
- `count` is decremented to `1`
- Current state: `candidate = 2`, `count = 1`

#### Iteration 4: `num = 1`
- `num` is not equal to `candidate`
- `count` is decremented to `0`
- Current state: `candidate = 2`, `count = 0`

#### Iteration 5: `num = 1`
- `count` is 0, so `candidate` becomes `1`
- `count` is incremented to `1` because `num` is equal to `candidate`
- Current state: `candidate = 1`, `count = 1`

#### Iteration 6: `num = 2`
- `num` is not equal to `candidate`
- `count` is decremented to `0`
- Current state: `candidate = 1`, `count = 0`

#### Iteration 7: `num = 2`
- `count` is 0, so `candidate` becomes `2`
- `count` is incremented to `1` because `num` is equal to `candidate`
- Final state: `candidate = 2`, `count = 1`

After completing the iterations, the final value of `candidate` is `2`, which is the majority element in the array.

### Explanation
- **Initialization**: Start with `count` as 0 and `candidate` as `null`.
- **For each element in the array**:
  - If `count` is 0, set `candidate` to the current element.
  - If the current element is the same as `candidate`, increment `count`.
  - If the current element is different from `candidate`, decrement `count`.
- The majority element will be the `candidate` at the end of the loop.

### Efficiency and Memory Usage

The statement "This algorithm ensures that we find the majority element in linear time (O(n)) and constant space (O(1))" means that the algorithm is very efficient both in terms of time and memory usage.

#### Linear Time (O(n))
- **Linear time** means that the time taken to execute the algorithm grows linearly with the size of the input array.
- If you have an array with `n` elements, the algorithm will perform a number of operations proportional to `n`.
- In this specific algorithm, we iterate through the array only once, making a constant amount of work for each element, resulting in `O(n)` time complexity.

#### Constant Space (O(1))
- **Constant space** means that the amount of extra memory used by the algorithm does not grow with the size of the input array.
- Regardless of how many elements are in the input array, the algorithm uses a fixed amount of additional memory.
- In this specific algorithm, we only use a few extra variables (`count` and `candidate`), which occupy a constant amount of space. Thus, the space complexity is `O(1)`.

### Why This Matters
- **Efficiency**: Algorithms with linear time complexity are efficient for large datasets because they process each element a fixed number of times.
- **Memory Usage**: Algorithms with constant space complexity are memory efficient because they do not require additional memory that grows with the input size.

### In Context of the Boyer-Moore Voting Algorithm
- The algorithm scans through the array once, making decisions based on the current element and updating `count` and `candidate` accordingly. This is why it runs in `O(n)` time.
- The only additional memory used is for the `count` and `candidate` variables, which do not depend on the input size, hence `O(1)` space.

In summary, the Boyer-Moore Voting Algorithm is highly efficient and well-suited for finding the majority element in large arrays because it minimizes both the time taken and the extra memory used.
