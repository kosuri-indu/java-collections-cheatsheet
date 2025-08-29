# Java Collections Cheat Sheet

This cheat sheet covers the most commonly used data structures in Java Collections, with their main methods, time complexities, and usage examples. Use this as a quick reference for coding and interviews.

## 1. List

### What is it?

A List is an ordered collection that allows duplicate elements. You can access elements by index.

### Declaration & Instantiation

```java
List<Integer> arrayList = new ArrayList<>();
List<Integer> linkedList = new LinkedList<>();
```

### Common Methods

| Method             | Description               | ArrayList Time | LinkedList Time |
| ------------------ | ------------------------- | -------------- | --------------- |
| add(E e)           | Add element               | O(1) amortized | O(1)            |
| add(int idx, E e)  | Add at index              | O(n)           | O(n)            |
| get(int idx)       | Get element at index      | O(1)           | O(n)            |
| remove(int idx)    | Remove at index           | O(n)           | O(n)            |
| contains(Object o) | Check if contains element | O(n)           | O(n)            |
| size()             | Get size                  | O(1)           | O(1)            |
| clear()            | Remove all elements       | O(n)           | O(n)            |

### Example

```java
List<String> names = new ArrayList<>();
names.add("Alice");
names.add("Bob");
System.out.println(names.get(0)); // Alice
```

**Note:**

- Use `ArrayList` for fast random access, `LinkedList` for frequent insertions/deletions.
- `LinkedList` can also be used as a queue or stack.

## 2. Set

### What is it?

A Set is a collection that does not allow duplicate elements.

### Declaration & Instantiation

```java
Set<Integer> hashSet = new HashSet<>();
Set<Integer> linkedHashSet = new LinkedHashSet<>();
Set<Integer> treeSet = new TreeSet<>();
```

### Common Methods

| Method             | Description               | HashSet Time | LinkedHashSet Time | TreeSet Time |
| ------------------ | ------------------------- | ------------ | ------------------ | ------------ |
| add(E e)           | Add element               | O(1)         | O(1)               | O(log n)     |
| remove(Object o)   | Remove element            | O(1)         | O(1)               | O(log n)     |
| contains(Object o) | Check if contains element | O(1)         | O(1)               | O(log n)     |
| size()             | Get size                  | O(1)         | O(1)               | O(1)         |
| clear()            | Remove all elements       | O(n)         | O(n)               | O(n)         |

### Example

```java
Set<String> set = new HashSet<>();
set.add("apple");
set.add("banana");
System.out.println(set.contains("apple")); // true
```

**Note:**

- `HashSet` is unordered, `LinkedHashSet` maintains insertion order, `TreeSet` is sorted.

## 3. Queue

### What is it?

A Queue is a collection for holding elements prior to processing (FIFO).

### Declaration & Instantiation

```java
Queue<Integer> linkedListQueue = new LinkedList<>();
Queue<Integer> arrayDequeQueue = new ArrayDeque<>();
```

### Common Methods

| Method      | Description         | LinkedList Time | ArrayDeque Time |
|-------------|--------------------|-----------------|-----------------|
| offer(E e)  | Add to queue       | O(1)            | O(1)            |
| poll()      | Remove head        | O(1)            | O(1)            |
| peek()      | View head          | O(1)            | O(1)            |
| isEmpty()   | Check if empty     | O(1)            | O(1)            |

### Example

```java
Queue<Integer> q = new LinkedList<>();
q.offer(1);
q.offer(2);
System.out.println(q.poll()); // 1

Queue<Integer> q2 = new ArrayDeque<>();
q2.offer(10);
q2.offer(20);
System.out.println(q2.poll()); // 10
```

**Note:**
- `offer` and `poll` are preferred over `add` and `remove` as they do not throw exceptions on failure.
- `ArrayDeque` is usually faster than `LinkedList` for queue operations.

## 4. Deque (Double-Ended Queue)

### What is it?

A Deque allows insertion and removal at both ends.

### Declaration & Instantiation

```java
Deque<Integer> deque = new ArrayDeque<>();
```

### Common Methods

| Method        | Description       | Time Complexity |
| ------------- | ----------------- | --------------- |
| addFirst(E e) | Add to front      | O(1)            |
| addLast(E e)  | Add to end        | O(1)            |
| removeFirst() | Remove from front | O(1)            |
| removeLast()  | Remove from end   | O(1)            |
| peekFirst()   | View front        | O(1)            |
| peekLast()    | View end          | O(1)            |

### Example

```java
Deque<Integer> d = new ArrayDeque<>();
d.addFirst(1);
d.addLast(2);
System.out.println(d.removeFirst()); // 1
```

## 5. Stack

### What is it?

A Stack is a LIFO (last-in, first-out) data structure.

### Declaration & Instantiation

```java
Stack<Integer> stack = new Stack<>();
Deque<Integer> stack2 = new ArrayDeque<>();
```

### Common Methods

| Method    | Description     | Time Complexity |
| --------- | --------------- | --------------- |
| push(E e) | Add to top      | O(1)            |
| pop()     | Remove from top | O(1)            |
| peek()    | View top        | O(1)            |
| isEmpty() | Check if empty  | O(1)            |

### Example

```java
Stack<Integer> s = new Stack<>();
s.push(10);
s.push(20);
System.out.println(s.pop()); // 20
```

**Note:**

- Prefer `ArrayDeque` for stack operations over `Stack` class.

## 6. Map

### What is it?

A Map stores key-value pairs. Keys are unique.

### Declaration & Instantiation

```java
Map<String, Integer> hashMap = new HashMap<>();
Map<String, Integer> linkedHashMap = new LinkedHashMap<>();
Map<String, Integer> treeMap = new TreeMap<>();
```

### Common Methods

| Method                | Description         | HashMap Time | LinkedHashMap Time | TreeMap Time |
|-----------------------|--------------------|--------------|--------------------|--------------|
| put(K key, V value)   | Add or update value| O(1)         | O(1)               | O(log n)     |
| get(Object key)       | Get value by key   | O(1)         | O(1)               | O(log n)     |
| remove(Object key)    | Remove by key      | O(1)         | O(1)               | O(log n)     |
| containsKey(Object k) | Check if key exists| O(1)         | O(1)               | O(log n)     |
| keySet()              | Get all keys       | O(n)         | O(n)               | O(n)         |
| values()              | Get all values     | O(n)         | O(n)               | O(n)         |

### Example

```java
Map<String, Integer> map = new HashMap<>();
map.put("a", 1);
map.put("b", 2);
System.out.println(map.get("a")); // 1

// Common interview pattern: counting characters
String s = "hello";
Map<Character, Integer> freq = new HashMap<>();
for (char ch : s.toCharArray()) {
	freq.put(ch, freq.getOrDefault(ch, 0) + 1);
}
System.out.println(freq); // {h=1, e=1, l=2, o=1}
```

**Note:**
- `HashMap` is unordered, `LinkedHashMap` maintains insertion order, `TreeMap` is sorted by key.

## 7. PriorityQueue

### What is it?

A PriorityQueue is a queue where elements are ordered by priority.

### Declaration & Instantiation

```java
PriorityQueue<Integer> pq = new PriorityQueue<>();
```

### Common Methods

| Method     | Description    | Time Complexity |
| ---------- | -------------- | --------------- |
| offer(E e) | Add element    | O(log n)        |
| poll()     | Remove min/max | O(log n)        |
| peek()     | View min/max   | O(1)            |

### Example

```java
PriorityQueue<Integer> pq = new PriorityQueue<>();
pq.offer(5);
pq.offer(1);
System.out.println(pq.poll()); // 1
```

**Note:**

- By default, it is a min-heap. Use a custom comparator for max-heap.

This cheat sheet is a quick reference. For more details, check the [Java documentation](https://docs.oracle.com/javase/8/docs/api/java/util/package-summary.html).

---

## 8. Common Coding Patterns & Interview Snippets

### List
```java
// Iterate with index
for (int i = 0; i < list.size(); i++) {
	System.out.println(list.get(i));
}
// Iterate with for-each
for (String s : list) {
	System.out.println(s);
}
// Remove all elements matching a condition
list.removeIf(x -> x < 0);
```

### Set
```java
// Remove duplicates from a list
List<Integer> nums = Arrays.asList(1, 2, 2, 3);
Set<Integer> unique = new HashSet<>(nums);
// Check if two sets have common elements
set1.retainAll(set2); // modifies set1 to keep only common elements
```

### Queue
```java
// BFS template
Queue<Integer> q = new LinkedList<>();
q.offer(start);
while (!q.isEmpty()) {
	int node = q.poll();
	// process node
}
```

### Deque
```java
// Sliding window maximum
Deque<Integer> dq = new ArrayDeque<>();
for (int i = 0; i < n; i++) {
	while (!dq.isEmpty() && arr[dq.peekLast()] <= arr[i]) dq.pollLast();
	dq.offerLast(i);
	if (dq.peekFirst() <= i - k) dq.pollFirst();
	// arr[dq.peekFirst()] is max in window
}
```

### Stack
```java
// Valid parentheses
Stack<Character> st = new Stack<>();
for (char ch : s.toCharArray()) {
	if (ch == '(') st.push(ch);
	else if (ch == ')' && !st.isEmpty()) st.pop();
	else return false;
}
return st.isEmpty();
```

### Map
```java
// Frequency count (characters, words, etc.)
map.put(key, map.getOrDefault(key, 0) + 1);
// Iterate over entries
for (Map.Entry<String, Integer> entry : map.entrySet()) {
	System.out.println(entry.getKey() + ": " + entry.getValue());
}
// Grouping by value
Map<Integer, List<String>> groups = new HashMap<>();
groups.computeIfAbsent(val, k -> new ArrayList<>()).add(str);
```

### PriorityQueue
```java
// Max heap
PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());
// Custom comparator
PriorityQueue<int[]> pq = new PriorityQueue<>((a, b) -> a[1] - b[1]);
```

---

## 9. Utilities & Useful Functions

### Arrays Class

| Method                        | Description                                 |
|-------------------------------|---------------------------------------------|
| Arrays.sort(arr)              | Sorts the array in ascending order          |
| Arrays.sort(arr, cmp)         | Sorts array with custom comparator          |
| Arrays.toString(arr)          | Returns string representation of array      |
| Arrays.equals(arr1, arr2)     | Checks if two arrays are equal              |
| Arrays.fill(arr, val)         | Fills array with given value                |
| Arrays.binarySearch(arr, key) | Binary search (sorted array required)       |

#### Examples
```java
int[] arr = {3, 1, 2};
Arrays.sort(arr); // [1, 2, 3]
System.out.println(Arrays.toString(arr)); // [1, 2, 3]

// Custom sort (descending)
Integer[] nums = {3, 1, 2};
Arrays.sort(nums, Collections.reverseOrder());
System.out.println(Arrays.toString(nums)); // [3, 2, 1]

// Fill
Arrays.fill(arr, 5); // arr = [5, 5, 5]

// Binary search
int idx = Arrays.binarySearch(arr, 5); // returns index if found, else (-(insertion point) - 1)
```

### Collections Class

| Method                              | Description                                 |
|-------------------------------------|---------------------------------------------|
| Collections.sort(list)              | Sorts list in ascending order               |
| Collections.sort(list, cmp)         | Sorts list with custom comparator           |
| Collections.reverse(list)           | Reverses the list                           |
| Collections.shuffle(list)           | Randomly shuffles the list                  |
| Collections.binarySearch(list, key) | Binary search (sorted list required)        |
| Collections.max(list)               | Returns max element                         |
| Collections.min(list)               | Returns min element                         |
| Collections.frequency(list, obj)    | Counts occurrences of obj in list           |

#### Examples
```java
List<Integer> list = Arrays.asList(3, 1, 2);
Collections.sort(list); // [1, 2, 3]
Collections.reverse(list); // [3, 2, 1]
Collections.shuffle(list); // random order
int idx = Collections.binarySearch(list, 2);
int max = Collections.max(list);
int freq = Collections.frequency(list, 2);
```

### String & Array Utilities

```java
// Convert array to string
int[] arr = {1, 2, 3};
System.out.println(Arrays.toString(arr)); // [1, 2, 3]

// Convert int to string
int n = 123;
String s = String.valueOf(n); // "123"

// Convert list to array
List<Integer> list = Arrays.asList(1, 2, 3);
Integer[] arr2 = list.toArray(new Integer[0]);

// Convert array to list
List<Integer> list2 = Arrays.asList(arr2);
```

### Comparator & Comparable

#### Comparable (Natural Ordering)
Implement `Comparable<T>` and override `compareTo()` for custom objects.

```java
class Person implements Comparable<Person> {
	int age;
	public Person(int age) { this.age = age; }
	@Override
	public int compareTo(Person other) {
		return Integer.compare(this.age, other.age); // ascending
	}
}

List<Person> people = Arrays.asList(new Person(30), new Person(20));
Collections.sort(people); // sorts by age ascending
```

#### Comparator (Custom Ordering)
Pass a Comparator to sort or data structures.

```java
// Sort by descending age
Collections.sort(people, (a, b) -> b.age - a.age);

// For PriorityQueue
PriorityQueue<Person> pq = new PriorityQueue<>((a, b) -> a.age - b.age); // min-heap by age
```

**Note:**
- Use `Comparator.comparing(Person::getAge)` for more readable code in Java 8+.
