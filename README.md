# 🛠 Git Learning 

### 1. **Setup & Init**

* `git config --global user.name "Your Name"`
* `git config --global user.email "you@example.com"`
* `git init` → create a new repo in a folder
* `git clone [url]` → practice cloning an existing repo

👉 **Practice:** Create a test folder, initialize a repo, and check configs.

---

### 2. **Stage & Snapshot**

* `git status` → check what’s changed
* `git add file.txt` → stage changes
* `git reset file.txt` → unstage
* `git diff` → see unstaged changes
* `git diff --staged` → see staged changes
* `git commit -m "message"` → save snapshot

👉 **Practice:** Make changes to a file, add & remove from staging, then commit.

---

### 3. **Branch & Merge**

* `git branch` → list branches
* `git branch feature` → create a branch
* `git checkout feature` → switch to it
* `git merge feature` → merge back to main
* `git log` → check history

👉 **Practice:** Create a feature branch, make a commit, merge it back.

---

### 4. **Share & Update**

* `git remote add origin [url]` → link remote
* `git fetch origin` → pull down changes
* `git merge origin/main` → merge remote into local
* `git push origin main` → upload changes
* `git pull` → fetch + merge

👉 **Practice:** Make a GitHub repo, push your commits, pull from it.

---

### 5. **Tracking Path Changes**

* `git rm file.txt` → remove tracked file
* `git mv old.txt new.txt` → rename file
* `git log --stat -M` → see moved files in history

👉 **Practice:** Rename a file, delete another, commit both.

---

### 6. **Temporary Commits (Stash)**

* `git stash` → save work-in-progress
* `git stash list` → see stashes
* `git stash pop` → reapply stash
* `git stash drop` → discard stash

👉 **Practice:** Modify a file, stash it, switch branch, come back, pop it.

---

### 7. **Rewrite History**

* `git rebase branch` → replay commits on top
* `git reset --hard commitID` → reset to earlier commit

👉 **Practice:** Make a few commits, reset to an older commit, then rebase.

---

### 8. **Inspect & Compare**

* `git log` → see history
* `git log branchB..branchA` → commits in A not in B
* `git log --follow file.txt` → file history
* `git diff branchB...branchA` → difference between branches
* `git show commitID` → details of a commit

👉 **Practice:** Explore history of your repo with these commands.

---

### 9. **Ignoring Patterns**

* Create a `.gitignore` with things like:

  ```
  *.log
  temp/
  ```
* `git config --global core.excludesfile ~/.gitignore_global`

👉 **Practice:** Add a `.gitignore` to your repo, commit it, and test ignored files.

---

### Focus on Mosh 

Dab: Dab <Int> ? -> Int 
Dab 10: Println Dab <Int>


### Some Haskell


```haskell
quicksort :: (Ord a) => [a] -> [a]
quicksort [] = []
quicksort (x:xs) =
    let smallerSorted = quicksort [a | a <- xs, a <= x]
        biggerSorted = quicksort [a | a <- xs, a > x]
    in  smallerSorted ++ [x] ++ biggerSorted
```

### Now in Zig 


```zig
const std = @import("std");

fn partition(arr: []i32, left: usize, right: usize) usize {
    const pivot = arr[right];
    var i: isize = @intCast(isize, left) - 1;
    var j: usize = left;

    while (j < right) : (j += 1) {
        if (arr[j] <= pivot) {
            i += 1;
            const idx: usize = @intCast(usize, i);
            const tmp = arr[idx];
            arr[idx] = arr[j];
            arr[j] = tmp;
        }
    }
    const tmp = arr[@intCast(usize, i + 1)];
    arr[@intCast(usize, i + 1)] = arr[right];
    arr[right] = tmp;
    return @intCast(usize, i + 1);
}

fn quicksort(arr: []i32, left: usize, right: usize) void {
    if (left < right) {
        const pi = partition(arr, left, right);
        if (pi > 0) quicksort(arr, left, pi - 1); // prevents underflow
        quicksort(arr, pi + 1, right);
    }
}

pub fn main() void {
    var data = [_]i32{10, 7, 8, 9, 1, 5};
    std.debug.print("Original array: {any}\n", .{data});
    quicksort(data[0..], 0, data.len - 1);
    std.debug.print("Sorted array: {any}\n", .{data});
}

```

### Now in D


```D
import std.stdio;
import std.algorithm; // for filter
import std.array;     // for array

int[] quicksort(int[] arr) {
    if (arr.length == 0) return [];
    auto pivot = arr[0];
    auto rest = arr[1..$];
    auto left = quicksort(rest.filter!(a => a <= pivot).array);
    auto right = quicksort(rest.filter!(a => a > pivot).array);
    return left ~ [pivot] ~ right;
}

void main() {
    int[] data = [10, 7, 8, 9, 1, 5];
    writeln("Original array: ", data);
    int[] sorted = quicksort(data);
    writeln("Sorted array: ", sorted);
}

```

### Now in JS

```js
function quicksort(arr) {
  if (arr.length <= 1) return arr;
  const [pivot, ...rest] = arr;
  const left = quicksort(rest.filter(x => x <= pivot));
  const right = quicksort(rest.filter(x => x > pivot));
  return [...left, pivot, ...right];
}
```


### Zen of Haskell


The "Zen of Haskell" can be understood as the guiding principles and philosophy behind Haskell's purely functional programming paradigm. Here are its core tenets:

### Purely Functional
Haskell is a purely functional language, meaning functions have no side effects and always produce the same output given the same input (referential transparency). This promotes correctness, reasoning, and easier refactoring.

### Immutability
Values in Haskell are immutable. Once assigned, variables do not change, which helps avoid bugs related to state changes and supports concurrency.

### First-Class and Higher-Order Functions
Functions are first-class citizens, meaning they can be passed as arguments, returned from other functions, and stored in data structures. This enables powerful abstraction and code reuse.

### Recursion and Declarative Style
Iteration is expressed through recursion rather than loops. Haskell programs describe what they want to compute rather than how, making code concise and expressive.

### Laziness and Non-strict Evaluation
Expressions are evaluated only when needed. This supports building infinite data structures, improves modularity, and can lead to performance benefits.

### Strong Static Typing with Type Inference
Haskell has a strong and expressive type system that catches many errors at compile time, while type inference reduces verbosity by deducing types automatically.

### Composability
Functions and code units are designed to compose seamlessly, encouraging modularity and reuse.

In essence, the Zen of Haskell is about writing clear, robust, concise, and correct code by leveraging functions as mathematical entities, immutability, and expressive types, embraced by a declarative programming style.[1][2][3][4][5][6]

[1](https://dev.to/dhanush9952/a-guide-to-functional-programming-18h9)
[2](https://blog.rheinwerk-computing.com/what-are-the-principles-of-functional-programming)
[3](https://learnyouahaskell.com/introduction)
[4](https://www.geeksforgeeks.org/blogs/functional-programming-paradigm/)
[5](https://www.haskell.org/haskellwiki/functional_programming)
[6](https://www.haskell.org)
[7](https://nptel.ac.in/courses/106106137)
[8](https://www.tutorialspoint.com/haskell/index.htm)
