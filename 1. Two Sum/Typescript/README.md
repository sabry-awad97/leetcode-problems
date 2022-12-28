# Solution in Typescript

```Typescript
/**
 * Find the indices of the two elements in the given array that add up to the target sum.
 *
 * @param {number[]} nums - The input array of integers
 * @param {number} target - The target sum
 * @returns {number[]} - The indices of the two elements that add up to the target sum, or [-1, -1] if no such elements exist
 */
function twoSum(nums: number[], target: number): number[] {
  // Create a map to store the indices of the elements in the array
  const indices: Map<number, number> = new Map();

  // Iterate through the array
  for (let i = 0; i < nums.length; i++) {
    // Calculate the difference between the target sum and the current element
    const diff = target - nums[i];

    // Check if the difference is present in the map
    if (indices.has(diff)) {
      // If it is, return the indices of the current element and the element with the difference
      return [i, indices.get(diff)];
    } else {
      // If it is not, add the current element and its index to the map
      indices.set(nums[i], i);
    }
  }

  // If no such elements are found, return [-1, -1]
  return [-1, -1];
}
```

In this solution, we first create a map to store the indices of the elements in the array. We then iterate through the array and calculate the difference between the target sum and the current element. If the difference is present in the map, it means that we have found two elements that add up to the target sum, so we return their indices. If the difference is not present in the map, we add the current element and its index to the map. If no such elements are found, we return [-1, -1] to indicate that no solution exists.

There are several other ways to solve the Two Sum problem as well. Here is another solution that uses a brute force approach, where we simply check all possible pairs of elements in the array:

```Typescript
/**
 * Find the indices of the two elements in the given array that add up to the target sum.
 *
 * @param {number[]} nums - The input array of integers
 * @param {number} target - The target sum
 * @returns {number[]} - The indices of the two elements that add up to the target sum, or [-1, -1] if no such elements exist
 */
function twoSum(nums: number[], target: number): number[] {
  // Iterate through the array
  for (let i = 0; i < nums.length; i++) {
    // Check all possible pairs of elements
    for (let j = i + 1; j < nums.length; j++) {
      // If the current pair of elements adds up to the target sum, return their indices
      if (nums[i] + nums[j] === target) {
        return [i, j];
      }
    }
  }

  // If no such elements are found, return [-1, -1]
  return [-1, -1];
}
```

This solution has a time complexity of O(n^2), since we need to check all possible pairs of elements in the array. This means that the solution will take longer to execute as the size of the input array increases.
