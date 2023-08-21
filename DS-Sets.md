# SET 1
### [ ] Q1: Find the first non-repeating character in a string by doing only one traversal of it
Input: string is ABCDBAGHC
Output: The first non-repeating character in the string is D
ANS:
```
import java.util.HashMap;
import java.util.Map;
 
// A Pair class
class Pair<U, V>
{
    public U first;     // first field of a pair
    public V second;    // second field of a pair
 
    // Constructs a new Pair with specified values
    private Pair(U first, V second)
    {
        this.first = first;
        this.second = second;
    }
 
    // Factory method for creating a Typed Pair immutable instance
    public static <U, V> Pair <U, V> of(U a, V b)
    {
        // calls private constructor
        return new Pair<>(a, b);
    }
}
 
class Main
{
    // Function to find the first non-repeating character in
    // the string by doing only a single traversal of it
    public static int findNonRepeatingChar(String str)
    {
        // base case
        if (str == null || str.length() == 0) {
            return -1;
        }
 
        // map to store character count and the index of its
        // last occurrence in the string
        Map<Character, Pair<Integer, Integer>> map = new HashMap<>();
 
        for (int i = 0; i < str.length(); i++)
        {
            map.putIfAbsent(str.charAt(i), Pair.of(0, 0));
            map.get(str.charAt(i)).first++;
            map.get(str.charAt(i)).second = i;
        }
 
        // stores index of the first non-repeating character
        int min_index = -1;
 
        // traverse the map and find a character with count 1 and
        // a minimum index of the string
        for (var value: map.values())
        {
            int count = value.first;
            int firstIndex = value.second;
 
            if (count == 1 && (min_index == -1 || firstIndex < min_index)) {
                min_index = firstIndex;
            }
        }
 
        return min_index;
    }
 
    public static void main(String[] args)
    {
        String str = "ABCDBAGHC";
 
        int index = findNonRepeatingChar(str);
        if (index != -1)
        {
            System.out.println("The first non-repeating character in the string is "
                    + str.charAt(index));
        } else {
            System.out.println("The string has no non-repeating character");
        }
    }
}
```
[ ] Q2: Trees: Given a binary tree, check if it is a binary search tree using inorder traversal.

```
/ A class to store a BST node
class Node
{
    int data;
    Node left = null, right = null;
 
    Node(int data) {
        this.data = data;
    }
}
 
class Main
{
    // Recursive function to insert a key into a BST
    public static Node insert(Node root, int key)
    {
        // if the root is null, create a new node and return it
        if (root == null) {
            return new Node(key);
        }
 
        // if the given key is less than the root node, recur for the left subtree
        if (key < root.data) {
            root.left = insert(root.left, key);
        }
 
        // if the given key is more than the root node, recur for the right subtree
        else {
            root.right = insert(root.right, key);
        }
 
        return root;
    }
 
    // Function to perform inorder traversal on the given binary tree and
    // check if it is a BST or not. Here, `prev` is the previously processed node
    public static boolean isBST(Node root, Node prev)
    {
        // base case: empty tree is a BST
        if (root == null) {
            return true;
        }
 
        // check if the left subtree is BST or not
        boolean left = isBST(root.left, prev);
 
        // value of the current node should be more than that of the previous node
        if (root.data <= prev.data) {
            return false;
        }
 
        // update previous node data and check if the right subtree is BST or not
        prev.data = root.data;
 
        return left && isBST(root.right, prev);
    }
 
    // Function to determine whether a given binary tree is a BST
    public static void isBST(Node node)
    {
        // pointer to store previously processed node in the inorder traversal
        Node prev = new Node(Integer.MIN_VALUE);
 
        // check if nodes are processed in sorted order
        if (isBST(node, prev)) {
            System.out.println("The tree is a BST.");
        }
        else {
            System.out.println("The tree is not a BST!");
        }
    }
 
    private static void swap(Node root)
    {
        Node left = root.left;
        root.left = root.right;
        root.right = left;
    }
 
    public static void main(String[] args)
    {
        int[] keys = { 15, 10, 20, 8, 12, 16, 25 };
 
        Node root = null;
        for (int key: keys) {
            root = insert(root, key);
        }
 
        // swap nodes
        swap(root);
        isBST(root);
    }
}
```

# SET - 2
### [ ] Q3: Stack: Implement a stack using the array
```
class Stack
{
    private int arr[];
    private int top;
    private int capacity;
 
    // Constructor to initialize the stack
    Stack(int size)
    {
        arr = new int[size];
        capacity = size;
        top = -1;
    }
 
    // Utility function to add an element `x` to the stack
    public void push(int x)
    {
        if (isFull())
        {
            System.out.println("Overflow\nProgram Terminated\n");
            System.exit(-1);
        }
 
        System.out.println("Inserting " + x);
        arr[++top] = x;
    }
 
    // Utility function to pop a top element from the stack
    public int pop()
    {
        // check for stack underflow
        if (isEmpty())
        {
            System.out.println("Underflow\nProgram Terminated");
            System.exit(-1);
        }
 
        System.out.println("Removing " + peek());
 
        // decrease stack size by 1 and (optionally) return the popped element
        return arr[top--];
    }
 
    // Utility function to return the top element of the stack
    public int peek()
    {
        if (!isEmpty()) {
            return arr[top];
        }
        else {
            System.exit(-1);
        }
 
        return -1;
    }
 
    // Utility function to return the size of the stack
    public int size() {
        return top + 1;
    }
 
    // Utility function to check if the stack is empty or not
    public boolean isEmpty() {
        return top == -1;               // or return size() == 0;
    }
 
    // Utility function to check if the stack is full or not
    public boolean isFull() {
        return top == capacity - 1;     // or return size() == capacity;
    }
}
 
class Main
{
    public static void main (String[] args)
    {
        Stack stack = new Stack(3);
 
        stack.push(1);      // inserting 1 in the stack
        stack.push(2);      // inserting 2 in the stack
 
        stack.pop();        // removing the top element (2)
        stack.pop();        // removing the top element (1)
 
        stack.push(3);      // inserting 3 in the stack
 
        System.out.println("The top element is " + stack.peek());
        System.out.println("The stack size is " + stack.size());
 
        stack.pop();        // removing the top element (3)
 
        // check if the stack is empty
        if (stack.isEmpty()) {
            System.out.println("The stack is empty");
        }
        else {
            System.out.println("The stack is not empty");
        }
    }
}
```
### [ ] Q4: String: Evaluate the given expression
Given an expression containing numeric operands with addition and subtraction operators, evaluate it. Assume that the expression is valid and may contain sub-expressions enclosed in opening and closing braces.

Input: s = -15-2+1
Output: -16
 
Input: s = -10+(5+(12+8)-2)+1
Output: 14

```
import java.util.Stack;
 
class Main
{
    public static int eval(String exp)
    {
        int result = 0;
 
        // stores the last number
        int n = 0;
 
        // sign is 1 for positive and -1 for negative
        int sign = 1;
 
        // take a stack to store the sign
        Stack<Integer> stack = new Stack<>();
        stack.push(sign);
 
        // do for each character
        for (char c: exp.toCharArray())
        {
            // if the current character is a digit, construct the full number
            if (Character.isDigit(c)) {
                n = n * 10 + (c - '0');
            }
            // if the current character is a plus operator
            else if (c == '+')
            {
                // include the number before it in the result
                result += sign * n;
 
                // reset the number
                n = 0;
 
                // '+' would not affect the sign within the parentheses
                sign = stack.peek();
            }
            // if the current character is a minus operator
            else if (c == '-')
            {
                // include the number before it in the result
                result += sign * n;
 
                // reset the number
                n = 0;
 
                // '-' would negate the sign within the parentheses
                sign = stack.peek() * -1;
            }
            // if the current character is an opening brace, push the sign to the stack
            else if (c == '(') {
                stack.push(sign);
            }
            // if the current character is a closing brace, pop the sign from the stack
            else if (c == ')') {
                stack.pop();
            }
        }
 
        // add the last number and return the result
        result += sign * n;
        return result;
    }
 
    public static void main(String[] args)
    {
        String exp = "-10+(5+(12+8)-2)+1";
        System.out.println(eval(exp));
    }
}
```
# SET - 3
### [ ] Q5: Find the first k non-repeating characters in a string in a single traversal.
Given a string, find the first k non-repeating characters in it by doing only a single traversal of it.

For example, if the string is ABCDBAGHCHFAC and k = 3, the output would be 'D', 'G', 'F'.
```
import java.util.HashMap;
import java.util.Map;
import java.util.PriorityQueue;
 
class Pair
{
    private int count;
    private int index;
 
    Pair(int count, int index)
    {
        this.count = count;
        this.index = index;
    }
 
    Pair() {}
 
    public int getCount() {
        return count;
    }
 
    public int getIndex() {
        return index;
    }
 
    public void setCount(int count) {
        this.count = count;
    }
 
    public void setIndex(int index) {
        this.index = index;
    }
}
 
class Main
{
    // Function to find first `k` non-repeating character in
    // the string by doing only a single traversal
    public static void findFirstKNonRepeating(String str, int k)
    {
        // map to store character count and the index of its
        // last occurrence in the string
        Map<Character, Pair> map = new HashMap<>();
 
        for (int i = 0; i < str.length(); i++)
        {
            Pair pair = map.getOrDefault(str.charAt(i), new Pair());
            pair.setCount(pair.getCount() + 1);
            pair.setIndex(i);
 
            map.put(str.charAt(i), pair);
        }
 
        // create an empty min-heap
        PriorityQueue<Integer> pq = new PriorityQueue<>();
 
        // traverse the map and push the index of all characters
        // having the count of 1 into the min-heap
        for (var value: map.values())
        {
            int count = value.getCount();
            int index = value.getIndex();
 
            if (count == 1) {
                pq.add(index);
            }
        }
 
        // pop the top `k` keys from the min-heap
        while (k-- > 0 && !pq.isEmpty())
        {
            // extract the minimum node from the min-heap
            System.out.print(str.charAt(pq.poll()) + " ");
        }
    }
 
    public static void main (String[] args)
    {
        String str = "ABCDBAGHCHFAC";
        int k = 3;
 
        findFirstKNonRepeating(str, k);
    }
}
```
### [ ] Q6: Check if an expression is balanced or not
Given a string containing opening and closing braces, check if it represents a balanced expression or not. {[{}{}]}[()], {{}{}}, []{}() are balanced expressions.

{()}[), {(}) are not balanced.
```
import java.util.Stack;
 
class Main
{
    // Function to check if the given expression is balanced or not
    public static boolean isBalanced(String exp)
    {
        // base case: length of the expression must be even
        if (exp == null || exp.length() % 2 == 1) {
            return false;
        }
 
        // take an empty stack of characters
        Stack<Character> stack = new Stack<>();
 
        // traverse the input expression
        for (char c: exp.toCharArray())
        {
            // if the current character in the expression is an opening brace,
            // push it into the stack
            if (c == '(' || c == '{' || c == '[') {
                stack.push(c);
            }
 
            // if the current character in the expression is a closing brace
            if (c == ')' || c == '}' || c == ']')
            {
                // return false if a mismatch is found (i.e., if the stack is empty,
                // the expression cannot be balanced since the total number of opening
                // braces is less than the total number of closing braces)
                if (stack.empty()) {
                    return false;
                }
 
                // pop character from the stack
                Character top = stack.pop();
 
                // if the popped character is not an opening brace or does not pair
                // with the current character of the expression
                if ((top == '(' && c != ')') || (top == '{' && c != '}')
                        || (top == '[' && c != ']')) {
                    return false;
                }
            }
        }
 
        // the expression is balanced only when the stack is empty at this point
        return stack.empty();
    }
 
    public static void main(String[] args)
    {
        String exp = "{()}[{}]";
 
        if (isBalanced(exp)) {
            System.out.println("The expression is balanced");
        }
        else {
            System.out.println("The expression is not balanced");
        }
    }
}
```
