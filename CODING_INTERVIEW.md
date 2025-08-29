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
