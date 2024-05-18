# LEETCODE-Trees-979
Let's perform a dry run of the `distributeCoins` method on a sample binary tree to understand how the algorithm works. We will use the following tree for this example:

```
        3
       / \
      0   0
```

Each node represents the number of coins at that node.

### Initial State
- The `ans` variable is initialized to 0.
- The `distributeCoins` method is called with the root node (value 3).

### Step-by-Step Execution

1. **Call `distributeCoins(root)`**
    - `ans = 0`
    - Call `dfs(root)` where `root` is the node with value 3.

2. **Call `dfs(root)`**
    - Node value: 3
    - Call `dfs(root.left)` where `root.left` is the node with value 0.

3. **Call `dfs(root.left)`**
    - Node value: 0
    - Call `dfs(root.left.left)` where `root.left.left` is `null`.
    - Since `root.left.left` is `null`, return 0.
    - Call `dfs(root.left.right)` where `root.left.right` is `null`.
    - Since `root.left.right` is `null`, return 0.
    - Calculate `coin`:
      ```
      coin = dfs(root.left.left) + dfs(root.left.right) + root.left.val - 1
           = 0 + 0 + 0 - 1
           = -1
      ```
    - Update `ans`:
      ```
      ans += Math.abs(coin)
         = 0 + Math.abs(-1)
         = 1
      ```
    - Return `coin` = -1.

4. **Return to `dfs(root)`**
    - Node value: 3
    - Result from `dfs(root.left)` is -1.
    - Call `dfs(root.right)` where `root.right` is the node with value 0.

5. **Call `dfs(root.right)`**
    - Node value: 0
    - Call `dfs(root.right.left)` where `root.right.left` is `null`.
    - Since `root.right.left` is `null`, return 0.
    - Call `dfs(root.right.right)` where `root.right.right` is `null`.
    - Since `root.right.right` is `null`, return 0.
    - Calculate `coin`:
      ```
      coin = dfs(root.right.left) + dfs(root.right.right) + root.right.val - 1
           = 0 + 0 + 0 - 1
           = -1
      ```
    - Update `ans`:
      ```
      ans += Math.abs(coin)
         = 1 + Math.abs(-1)
         = 2
      ```
    - Return `coin` = -1.

6. **Return to `dfs(root)`**
    - Node value: 3
    - Result from `dfs(root.right)` is -1.
    - Calculate `coin`:
      ```
      coin = dfs(root.left) + dfs(root.right) + root.val - 1
           = -1 + -1 + 3 - 1
           = 0
      ```
    - Update `ans` (no change in `ans` as `coin` is 0):
      ```
      ans += Math.abs(coin)
         = 2 + Math.abs(0)
         = 2
      ```
    - Return `coin` = 0.

7. **Return to `distributeCoins(root)`**
    - The final value of `ans` is 2.
    - The method returns `ans` which is 2.

### Summary

- **Total Moves Required**: 2
- This matches our understanding that two moves are needed: one move of a coin from the root to the left child and one move of a coin from the root to the right child. This ensures each node has exactly one coin.

Thus, the dry run confirms that the algorithm correctly calculates the minimum number of moves required to distribute the coins such that every node has exactly one coin.
