Download Link: https://assignmentchef.com/product/solved-cst370-homework-4
<br>
<h1>About</h1>

For this 2-week homework assignment, you be implementing tries, huffman codes, and radix sorts.




<h1>Problems</h1>

<table width="312">

 <tbody>

  <tr>

   <td width="250">1   Tries</td>

   <td width="63">15 points</td>

  </tr>

  <tr>

   <td width="250">2    Huffman codes</td>

   <td width="63">20 points</td>

  </tr>

  <tr>

   <td width="250">3    Radix Sort</td>

   <td width="63">15 points</td>

  </tr>

 </tbody>

</table>

1

This page is intentionally left blank.

<ol>

 <li><strong> Tries </strong><strong>(15 points)</strong></li>

</ol>

<a href="https://www.hackerrank.com/contests/cst370-s19-hw4/challenges/hw4-tries"><strong>https://www.hackerrank.com/contests/cst370-s19-hw4/challenges/hw4-tries</strong></a>

For this problem you will implement a trie (prefix tree) and use it to autocomplete words. In C++, the trie node and class definitions might look like:

struct TrieNode { bool isLeaf; vector&lt;TrieNode*&gt; letters;

}; class Trie {

TrieNode* root;

};

You will need to implement the following operations:

lookup(string) which returns a boolean indicating whether given word was found. insert(string) which inserts the given word into the trie.

remove(string) which removes the given word from the trie (really removes it, not just changing the flag).

info() which prints out the number of nodes and number of words in the trie. alphabetical() which prints out the words in the trie in alphabetical order.

autocomplete(prefix, k) which prints alphabetically all possible words that can be formed by the given prefix and k additional characters.




For example, in C++, the function headers would be the following:

class Trie {

TrieNode *root;

public:

Trie() {

<em>// … </em>} bool lookup(string str) { <em>// … </em>} void insert(string str) { <em>// … </em>} void remove(string str) { <em>// … </em>} int info() { <em>// … </em>} void alphabetical() { <em>// … </em>} void autocomplete(string prefix, int k) { <em>// …</em>

}

};

<h2>Input</h2>

<ul>

 <li>The first line of the input will be an integer n indicating how many commands follow it.</li>

 <li>The next n lines will consist of one of 5 commands (”insert”, ”remove”, ”lookup”, ”info”, and ”autocomplete”).</li>

 <li>The commands ”insert”, ”remove”, and ”lookup” will be followed by a space, then a string representing the word to perform the command on.</li>

 <li>The commands ”info” and ”alphabetical” have nothing following it.</li>

 <li>The command ”autocomplete” will be followed by a space, then a string to perform the command on, then a space, then finally an integer representing the number of additional characters to consider. <em>The integer may be a special value of ”-1” which means consider all words without a length limitation.</em></li>

</ul>

At the end of the input there will be a blank line. Your program should initialize an empty trie and perform the commands given by the input, in sequence, on it.

<h2>Constraints</h2>

You can assume there will be no invalid input. You can also assume the trie will consist of only lowercase words consisting of characters a-z with no duplicate words.

<h2>Output</h2>

<ul>

 <li>For the ”insert” and ”remove” commands, print nothing.</li>

 <li>For the ”lookup” command, print the line ”0” if the string is not found and the line ”1” if it is found.</li>

 <li>For the ”info” command, print a line containing two space separated integers. The first integer is the number of nodes in the trie, the second is the number of words. For the ”alphabetical” command, print all the words contained in the trie in alphabetical order. One word per line.</li>

 <li>For the ”autocomplete” command, print the possible autocompleted words <strong>on a single space-separated line </strong>in alphabetical order (the line will end in a space).</li>

</ul>

See the sample output section and hackerrank for concrete examples

Sample Input 1                                                      Sample Output 1

<table width="622">

 <tbody>

  <tr>

   <td width="311">17 insert james insert jackie lookup ja insert ja lookup ja insert jay insert jane lookup jackie alphabetical info autocomplete ja 2 autocomplete ja -1 remove jackie lookup jackie lookup ja alphabetical info</td>

   <td width="311">011 ja jackie james jane jay13 5 ja jane jay ja jackie james jane jay01 ja james jane jay9 4</td>

  </tr>

 </tbody>

</table>




<h1>2.      Huffman codes (20 points)</h1>

<a href="https://www.hackerrank.com/contests/cst370-s19-hw4/challenges/hw4-huffman"><strong>https://www.hackerrank.com/contests/cst370-s19-hw4/challenges/hw4-huffman</strong></a>

For this problem you will implement a Huffman tree to encode and decode strings to and from variable-width encodings.

<h2>Input</h2>

<ul>

 <li>The input will consist of two lines.</li>

 <li>The first line will be the string to derive your codes from and encode. Build your Huffman tree from this string.</li>

 <li>The second line will consist of a test string of 0s and 1s to decode.</li>

</ul>

At the end of the input there will be a blank line. Your program should build a huffman tree encoding from the first line and use that tree to decode the second line.

In order to build a Huffman Tree, you will need a priority queue. You may use the following priority queues as starter code:

C++ https://repl.it/@dsyang/HuffmanQueue-Cpp

Java https://repl.it/@dsyang/HuffmanQueue-java

Python https://repl.it/@dsyang/HuffmanQueue-py

<h2>Constraints</h2>

The order in which you insert nodes into your priority queue and the implementation of the priority queue itself has an impact to the created huffman tree. To achieve the same encoding as the test cases, build your huffman tree as such:

<ul>

 <li>Use a MinHeap in the implementation of the priority queue. You can use one of the MinHeaps provided above or modify your heap from homework 1.</li>

 <li>When initially adding characters into your priority queue, insert the characters in alphabetical order. For example, if your frequency map is: b:2, c:1, x:1, a:4, [space]:3 then you would add them into the priority queue in this order: [space], a, b, c, x.</li>

</ul>

<h2>Output</h2>

<ul>

 <li>The output will consist of two lines.</li>

 <li>The first line will be the encoding of the first input string according to your tree.</li>

 <li>The second line will be the decoding of the second input string according to your tree.</li>

</ul>

See the sample output section and hackerrank for concrete examples

Sample Input 1

i love computer science

1100101110101100110111111011100011010101101100100111

Sample Output 1

<table width="620">

 <tbody>

  <tr>

   <td width="620">1100101110100001101111110110000001110001100100 (line wrap)11111110100101010110011001110110100111 i live in nice</td>

  </tr>

 </tbody>

</table>




<h1>3.      Radix Sort (15 points)</h1>

<a href="https://www.hackerrank.com/contests/cst370-s19-hw4/challenges/hw4-radix"><strong>https://www.hackerrank.com/contests/cst370-s19-hw4/challenges/hw4-radix</strong></a>

For this problem you will be provided an array of integers and asked to sort them using radix sort. You will be printing the partially sorted array after sorting by each digit.

<h2>Input</h2>

The input will consist of one line containing space integers. At the end of the input there will be a blank line.

<h2>Constraints</h2>

You can asssume the input is valid and falls within the constraints under which it is appropriate to use radix sort.

<h2>Output</h2>

The output will consist of k lines, where k is the number of calls to counting sort (i.e., the number of digits in the largest element in the input). Each line will contain a list of space integers in their partially sorted order after that call (the line will end with ” ”) See the sample output section and hackerrank for concrete examples

Sample Input 1

12

9 87 199 15 3 214 19 26 58 2 102 23

Sample Output 1

2 102 3 23 214 15 26 87 58 9 199 19 2 102 3 9 214 15 19 23 26 58 87 199

2 3 9 15 19 23 26 58 87 102 199 214




This page is intentionally left blank.