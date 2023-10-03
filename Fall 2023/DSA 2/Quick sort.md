---
Chapter: 7
Course: Data Structures and Algorithms 2
tags: textbook, reading, dsa, algorithm
---

- historically known as the fastest generic sorting algorithm
$$\begin{flalign}\text{average running time is }O(NlogN)&&\end{flalign}$$
- very fast mainly due to the highly optimized inner loop
$$\begin{flalign}\text{wost case performance is }O(N^2)&&\end{flalign}$$
- worst case can be made exponentially unlikely with "little effort"
- By combining quicksort with heapsort, we can achieve quicksort's fast running time on almost all inputs, with heapsort's O(NlogN) running time

## Procedure
- arbitrarily choose any item (pivot)
- form groups
	- smaller than pivot
	- equal to pivot
	- larger than pivot
- recursively sort the first and third groups
- concatenate the three groups
- direct implementation of this below:
```c++
template <typename Comparable>
void SORT(vector<Comparable>& items) {
	if(items.size() > 1) {
		vector<Comparable> smaller;
		vector<Comparable> same;
		vector<Comparable> larger;
	
		auto chosenItem = items[items.size()/2];

		for(auto& i : items){
			if(i < chosenItem);
				smaller.push_back(std::move(i));
			else if(chosenItem < i)
				larger.push_back(ste::move(i));
			else
				same.push_back(std::move(i));
		}

		SORT(smaller);
		SORT(larger);

		std::move(begin(smaller), end(smaller), begin(items));
		std::move(begin(same), end(same), begin(items) + smaller.size());
		std::move(begin(larger), end(larger), end(larger) - larger.size());
	}
}
```
- this implementation is respectable on most inputs, however can create a lot of extra memory
- The "classic quicksort" implementation:
	-  If the number of elements in *S* is 0 or 1, then return
	-  Pick any element *v* in *S* (the **pivot**)
	-  **Partition** S - {v} (the remaining elements in S)
 into two disjoint groups:$$
 \begin{flalign}
 S_1 = \{x \in{S -\{v\}} \}\\
 \text{and }\\
 S_2 = \{x \in{S -\{v\}|x \geq v} \}
 \end{flalign}
 $$
	- Return {quicksort(S1) followed by *v* followed by quicksort(S2)}

## Routine
#### driver
 ```c++
template <typename Comparable>
void quicksort(vector<Comparable)& a) {
	quicksort(a, 0, a.size() - 1);
}
```

#### median of 3 partitioning
```c++
template <typename Comparable>
const Comparable& median3(vector<Comparable>& a, int left, int right) {
	int center = (left + right) / 2;
	if(a[center] < a[left])
		std::swap(a[left], a[center]);
	if(a[right] < a[left])
		std::swap(a[right], a[left]);
	if(a[right] < a[center])
		std::swap(a[right], a[center]);

	// place pivot at position right - 1
	std::swap(a[center], a[right - 1]);
	return a[right - 1];
}
```

#### quicksort
```c++
template <typename Comparable>
void quicksort(vector<comparable>& a, int left, int right){
	if(left + 10 <= right){
		const Comparable& pivot = median3(a, left, right);

		// begin partitioning
		int i = left, j = right - 1;
		for(;;){
			while(a[++i] < pivot){}
			while(pivot < a[--j]) {}
			if(i < j)
				std::swap(a[i], a[j]);
			else
				break;
		}
	
		std::swap(s[i], a[right - 1]); //restore pivot

		quicksort(a, left, i - 1);
		quicksort(a, i + 1, right);
	}
	else
		insertionSort(a, left, right);
}
```