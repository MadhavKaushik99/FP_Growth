# FP_Growth
Implemented FP Growth Algorithm in Python for Association Mining

FP Growth implements tree, linked list, and the concept of depth-first search. The process can be split into two main stages, each stage can be further divided into two steps.

Stage 1: FP tree construction

Step 1: Cleaning and sorting For each transaction, we first remove the items that are below the minimum support. Then, we sort the items in frequency support descending order.

Step 2: Construct FP tree, header table with cleaned itemsets Loop through the cleaned itemsets, map it to the tree one at a time. If any item already exists in the branch, they share the same node and the count is incremented. Else, the item will be on the new branch created. The header table is also constructed during this procedure. There’s a linked list for each unique item in the transactions. With the linked list, we can find the occurrence of the item on the tree in a short period of time without traversing the tree.

Stage 2: Mine the main tree and conditional FP trees

Step 1: Divide the main FP tree into conditional FP trees Staring from each frequent 1-pattern, we create conditional pattern bases with the set of prefixes in the FP tree. Then, we use those pattern bases to construct conditional FP trees with the exact same method in Stage 1.

Step 2: Mine each conditional trees recursively The frequent patterns are generated from the conditional FP Trees. One conditional FP tree is created for one frequent pattern. The recursive function we used to mine the conditional trees is close to depth-first search. It makes sure that there is no more trees can be constructed with the remaining items before moving on.
