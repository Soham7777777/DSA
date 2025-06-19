# Algorithm Analysis:
---

- Qualities of a good program:
  - runs correctly
  - runs efficiently (executes in minimum time with minimum memory space)
  - easy to read and understand
  - easy to debug
  - easy to modify

**Data:** A value or set of values associated with a variable or constant.
  - If a data item does not have subordinate data items then its categorized as elementary data item else its called a group item.

**Record:** Collection of data items.

**File:** Collection of related records
  - Each record in a file may consist a certain data item that uniquely identifies the record, which is known as primary key.

**Data Structure:** A group of data elements that put together under one name which defines a particular way of storing and organizing data.

**Selection of Data Structure:**
- determine the basic operations that must be supported
- Quantify the resource constraints for each operation
- select the data structure that best meets the requirements


## Classification of Data Structures:

**Primitive:** Fundamental data types which are supported by a programming language. e.g. bool, char, int, float etc...


### Non-primitive:

- Created using primitive data structures. Classified in two categories:

**Liner data structure:** Elements of data stored in sequential order. e.g. arrays, linked lists, stacks and queues.
  - The liner relation ship is achieved either by having sequential memory locations or by having links.

**Non-liner data structure:** Elements of data are not stored in sequential order. e.g. trees and graphs.


### Data Structures:

**Array:** Fixed length collection of similar data elements, stored in consecutive memory locations and referenced by an index.

**Linked-list:** Variable length collection of similar data elements, stored in nodes connected sequentially by links and referenced by its head node.

**Stack:** A last-in-first-out linear data structure that allows insertion and deletion of elements at only one end.

**Queue:** A first-in-last-out linear data structure that allows insertion of elements at one end and deletion at other end.

**Tree:** A non-linear data structure that consist of collection of nodes arranged in a hierarchical order referenced by a root node which is at the top of hierarchy.

**Graph:** A non-liner data structure that consist of collection of nodes and, edges that connect these nodes.


### Operations on Data Structures:

**Traversing:** Access each data item exactly once so that it can be processes.

**Searching:** Find the location of one or more data items that satisfy the given constraint, which may or may not be present in the collection.

**Sorting:** Arrange the items in particular order.

**Merging:** Combine tow sorted collections to form a single sorted collection.

**Insertion:** Add new data item in the given collection.

**Deletion:** Remove a particular data item in the given collection.


## Abstract Data Type:

**Data Type:** Data items with certain characteristics and permissible operations fall under the same category of data type.

**Abstract Data Type:** Data types that can be used without having to know the implementation details.


### Advantages:

- The implementation can be modified or substitute completely new without changing the data type usage, e.g. changing the implementation of stack by using linked-list instead of array which doesn't break the code that already uses the stack.

**Algorithm:** A formally defined procedure for performing some calculations to solve a problem and has finite number of steps.


### Approach to Design Algorithm:

- Complex algorithm is divided into smaller units called modules, this process is known as modularization which as below advantages:
  - Divides complex algorithm in simple and manageable chunks thus easy to design and implement.
  - Each module can be implemented independently which simplifies the implementation of algorithm and simple to test, debug, document and maintain.

- Two approaches of modularization:
  
  - **Top-down approach:** Divide complex algorithm into modules which allows stepwise refinement where we start with an abstract design and make it concrete at each level of refinement.
  
  - **Bottom-up approach:** Start with most concrete modules and then proceed towards designing higher level modules by grouping sub-modules.

Design of complex algorithm is blend of top-down and bottom-up approach.


### Control structures used in algorithms:

**Sequence:** Each step is executed in specified order, conveniently top to bottom.

**Decision:** Next step of execution depends on outcome of some condition.

**Repetition:** Execute one or more steps for a number of times.


## Time and Space Complexity:

**Time complexity:** Running time of the program as a function of input size.

**Space complexity:** Amount of computer memory required to run the program as a function of input size.
  - **Fixed part:** Memory allocated for storing instructions, constants, variables, structures, etc... that initializes the program.
  - **Variable part:** Memory allocated during runtime which includes recursion stack and dynamic memory allocation.


### Time Complexity Cases:

**Worst case:** Behavior of an algorithm with respect to worst possible case of input instance.

**Average case:** Behavior of an algorithm with respect to 'average' input instance that is randomly drawn from given distribution with all inputs of given size are equally likely.

**Best case:** Behavior of an algorithm under optimal conditions.

**Amortized running time:** Time required to perform a sequence of related operations averaged over all the operations performed, this guarantees the average performance for each operation in the worst case.


### Time-Space Trade-off:

- There may be more than one way to solve same problem with different algorithms that requires different memory and time constraints. Algorithms are chosen based on current major concern e.g. memory is sacrificed for time, or time is sacrificed for memory if memory is major concern.


- The time complexity is expressed as `f(n)` where is n is the input size.
  - This is used to predict the rate of growth of complexity as the input size increased.
  - Compare different algorithms that solves the same problem.

- Efficiency of algorithm is directly proportional to the number of iterations in each loop.


### Types of Loops:

**Liner loops:**
```
for(i=0;i<100;i++) -> f(n) = n

for(i=0;i<100;i+=2) -> f(n) = n/2
```

**Logarithmic loops:**
```
for(i=1;i<1000;i*=2) -> f(n) = log2(n)

for(i=1000;i>=1;i/=2) -> f(n) = log2(n)
```

**Nested loops**:
```
Liner logarithmic loop:
  for(i=0;i<10;i++) -> f(n) = n
    for(j=1; j<10;j*=2) -> f(n) = log2(n)
  
  time complexity: n x log(n)
```
```
Quadratic loop:
  for(i=0;i<10;i++) -> f(n) = n
    for(j=0; j<10;j++) -> f(n) = n

  time complexity: n^2
```
```
Dependent quadratic loop:
  for(i=0;i<10;i++) -> f(n) = n
    for(j=0; j<=i;j++) -> f(n) = (n+1)/2
  
  time complexity: n x ((n+1)/2)
```

**Exponential loops:**
```
for (int i = 1; i*i <= n; i++) -> f(n) = sqrt(n)

void backtrack(string s) {
    if (s.length() == n) return;
    backtrack(s + "0");
    backtrack(s + "1");
} -> f(n) = 2^n

void generateSequences(vector<int>& seq, int n, int k) {
    if (seq.size() == k) {
        // Process the k-length sequence
        for (int num : seq) cout << num << " ";
        cout << endl;
        return;
    }
    
    for (int i = 0; i < n; i++) {
        seq.push_back(i);  // Choose an element
        generateSequences(seq, n, k);  // Recurse
        seq.pop_back();  // Backtrack
    }
} -> f(n) = k^n
```

**Factorial loops:**
```
void permute(vector<int>& nums, int index) {
    if (index == nums.size()) return;
    for (int i = index; i < nums.size(); i++) {
        swap(nums[i], nums[index]);
        permute(nums, index + 1);
        swap(nums[i], nums[index]);
    }
} -> f(n) = n!
```

**Log-logarithmic loops:**
```
for (int i = 2; i <= n; i = pow(i, 2)) -> f(n) = log(log(n))
```
