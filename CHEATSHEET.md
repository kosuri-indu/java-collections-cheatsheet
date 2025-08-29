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
Queue<Integer> queue = new LinkedList<>();
Queue<Integer> arrayDeque = new ArrayDeque<>();
```

### Common Methods

| Method     | Description    | Time Complexity |
| ---------- | -------------- | --------------- |
| offer(E e) | Add to queue   | O(1)            |
| poll()     | Remove head    | O(1)            |
| peek()     | View head      | O(1)            |
| isEmpty()  | Check if empty | O(1)            |

### Example

```java
Queue<Integer> q = new LinkedList<>();
q.offer(1);
q.offer(2);
System.out.println(q.poll()); // 1
```

**Note:**

- `offer` and `poll` are preferred over `add` and `remove` as they do not throw exceptions on failure.

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
| --------------------- | ------------------- | ------------ | ------------------ | ------------ |
| put(K key, V value)   | Add or update value | O(1)         | O(1)               | O(log n)     |
| get(Object key)       | Get value by key    | O(1)         | O(1)               | O(log n)     |
| remove(Object key)    | Remove by key       | O(1)         | O(1)               | O(log n)     |
| containsKey(Object k) | Check if key exists | O(1)         | O(1)               | O(log n)     |
| keySet()              | Get all keys        | O(n)         | O(n)               | O(n)         |
| values()              | Get all values      | O(n)         | O(n)               | O(n)         |

### Example

```java
Map<String, Integer> map = new HashMap<>();
map.put("a", 1);
map.put("b", 2);
System.out.println(map.get("a")); // 1
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
