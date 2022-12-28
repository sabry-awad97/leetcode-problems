# Solution in Rust

Here is an example of how to implement the two sum problem in Rust using a hash map:

```rust
use std::collections::HashMap;

fn two_sum(nums: Vec<i32>, target: i32) -> Option<(usize, usize)> {
    let mut map = HashMap::new();

    // Iterate through the list and store each integer and its index in the hash map
    for (i, num) in nums.iter().enumerate() {
        map.insert(num, i);
    }

    // Iterate through the list again, checking if the target sum minus the current integer is present in the hash map
    for (i, num) in nums.iter().enumerate() {
        let diff = target - num;
        if let Some(j) = map.get(&diff) {
            // If the difference is present in the hash map, we have found our solution
            return Some((i, *j));
        }
    }

    // If we reach this point, it means that no two integers in the list add up to the target sum
    None
}

fn main() {
    let nums = vec![1, 2, 3, 4];
    let target = 5;
    let result = two_sum(nums, target);
    println!("{:?}", result); // Outputs Some((1, 2))
}
```

In the first part of the `two_sum` function, we create a new empty hash map called `map` and then iterate through the list of integers, inserting each integer and its index into the map. This allows us to quickly look up the index of any given integer in the list later on.

In the second part of the function, we iterate through the list again, this time checking if the target sum minus the current integer is present in the hash map. If it is, we return a tuple containing the indices of the two integers that add up to the target sum. If we reach the end of the list without finding a solution, we return `None`.

This implementation of the two sum problem is efficient and easy to understand, making it a good choice for solving this problem in Rust.

Here is a line-by-line breakdown of the Rust code

```rust
use std::collections::HashMap;
```

- This line imports the `HashMap` type from the `collections` module of the Rust standard library. A `HashMap` is a data structure that allows us to store key-value pairs and quickly look up values by their corresponding keys.

```rust
fn two_sum(nums: Vec<i32>, target: i32) -> Option<(usize, usize)> {
```

- This line defines a new function called `two_sum` that takes in two arguments: a `Vec` of `i32` values called `nums`, and an `i32` value called `target`.
  The function returns an `Option` type, which is a Rust type that represents a value that may or may not be present.
  In this case, the `Option` type is a tuple of two `usize` values, which represent the indices of the two integers that add up to the target sum.
  If no such integers are found, the function will return `None`.

```rust
    let mut map = HashMap::new();
```

- This line creates a new empty `HashMap` called map. The `mut` keyword indicates that `map` is a mutable variable, which means that its value can be changed later on.

```rust
    for (i, num) in nums.iter().enumerate() {
        map.insert(num, i);
    }
```

- This line iterates through the `nums` vector, using the `iter().enumerate()` method to get both the index and value of each element in the vector. For each iteration, the index and value are destructured into the variables `i` and `num`, respectively. The `insert` method is then called on `map`, inserting the value of `num` as a key and the value of `i` as the corresponding value.

```rust
    for (i, num) in nums.iter().enumerate() {
        let diff = target - num;
        if let Some(j) = map.get(&diff) {
            return Some((i, *j));
        }
    }
```

- This line iterates through the nums vector in the same way as before, again getting both the index and value of each element. The diff variable is then set to the difference between target and num.

- The `if let` statement then checks if the value of `diff` is present in the `map` hash map by calling the `get` method and passing in `&diff` as an argument. The `&` operator indicates that we are passing a reference to diff, rather than the value itself. If `diff` is present in the map, the `if let` statement will bind the value associated with diff in the map to the variable `j`, which is then returned as part of a tuple along with `i` using the `Some` variant of the `Option` type.

```rust
    None
```

- If the `for` loop completes without finding a solution, the function will return `None`, indicating that no two integers in the list add up to the `target` sum.
