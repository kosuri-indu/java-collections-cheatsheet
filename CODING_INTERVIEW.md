# Java Coding Interview Patterns & Tips

This guide covers common patterns, tips, and best practices for Java coding interviews, especially when working with collections and data structures.

## 1. Common Coding Patterns

### 1.1. Sliding Window

Efficiently process subarrays or substrings of a fixed or variable size.

```java
int left = 0;
for (int right = 0; right < arr.length; right++) {
		// Expand window
		while (/* window too big or invalid */) {
				left++;
		}
		// Process window [left, right]
}
```

### 1.2. Two Pointers

Used for searching pairs in a sorted array or removing duplicates.

```java
int i = 0, j = arr.length - 1;
while (i < j) {
		int sum = arr[i] + arr[j];
		if (sum == target) break;
		else if (sum < target) i++;
		else j--;
}
```

### 1.3. Fast & Slow Pointers (Cycle Detection)

```java
ListNode slow = head, fast = head;
while (fast != null && fast.next != null) {
		slow = slow.next;
		fast = fast.next.next;
		if (slow == fast) return true;
}
```

### 1.4. HashMap for Counting/Frequency

```java
Map<Character, Integer> freq = new HashMap<>();
for (char c : s.toCharArray()) {
		freq.put(c, freq.getOrDefault(c, 0) + 1);
}
```

### 1.5. Stack for Parentheses/Expression Problems

```java
Stack<Character> stack = new Stack<>();
for (char c : s.toCharArray()) {
		if (c == '(') stack.push(c);
		else if (c == ')' && !stack.isEmpty()) stack.pop();
		else return false;
}
return stack.isEmpty();
```

### 1.6. BFS/DFS with Queue/Stack

```java
// BFS
Queue<TreeNode> q = new LinkedList<>();
q.offer(root);
while (!q.isEmpty()) {
		TreeNode node = q.poll();
		// process node
		if (node.left != null) q.offer(node.left);
		if (node.right != null) q.offer(node.right);
}

// DFS
Stack<TreeNode> st = new Stack<>();
st.push(root);
while (!st.isEmpty()) {
		TreeNode node = st.pop();
		// process node
		if (node.right != null) st.push(node.right);
		if (node.left != null) st.push(node.left);
}
```

## 2. General Interview Tips

- Always clarify requirements and edge cases with the interviewer.
- Use meaningful variable names and write clean, readable code.
- Start with a brute-force solution, then optimize.
- Use Java interfaces (`List`, `Map`, `Set`) for variable declarations.
- Know the time and space complexity of your approach.
- Test your code with sample and edge cases.
- Communicate your thought process clearly.

## 3. Useful Java Snippets

- **Convert List to Array:**
  ```java
  List<Integer> list = ...;
  Integer[] arr = list.toArray(new Integer[0]);
  ```
- **Convert Array to List:**
  ```java
  int[] arr = ...;
  List<Integer> list = Arrays.stream(arr).boxed().collect(Collectors.toList());
  ```
- **Sort with Comparator:**
  ```java
  Collections.sort(list, (a, b) -> b - a); // descending
  ```
- **PriorityQueue as Max Heap:**
  ```java
  PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());
  ```
- **StringBuilder for Efficient String Concatenation:**
  ```java
  StringBuilder sb = new StringBuilder();
  sb.append("a");
  sb.append("b");
  String result = sb.toString();
  ```

## 4. Recommended Practice

- Practice LeetCode, HackerRank, or CodeSignal problems.
- Review common data structures and algorithms.
- Write code on paper or a whiteboard to simulate interview conditions.
- Time yourself to get used to coding under pressure.

Good luck with your interviews!
