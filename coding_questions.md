# Coding Questions

## 339. Nested List Weight Sum
Master both DFS and BFS. Memorize answers.

## 364. Nested List Weight Sum II
Master DFS for now. Memorize both two pass and one pass.

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
If the words differ, I track their last positions as I scan.

## 245. Shortest Word Distance III
If the words differ, I track their last positions as I scan.
If the words are the same, I track consecutive occurrences using previous_position. Both cases run in O(N) time.

# TODO

## 146. LRU Cache

## 716. Max Stack
Difficult
