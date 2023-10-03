---
Chapter: 7
Course: Data Structures and Algorithms
tags: textbook, reading, dsa, algorithm
---

# The Algorithm
- consists of N - 1 passes.
- For pass p=1 through N-1, ensures the elements in positions 0 - p-1 are sorted

## Procedure
- in pass p, move the element in position p left until it is in the correct place among the first p+1 elements
- this is done without explicit swaps by storing the element in position p to `tmp` and all larger elements are moved one position to the right
- then tmp is moved to the correct spot
	- same as in binary heaps
>see pg. 293 in [[DataStructures.pdf|the Textbook]]

```c++
/**
 * Simple insertion sort.
 */

template <typename Comparable>
void insertionSort(vector<Comparable>& a){
	for(int p = 1; p < a.size(); ++p){
		Comparable tmp = std::move(a[p]);

		int j;
		// find the correct place to insert tmp, and move all elements to the right one as we go
		for(j = p; j > 0 && tmp < a[j-1]; --j){
			a[j] = std::move(a[j-1]);
		}
		// insert tmp into the correct place in the array
		a[j] = std::move(tmp);
	}
}
```

### The STL Implementation
- Instead of having the sort routines take an array of comparable items as a single parameter
- The sort routines receive a pair of iterators that represent the start and end marker of a range
- A two-parameter sort routine uses just a pair of iterators and presumes that the items can be ordered, while a three-parameter sort routine has a function object as a third parameter
- Converting the algorithm to use the STL introduces several issues:
	1. We must provide a two-parameter sort and a three-parameter sort. presumably the two parameter sort invokes the three-parameter sort with `less<Object>{ }` as the third parameter
	2. Array access must be converted to iterator access
	3. Line 11 of the original code requires that we create `tmp` which in the new code will have type `Object`
- The first issue is the trickiest because the template type parameters for the two-parameter sort are both `Iterator`; however, `Object` is not one of the generic type parameters
	- C++11 introduces the `decltype` which cleanly expresses the intent
- [[DataStructures.pdf|Figure7.3]] on page 294 shows the implementation for the two-parameter sort
below is the three-parameter sort implementation
```c++
template <typename Iterator, typename Comparator>
void insertionSort(const Iterator& begin, const Iterator& end, Comparator lessThan) {
	if(begin == end)
		return;
	Iterator j;
	for(Iterator p = begin+1; p != end; ++p){
		auto tmp = std::move(*p);
		for(j = p; j != begin && lessThan(tmp, *(j-1*), --j)
			*j = std::move(*(j-1));
		*j = std::move(tmp);
	}
}
```
