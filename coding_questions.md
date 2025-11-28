# Coding Questions

## 339. Nested List Weight Sum
### DFS
I use a depth-first search helper function that takes a list and a current depth.  
For each element:  
• If it’s an integer, I add integer * depth to the sum.  
• If it’s a nested list, I recursively process that list with depth + 1.  

### BFS
I use level-order BFS; each level corresponds to a depth, so I multiply integers by that depth and expand lists into the queue for the next level.”

Master both DFS and BFS. Memorize answers.

## 364. Nested List Weight Sum II
Master DFS for now. Memorize both two pass and one pass.

### DFS
This problem weights integers based on maxDepth − depth + 1, so I need the maximum depth first.  

I do two passes using DFS:  
• In the first DFS, I traverse the entire structure to compute maxDepth.  
• In the second DFS, I multiply each integer by its weight based on depth:  

weight = maxDepth - depth + 1  

DFS is ideal because it naturally tracks depth as it goes deeper into nested lists.  

Time complexity is O(N) for both passes combined.  

### BFS
I traverse the list level-by-level.
I keep a runningSum of all integers seen so far.
At each level, I add new integers into it, and then add that cumulative runningSum to the final result.
This naturally gives larger weights to shallow levels because their values are included in the total more times.

## 432. All O`one Data Structure
“I maintain a doubly-linked list of buckets sorted by frequency.
Each bucket represents a frequency and contains all keys with that frequency.

I also keep a hash map from each key to its current bucket node.

inc(key) moves the key to the bucket with freq+1, which is always immediately to the right in the sorted list.

dec(key) moves it to the bucket with freq-1, which is always immediately to the left.
(Creating the bucket if it does not exist.)

If a bucket becomes empty, I remove it, preserving a sorted list of frequencies.

Because the list is always sorted:

head.next always holds the minimum count

tail.prev always holds the maximum count

This gives O(1) for all operations, including getMinKey() and getMaxKey().”

## 716. Max Stack

### DLL + MAX HEAP
I implement the stack as a doubly linked list, so I can push, pop, and  
remove any specific node in O(1).  

For tracking the maximum, I maintain a max-heap, where each entry stores  
(-value, -sequenceId, nodePointer).  

-value turns Python’s min-heap into a max-heap, and -sequenceId ensures  
that among equal values, the most recently pushed element is chosen,  
matching the “top-most max” requirement.  

When a node is removed through the stack, I mark it as dead. The heap may  
still contain stale entries, so peekMax and popMax lazily skip dead  
nodes.  

This gives O(1) top/pop and O(log n) push/popMax, satisfying the  

## 205. Isomorphic Strings
## 1004. Max Consecutive Ones III
## 17. Letter Combinations of a Phone Number
Don't remember to return when path length equal to digits count

## 46. Permutations
Practice again. Not very familiar.

## 101. Symmetric Tree

## 104. Maximum Depth of Binary Tree

## 235. Lowest Common Ancestor of a Binary Search Tree

## 244. Shortest Word Distance II
I store all positions of each word, then use a two-pointer scan over the two sorted index lists to compute the shortest distance in O(m+n) per query.”

## 243. Shortest Word Distance
I track the most recent positions of both words as I scan the list once. Every time I have valid positions for both, I update the minimum distance. This gives an O(N) one-pass O(1)-space solution.

## 245. Shortest Word Distance III
If the words differ, I track their last positions as I scan.
If the words are the same, I track consecutive occurrences using previous_position. Both cases run in O(N) time.

## 277. Find the Celebrity
I first identify a single candidate by eliminating people who cannot be celebrities—anyone the candidate knows is automatically disqualified. After one linear pass, only one person can still be a celebrity. Then I verify that this person knows nobody and that everyone knows them. If both conditions hold, they are the celebrity; otherwise, there is none

## 53. Maximum Subarray
I use Kadane’s algorithm: as I scan the array, I keep the best subarray ending at each position, reset when the running sum turns negative, and track the highest sum overall. It runs in linear time and constant space.

# TODO

## 146. LRU Cache


constraints.  
