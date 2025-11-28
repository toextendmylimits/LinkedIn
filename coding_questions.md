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

## 146. LRU Cache
I implement LRU Cache using two structures: a hash map and a doubly linked list.  
The hash map gives O(1) access to nodes.  
The linked list keeps keys ordered by recency—most recent at the head, least recent at the tail.  
Whenever I get or update a key, I move its node to the head.  
When inserting a new key and the cache is full, I evict the node at the tail, which is the least recently used.  
This design guarantees O(1) get and put.  

## 205. Isomorphic Strings
## 1004. Max Consecutive Ones III
## 17. Letter Combinations of a Phone Number
Don't remember to return when path length equal to digits count

## 46. Permutations
Practice again. Not very familiar.

We generate all permutations using backtracking.  
We build a permutation step by step, and at each step we choose any unused number.  
We keep a used[] array to avoid reusing numbers.  
When the path reaches length n, we copy it into the result.  
After each recursive call, we undo the choice (pop + mark unused) to explore the next possibility.  
This guarantees we explore all n! permutations.  

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
I use Kadane’s algorithm.  
As I scan the array, I keep a running total for the best subarray ending at each position.  
At every step, I choose whether to start a new subarray or continue the previous one.  
If the running total becomes negative, I reset it because it can’t help future sums.  
While doing this, I track the best overall sum.  
This gives a linear-time, constant-space solution.  

## 34. Find First and Last Position of Element in Sorted Array 
I use binary search twice.  
The first search finds the first position where the target appears by always moving left when we see the target.  
The second search finds the last position by always moving right when we see the target.  
Both searches run in O(log n), so the overall runtime is O(log n).  

## 152. Maximum Product Subarray

We track both the max and min product ending at each position. For each new number, we consider three choices:   
the number itself, number × previous max, and number × previous min.   
We include the number alone because sometimes it's better to start a new subarray,   
especially after zeros or when previous products become worse than starting fresh.   
Then we pick the best and worst of the three, update global max, and move on. This handles negatives and zeros correctly in O(n).

## 297. Serialize and Deserialize Binary Tree 

I use preorder DFS to serialize the tree.  
Every node is recorded as its value, and I use "x" for null pointers.  
This sequence uniquely describes the tree because preorder always visits: node → left → right.  

To deserialize, I read the values in order using an iterator.  
Whenever I see "x" I return None; otherwise I create a node and recursively build its left and right subtrees.  
Because serialize and deserialize follow the same preorder structure, the original tree is reconstructed exactly.  

## 380. Insert Delete GetRandom O(1)  
I use a list called values to store all elements, and a hash map index_map that maps each value to its index in the list.  
Insert: append the element and record its index.  
Remove: swap the element with the last element, update the map, then pop it.  
GetRandom: choose a random element from values.  
This makes insert, remove, and getRandom all O(1).  

## 605. Can Place Flowers 
We scan the flowerbed from left to right.  
Whenever we see a 0, we check its left and right neighbors:  

left is empty (or out of bounds), and  

right is empty (or out of bounds)  

→ we can plant a flower here. Set this position to 1 and reduce n by 1.  
If n ever becomes 0, return true.  
If we finish scanning and n > 0, return false.  

This works in O(N) time and modifies the array in-place.  

## 156. Binary Tree Upside Down

I recursively go to the leftmost node, because that will become the new root.  
Then when the recursion unwinds, I rewire the pointers:  
The original left child’s left pointer becomes the original right child, and its right pointer becomes the original root.  
Finally, I clear root.left and root.right so the structure doesn’t form cycles.  

# TODO

## 272. Closest Binary Search Tree Value II





constraints.  
