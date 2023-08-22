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
# SET - 4
### Q7: Construct the longest palindrome by shuffling or deleting characters from a string
Input:  ABBDAB
Output: The longest palindrome is BABAB (or BADAB or ABBBA or ABDBA)
 
Input:  ABCDD
Output: The longest palindrome is DAD (or DBD or DCD)

```
import java.util.HashMap;
import java.util.Map;
 
class Main
{
    // Construct the longest palindrome by shuffling or deleting
    // characters from a given string
    public static String longestPalindrome(String str)
    {
        // base case
        if (str == null || str.length() == 0) {
            return str;
        }
 
        // create a frequency map for characters of a given string
        Map<Character, Integer> freq = new HashMap<>();
        for (char ch: str.toCharArray()) {
            freq.put(ch, freq.getOrDefault(ch, 0) + 1);
        }
 
        String mid_char = "";                  // stores odd character
        StringBuilder left = new StringBuilder();   // stores left substring
 
        // iterate through the frequency map
        for (var entry: freq.entrySet())
        {
            char ch = entry.getKey();               // get current character
            int count = entry.getValue();           // get character frequency
 
            // if the current character's frequency is odd,
            // update mid to current char (and discard the old one)
            if (count % 2 == 1) {
                mid_char = String.valueOf(ch);
            }
 
            // append half of the characters to the left substring
            // (the other half goes to the right substring in reverse order)
            left.append(String.valueOf(ch).repeat(count / 2));
        }
 
        // the right substring will be the reverse of the left substring
        StringBuilder right = new StringBuilder(left).reverse();
 
        // return string formed by the left substring, mid-character (if any),
        // and the right substring
        return ("" + left + mid_char + right);
    }
 
    public static void main(String[] args)
    {
        String str = "ABBDAB";
        System.out.print("The longest palindrome is " + longestPalindrome(str));
    }
}

```
### Q8: Search a given key in BST – Iterative and Recursive Solution

```
// A class to store a BST node
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
 
    // Recursive function to search in a given BST
    public static void search(Node root, int key, Node parent)
    {
        // if the key is not present in the key
        if (root == null)
        {
            System.out.println("Key not found");
            return;
        }
 
        // if the key is found
        if (root.data == key)
        {
            if (parent == null) {
                System.out.println("The node with key " + key + " is root node");
            }
 
            else if (key < parent.data)
            {
                System.out.println("The given key is the left node of the node " +
                            "with key " + parent.data);
            }
            else {
                System.out.println("The given key is the right node of the node " +
                            "with key " + parent.data);
            }
 
            return;
        }
 
        // if the given key is less than the root node, recur for the left subtree;
        // otherwise, recur for the right subtree
 
        if (key < root.data) {
            search(root.left, key, root);
        }
        else {
            search(root.right, key, root);
        }
    }
 
    public static void main(String[] args)
    {
        int[] keys = { 15, 10, 20, 8, 12, 16, 25 };
 
        Node root = null;
        for (int key: keys) {
            root = insert(root, key);
        }
 
        search(root, 25, null);
    }
}
```

# SET 5
### Q9: Coin change-making problem
Given an unlimited supply of coins of given denominations, find the minimum number of coins required to get the desired change.
For example, consider S = { 1, 3, 5, 7 }.
f the desired change is 15, the minimum number of coins required is 3
 
(7 + 7 + 1) or (5 + 5 + 5) or (3 + 5 + 7)
 
 
If the desired change is 18, the minimum number of coins required is 4
 
(7 + 7 + 3 + 1) or (5 + 5 + 5 + 3) or (7 + 5 + 5 + 1)
```
class Main
{
    // Function to find the minimum number of coins required
    // to get a total of `target` from set `S`
    public static int findMinCoins(int[] S, int target)
    {
        // if the total is 0, no coins are needed
        if (target == 0) {
            return 0;
        }
 
        // return infinity if total becomes negative
        if (target < 0) {
            return Integer.MAX_VALUE;
        }
 
        // initialize the minimum number of coins needed to infinity
        int coins = Integer.MAX_VALUE;
 
        // do for each coin
        for (int c: S)
        {
            // recur to see if the total can be reached by including current coin `c`
            int result = findMinCoins(S, target - c);
 
            // update the minimum number of coins needed if choosing the current
            // coin resulted in a solution
            if (result != Integer.MAX_VALUE) {
                coins = Integer.min(coins, result + 1);
            }
        }
 
        // return the minimum number of coins needed
        return coins;
    }
 
    public static void main(String[] args)
    {
        // coins of given denominations
        int[] S = { 1, 3, 5, 7 };
 
        // total change required
        int target = 18;
 
        int coins = findMinCoins(S, target);
        if (coins != Integer.MAX_VALUE)
        {
            System.out.print("The minimum number of coins required to get the " +
                    "desired change is " + coins);
        }
    }
}
```
# SET - 6
### Q 11: Given an unsorted integer array nums, return the smallest missing positive integer.

```
// Java Program to find the smallest positive missing number
import java.util.*;
public class GFG {
 
    static int solution(int[] A)
    {
        int n = A.length;
        // Let this 1e6 be the maximum element provided in
        // the array;
        int N = 1000010;
 
        // To mark the occurrence of elements
        boolean[] present = new boolean[N];
 
        int maxele = Integer.MIN_VALUE;
 
        // Mark the occurrences
        for (int i = 0; i < n; i++) {
 
            // Only mark the required elements
            // All non-positive elements and the elements
            // greater n + 1 will never be the answer
            // For example, the array will be {1, 2, 3} in
            // the worst case and the result will be 4 which
            // is n + 1
            if (A[i] > 0 && A[i] <= n)
                present[A[i]] = true;
 
            // find the maximum element so that if all the
            // elements are in order can directly return the
            // next number
            maxele = Math.max(maxele, A[i]);
        }
 
        // Find the first element which didn't
        // appear in the original array
        for (int i = 1; i < N; i++)
            if (!present[i])
                return i;
 
        // If the original array was of the
        // type {1, 2, 3} in its sorted form
        return maxele + 1;
    }
 
    // Driver Code
    public static void main(String[] args)
    {
        int arr[] = { 0, 10, 2, -10, -20 };
        System.out.println(solution(arr));
    }
}
```
### Q12: Find duplicates in an array
// Generic method to check for duplicates in an array
private static <T> boolean checkForDuplicates(T... array)
{
    // create an empty set
    Set<T> set = new HashSet<T>();
 
    // do for every array element
    for (T e: array)
    {
        // return true if a duplicate is found
        if (set.contains(e)) {
            return true;
        }
 
        // insert the current element into a set
        if (e != null) {
            set.add(e);
        }
    }
 
    // no duplicate is found
    return false;
}

# SET 7
### Q13: Find total ways to reach the n’th stair from the bottom
Given a staircase, find the total number of ways to reach the n'th stair from the bottom of the stair when a person can only climb either 1 or 2 or 3 stairs at a time.

Total ways to reach the 3rd stair are 4
 
1 step + 1 step + 1 step
1 step + 2 steps
2 steps + 1 step
3 steps

 ```
class Main
{
    // Recursive function to find total ways to reach the n'th stair from the bottom
    // when a person is allowed to climb either 1 or 2 or 3 stairs at a time
    public static int totalWays(int n)
    {
        // base case
        if (n < 0) {
            return 0;
        }
 
        // base case: there is one way to cover it with no steps
        if (n == 0) {
            return 1;
        }
 
        // combine results of taking 1 step or 2 steps or 3 steps at a time
        return totalWays(n - 1) + totalWays(n - 2) + totalWays(n - 3);
    }
 
    public static void main(String[] args)
    {
        int n = 4;
        System.out.printf("Total ways to reach the %d'th stair are %d",
                            n, totalWays(n));
    }
}


```
### Q 14:  Find all  triplets with zero sum
nput: arr[] = {0, -1, 2, -3, 1}
Output: (0 -1 1), (2 -3 1)
Explanation: The triplets with zero sum are 0 + -1 + 1 = 0 and 2 + -3 + 1 = 0  
```
/ Java  program to find triplets in a given
// array whose sum is zero
import java.io.*;
import java.util.Arrays;
 
class GFG {
    // function to print triplets with 0 sum
    static void findTriplets(int arr[], int n)
    {
        boolean found = false;
 
        // sort array elements
        Arrays.sort(arr);
 
        for (int i = 0; i < n - 1; i++) {
            // initialize left and right
            int l = i + 1;
            int r = n - 1;
            int x = arr[i];
            while (l < r) {
                if (x + arr[l] + arr[r] == 0) {
                    // print elements if it's sum is zero
                    System.out.print(x + " ");
                    System.out.print(arr[l] + " ");
                    System.out.println(arr[r] + " ");
 
                    l++;
                    r--;
                    found = true;
                }
 
                // If sum of three elements is less
                // than zero then increment in left
                else if (x + arr[l] + arr[r] < 0)
                    l++;
 
                // if sum is greater than zero then
                // decrement in right side
                else
                    r--;
            }
        }
 
        if (found == false)
            System.out.println(" No Triplet Found");
    }
 
    // Driven source
    public static void main(String[] args)
    {
 
        int arr[] = { 0, -1, 2, -3, 1 };
        int n = arr.length;
        findTriplets(arr, n);
    }
    // This code is contributed by Tushil..
}
```
Given a set of coins with different combinations, find the minimum number of coins needed to make a specific amount
