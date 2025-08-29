# Java Collections Cheat Sheet

This cheat sheet covers the most commonly used data structures in Java Collections, with their main methods, time complexities, and usage examples. Use this as a quick reference for coding and interviews.

**Note on Amortized Time:**
Amortized time means that while a single operation might occasionally take longer, the average time per operation over a sequence of operations is as stated. For example, `ArrayList.add()` is O(1) amortized because most adds are O(1), but sometimes resizing the array takes O(n).

## 1. List

### What is it?

A List is an ordered collection that allows duplicate elements. You can access elements by index.

### Declaration & Instantiation

```java
List<Integer> arrayList = new ArrayList<>();
List<Integer> linkedList = new LinkedList<>();
```

### Common Methods

| Method             | Description               | ArrayList Time | LinkedList Time | Example            |
| ------------------ | ------------------------- | -------------- | --------------- | ------------------ |
| add(E e)           | Add element               | O(1) amortized | O(1)            | list.add("a")      |
| add(int idx, E e)  | Add at index              | O(n)           | O(n)            | list.add(1, "a")   |
| get(int idx)       | Get element at index      | O(1)           | O(n)            | list.get(0)        |
| remove(int idx)    | Remove at index           | O(n)           | O(n)            | list.remove(0)     |
| contains(Object o) | Check if contains element | O(n)           | O(n)            | list.contains("a") |
| size()             | Get size                  | O(1)           | O(1)            | list.size()        |
| clear()            | Remove all elements       | O(n)           | O(n)            | list.clear()       |

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

| Method             | Description               | HashSet Time | LinkedHashSet Time | TreeSet Time | Example         |
| ------------------ | ------------------------- | ------------ | ------------------ | ------------ | --------------- |
| add(E e)           | Add element               | O(1)         | O(1)               | O(log n)     | set.add(1)      |
| remove(Object o)   | Remove element            | O(1)         | O(1)               | O(log n)     | set.remove(1)   |
| contains(Object o) | Check if contains element | O(1)         | O(1)               | O(log n)     | set.contains(1) |
| size()             | Get size                  | O(1)         | O(1)               | O(1)         | set.size()      |
| clear()            | Remove all elements       | O(n)         | O(n)               | O(n)         | set.clear()     |

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
// LinkedList can be used as Queue, Deque, or List
Queue<Integer> linkedListQueue = new LinkedList<>();
Queue<Integer> arrayDequeQueue = new ArrayDeque<>();
LinkedList<Integer> ll = new LinkedList<>(); // for all List, Queue, Deque methods
```

### Common Methods

| Method         | Description                | LinkedList Time | ArrayDeque Time | Example                |
| -------------- |---------------------------|-----------------|-----------------|------------------------|
| offer(E e)     | Add to queue (preferred)  | O(1)            | O(1)            | q.offer(1)             |
| add(E e)       | Add to queue (throws ex)  | O(1)            | O(1)            | q.add(1)               |
| poll()         | Remove head (preferred)   | O(1)            | O(1)            | q.poll()               |
| remove()       | Remove head (throws ex)   | O(1)            | O(1)            | q.remove()             |
| peek()         | View head                 | O(1)            | O(1)            | q.peek()               |
| isEmpty()      | Check if empty            | O(1)            | O(1)            | q.isEmpty()            |
| addAll(c)      | Add all elements          | O(m)            | O(m)            | q.addAll(list)         |
| removeAll(c)   | Remove all in collection  | O(n*m)          | O(n*m)          | q.removeAll(list)      |

### Example

```java
Queue<Integer> q = new LinkedList<>();
q.offer(1);
q.add(2);
System.out.println(q.poll()); // 1

Queue<Integer> q2 = new ArrayDeque<>();
q2.offer(10);
q2.add(20);
System.out.println(q2.poll()); // 10

// Add all elements from a list
List<Integer> nums = Arrays.asList(3, 4, 5);
q.addAll(nums);
// Remove all elements in another collection
q.removeAll(nums);
```

**Note:**

- `offer` and `poll` are preferred over `add` and `remove` as they do not throw exceptions on failure.
- `add` and `remove` throw exceptions if the operation fails (e.g., empty queue).
- `addAll` and `removeAll` are useful for batch operations.
- `ArrayDeque` is usually faster than `LinkedList` for queue operations.
- `LinkedList` implements List, Queue, and Deque interfaces, so it can be used flexibly.

## 4. Deque (Double-Ended Queue)

### What is it?

A Deque allows insertion and removal at both ends.

### Declaration & Instantiation

```java
Deque<Integer> deque = new ArrayDeque<>();
```

### Common Methods

| Method        | Description       | Time Complexity | Example             |
| ------------- | ----------------- | --------------- | ------------------- |
| addFirst(E e) | Add to front      | O(1)            | deque.addFirst(1)   |
| addLast(E e)  | Add to end        | O(1)            | deque.addLast(2)    |
| removeFirst() | Remove from front | O(1)            | deque.removeFirst() |
| removeLast()  | Remove from end   | O(1)            | deque.removeLast()  |
| peekFirst()   | View front        | O(1)            | deque.peekFirst()   |
| peekLast()    | View end          | O(1)            | deque.peekLast()    |

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

| Method    | Description     | Stack Time | ArrayDeque Time | Example                           |
| --------- | --------------- | ---------- | --------------- | --------------------------------- |
| push(E e) | Add to top      | O(1)       | O(1)            | stack.push(1) / deque.push(1)     |
| pop()     | Remove from top | O(1)       | O(1)            | stack.pop() / deque.pop()         |
| peek()    | View top        | O(1)       | O(1)            | stack.peek() / deque.peek()       |
| isEmpty() | Check if empty  | O(1)       | O(1)            | stack.isEmpty() / deque.isEmpty() |

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

| Method                | Description         | HashMap Time | LinkedHashMap Time | TreeMap Time | Example              |
| --------------------- | ------------------- | ------------ | ------------------ | ------------ | -------------------- |
| put(K key, V value)   | Add or update value | O(1)         | O(1)               | O(log n)     | map.put("a", 1)      |
| get(Object key)       | Get value by key    | O(1)         | O(1)               | O(log n)     | map.get("a")         |
| remove(Object key)    | Remove by key       | O(1)         | O(1)               | O(log n)     | map.remove("a")      |
| containsKey(Object k) | Check if key exists | O(1)         | O(1)               | O(log n)     | map.containsKey("a") |
| keySet()              | Get all keys        | O(n)         | O(n)               | O(n)         | map.keySet()         |
| values()              | Get all values      | O(n)         | O(n)               | O(n)         | map.values()         |

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
// Min-heap (default)
PriorityQueue<Integer> minHeap = new PriorityQueue<>();
// Max-heap
PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());
```

### Common Methods

| Method     | Description    | Time Complexity | Example     |
| ---------- | -------------- | --------------- | ----------- |
| offer(E e) | Add element    | O(log n)        | pq.offer(5) |
| poll()     | Remove min/max | O(log n)        | pq.poll()   |
| peek()     | View min/max   | O(1)            | pq.peek()   |

### Example

```java
PriorityQueue<Integer> pq = new PriorityQueue<>();
pq.offer(5);
pq.offer(1);
System.out.println(pq.poll()); // 1
```

**Note:**

- By default, it is a min-heap. Use a custom comparator for max-heap.

## 8. Utilities & Useful Functions

### Arrays Class

| Method                        | Description                            | Time Complexity | Example                     |
| ----------------------------- | -------------------------------------- | --------------- | --------------------------- |
| Arrays.sort(arr)              | Sorts the array in ascending order     | O(n log n)      | Arrays.sort(arr)            |
| Arrays.sort(arr, cmp)         | Sorts array with custom comparator     | O(n log n)      | Arrays.sort(arr, cmp)       |
| Arrays.toString(arr)          | Returns string representation of array | O(n)            | Arrays.toString(arr)        |
| Arrays.equals(arr1, arr2)     | Checks if two arrays are equal         | O(n)            | Arrays.equals(a, b)         |
| Arrays.fill(arr, val)         | Fills array with given value           | O(n)            | Arrays.fill(arr, 5)         |
| Arrays.binarySearch(arr, key) | Binary search (sorted array required)  | O(log n)        | Arrays.binarySearch(arr, 5) |

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

| Method                              | Description                          | Time Complexity | Example                           |
| ----------------------------------- | ------------------------------------ | --------------- | --------------------------------- |
| Collections.sort(list)              | Sorts list in ascending order        | O(n log n)      | Collections.sort(list)            |
| Collections.sort(list, cmp)         | Sorts list with custom comparator    | O(n log n)      | Collections.sort(list, cmp)       |
| Collections.reverse(list)           | Reverses the list                    | O(n)            | Collections.reverse(list)         |
| Collections.shuffle(list)           | Randomly shuffles the list           | O(n)            | Collections.shuffle(list)         |
| Collections.binarySearch(list, key) | Binary search (sorted list required) | O(log n)        | Collections.binarySearch(list, 2) |
| Collections.max(list)               | Returns max element                  | O(n)            | Collections.max(list)             |
| Collections.min(list)               | Returns min element                  | O(n)            | Collections.min(list)             |
| Collections.frequency(list, obj)    | Counts occurrences of obj in list    | O(n)            | Collections.frequency(list, 2)    |

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

## 9. Comparator & Comparable

### Comparable (Natural Ordering)

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

### Comparator (Custom Ordering)

Pass a Comparator to sort or data structures.

```java
// Sort by descending age
Collections.sort(people, (a, b) -> b.age - a.age);
// For PriorityQueue
PriorityQueue<Person> pq = new PriorityQueue<>((a, b) -> a.age - b.age); // min-heap by age
```

**Note:**

- Use `Comparator.comparing(Person::getAge)` for more readable code in Java 8+.
