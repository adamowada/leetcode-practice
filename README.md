## LeetCode Problems

### 1. [Defanging an IP Address](https://leetcode.com/problems/defanging-an-ip-address/) - Easy - Completed on 1/14/20

#### Description

Given a valid (IPv4) IP address, return a defanged version of that IP address.
A defanged IP address replaces every period "." with "[.]".

```
Example 1:

Input: address = "1.1.1.1"
Output: "1[.]1[.]1[.]1"

Example 2:

Input: address = "255.100.50.0"
Output: "255[.]100[.]50[.]0"
```

#### Constraints

The given address is a valid IPv4 address.

#### My Solution 

```
/**
 * @param {string} address
 * @return {string}
 */

var defangIPaddr = function(address) {
    address = address.split(".", ); // input address is now an array filled with 4 items and no periods
    
// this is a super janky workaround but  ¯\_(ツ)_/¯
    
    var newaddr = ""; 	// start with an empty string
    newaddr += address[0];  	// add the first item of address array to string
    for (i = 1; i < address.length; i++) { 	// starting with 2nd item of array, 
           newaddr += "[.]" + address[i]; 	// add each item with [.] before it
    }
    
    return newaddr; // return filled string with properly defanged ip address
};
```

#### My Original Plan

1. Break up the string into an array
2. Remove periods
3. Add [.] between numbers 
4. Rurn array back into string
5. Return string

#### What I Ended Up Doing

1. Break up string into array and remove periods with split method
2. Create an empty string
3. Concat first item of array (first set of ip numbers) with empty string
4. Write a for loop and from second item of the array through the last concat [.] + item to string
5. Return string

#### How Long Did It Take Me

1hr 35min

#### What I learned

- Difference between return and console.log()
- REMEMBER TO ADD SEMICOLONS
- How to turn string into an array with split method
	string.split(separator, limit)
	and if you leave it as string.split() the array will only have one item being "string"
- How to insert/remove items in array using splice method
	array.splice(index, howmany, item1, ....., itemX)
	but not really because I don't understand how howmany can equal 0 or its proper use because I ended up using a string 
- How to write a for loop
- Declare an empty string before adding to it in for loop
- array.length returns a number. This is useful in for loops
- Using += to concatenate strings

#### What Knowledge Would Have Made This Problem Easier

- If the final return is a string sometimes it's easier to use string methods rather than fidle around with arrays
- The proper way to write for loops
- Sometimes jank is ok?

### 2. [Find Numbers With Even Number of Digits](https://leetcode.com/problems/find-numbers-with-even-number-of-digits/submissions/) - Easy - Completed on 1/14/20

#### Description

Given an array nums of integers, return how many of them contain an even number of digits.

```
Example 1:

Input: nums = [12,345,2,6,7896]
Output: 2
Explanation: 
12 contains 2 digits (even number of digits). 
345 contains 3 digits (odd number of digits). 
2 contains 1 digit (odd number of digits). 
6 contains 1 digit (odd number of digits). 
7896 contains 4 digits (even number of digits). 
Therefore only 12 and 7896 contain an even number of digits.
Example 2:

Input: nums = [555,901,482,1771]
Output: 1 
Explanation: 
Only 1771 contains an even number of digits.
```

#### Constraints

Constraints:

1 <= nums.length <= 500
1 <= nums[i] <= 10^5

#### My Solution 

```
/**
 * @param {number[]} nums
 * @return {number}
 */

var findNumbers = function(nums) {
    var evens = 0;		\\ start with empty string
    for (i = 0; i < nums.length; i++ ) {	\\ for each item in nums array
        if (nums[i].toString().length % 2 == 0) {	\\ check if number of digits is evenly divisible by 2 
            evens += 1;
        }
    }
    return evens;
};
```

#### My Original Plan

1. Check length of each number in a for loop
2. If length mod 2 = 0 then count it
3. Return number of evens

#### What I Ended Up Doing

1. Turn each number in nums array into string, then check length of that string
2. If length mod 2 = 0 then count it
3. Return number of evens

#### How Long Did It Take Me

17min

#### What I learned

- How to use % mod 
- That you can't use .length() on a number
- How to convert number into string with .toString()
- That if you misplace "return evens;" in your for loop bracket bad things happen
- You can stack methods

#### What Knowledge Would Have Made This Problem Easier

- Use better organization of code to avoid errors
- You have to convert a number into a string to get its length

### 3. [Two Sum](https://leetcode.com/problems/two-sum/submissions/) - Easy - Completed on 1/21/20

#### Description

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

```
Example:

Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

#### Constraints

Constraints:

None. 

#### My Solution 

```
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    for (i = 0; i < nums.length; i++) {
        for (j = 0; j < nums.length; j++) {
            if (i != j && nums[i] + nums[j] === target) {
                return [i, j];
                };
            };
        };
};
```

#### My Original Plan

1. Loop through each number in array
2. For each number, loop through rest of numbers and sum
3. If sum equals target, return array of those numbers

#### What I Ended Up Doing

It went according to plan.

#### How Long Did It Take Me

15min

#### What I learned

- This problem was pretty easy for me. The biggest thing I learned was how to use nested for loops.

#### What Knowledge Would Have Made This Problem Easier

- Having had experience with nested for loops, but again this was already pretty easy.

### 4. [Reverse Integer](https://leetcode.com/problems/reverse-integer/) - Easy - Completed on 1/22/20

#### Description

Given a 32-bit signed integer, reverse digits of an integer.

```
Example 1:

Input: 123
Output: 321
Example 2:

Input: -123
Output: -321
Example 3:

Input: 120
Output: 21
```

#### Constraints

Constraints:

Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−231,  231 − 1]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

#### My Solution 

```
/**
 * @param {number} x
 * @return {number}
 */
var reverse = function(x) {
    var answer = '';
    var x = x.toString();
    if (x.charAt(-1) === '0') {
        x = x.substr(0, x.length - 2);
        };
    if (x.charAt(0) === '-') {
        answer = answer + '-';
        x = x.substr(1, x.length - 1);
        };
    for (i = 0; i < x.length; i++) {
        answer = answer + x.charAt(x.length - i - 1);
        };    
    if (Math.abs(Number(answer)) > 2147483647) {
        return 0;
        };
    return(Number(answer));
};
```

#### My Original Plan

1. Remove 0s from end of number
2. Treat number as an array of numbers
3. Return loop from end of array to beginning (reversing the order of characters)

#### What I Ended Up Doing

1. Contemplating the meaninglessness of life, struggle, and pain
2. Re-read the instructions
3. Turn number into string
4. Remove 0s at the end 
5. Keep negative sign in front if there in a new string
6. Loop backwards through string with charAt() and move to new string
7. Add if statemenet if it overflows
8. Return finished string as a number

#### How Long Did It Take Me

1hr 30min

#### What I learned

- PATIENCE. And to breathe. And tenacity.
- The importance of really understanding the problem domain
- The importance of studying examples for patterns to understand edge cases
- In order to concat a string I need to reassign it
- Calling toString as toString() because toChar() was throwing errors
- Learning how to debug the toChar() method ^
- Using Math.abs() instead of just > to evaluate overflow
- How to use string methods on numbers, and vice versa, and using toChar() on strings like an array's index
- Move back to front in a for loop with .length() - i - 1 logic

#### What Knowledge Would Have Made This Problem Easier

- I still don't REALLY understand the difference between methods and functions, but understanding when you can just dot method or if you need dot method()
- Taking a few more minutes to read problem, study examples, and think about edge cases
- Firmer understanding of data types and their methods
- Syntax ^
- Knowing that I could start at end of for loop and decrement 

### 5. [Palindrome Number](https://leetcode.com/submissions/detail/296550434/) - Easy - Completed on 1/22/20

#### Description

Determine whether an integer is a palindrome. An integer is a palindrome when it reads the same backward as forward. Follow up:

Could you solve it without converting the integer to a string?

```
Example 1:

Input: 121
Output: true
Example 2:

Input: -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
Example 3:

Input: 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.
```

#### Constraints

Constraints:

None.

#### My Solution 

```
/**
 * @param {number} x
 * @return {boolean}
 */
var isPalindrome = function(x) {
    if (x < 0) {
        return false;
        };
    for (i = 0; i < (x.toString().length); i++) {
        if (x.toString().charAt(i) !== x.toString().charAt(x.toString().length -i -1)) {
            return false;
            };
        };
    return true;
};
```

#### My Original Plan

1. If < 0, return false
2. Combine .toString() with .charAt() to loop through number
3. Return false if characters don't strictly equal each other

#### What I Ended Up Doing

1. If < 0, return false
2. Loop through number with .toString().charAt(), compare first char to last char, second char to second to last char, etc, with .length - i - 1 logic
3. Return false if characters don't strictly equal each other
4. Success without turning number into string!

#### How Long Did It Take Me

40min

#### What I learned

- More practice reversing through strings (and numbers)
- A practical use of -i-1 logic to compare to i 
- Really understanding loop logic, my first attempt put return true in the if/else statement inside the for loop, but this caused the first matching chars to return true

#### What Knowledge Would Have Made This Problem Easier

- Loop logic
- A smarter way to loop, as this solution goes through the whole length when it only needs to go through half, ie wasted compute time. 

### 6. [Roman to Integer](https://leetcode.com/problems/roman-to-integer/) - Easy - Completed on 1/23/20

#### Description

Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.
```
Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
```
For example, two is written as II in Roman numeral, just two one's added together. Twelve is written as, XII, which is simply X + II. The number twenty seven is written as XXVII, which is XX + V + II.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used:

I can be placed before V (5) and X (10) to make 4 and 9. 
X can be placed before L (50) and C (100) to make 40 and 90. 
C can be placed before D (500) and M (1000) to make 400 and 900.
Given a roman numeral, convert it to an integer.

```
Example 1:

Input: "III"
Output: 3
Example 2:

Input: "IV"
Output: 4
Example 3:

Input: "IX"
Output: 9
Example 4:

Input: "LVIII"
Output: 58
Explanation: L = 50, V= 5, III = 3.
Example 5:

Input: "MCMXCIV"
Output: 1994
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.
```

#### Constraints

Constraints:

Input is guaranteed to be within the range from 1 to 3999.

#### My Solution 

```
/**
 * @param {string} s
 * @return {number}
 */
var romanToInt = function(s) {
    var array = [];
    var numberArray = [];
    var romanArray = [];
    var answer = 0;
    array = s.split("");
    for (i = 0; i < array.length; i++) {
        if (array[i] === 'I') {
            numberArray.push(1);
            }
        if (array[i] === 'V') {
            numberArray.push(5);
            }
        if (array[i] === 'X') {
            numberArray.push(10);
            }
        if (array[i] === 'L') {
            numberArray.push(50);
            }
        if (array[i] === 'C') {
            numberArray.push(100);
            }
        if (array[i] === 'D') {
            numberArray.push(500);
            }
        if (array[i] === 'M') {
            numberArray.push(1000);
            }
    }
    for (i = 0; i < numberArray.length-1; i++) {
        if (numberArray[i] >= numberArray[i+1]) {
            romanArray.push(numberArray[i]); // remember that newArray.push(i) != newArray.push(array[i]) and use the later
        } else if (numberArray[i] < numberArray[i+1]) {
            romanArray.push(-numberArray[i]);
            }
        }
    romanArray.push(numberArray[numberArray.length-1]);
    for (i = 0; i < romanArray.length; i++) {
        answer = answer + romanArray[i];
        }
    return answer;
};
```

#### My Original Plan

1. Assign I, IV, V, IX, X, XL, L, XC, C, CD, D, CM, M to their integer values
2. Loop through string looking for these characters or character pairs
3. Add up corresponding values

#### What I Ended Up Doing

1. Only assign I, V, X, L, C, D, M to integer values
2. Convert string of characters to array of integer values per rule 1
3. Realize that IV = 4 = -1 + 5
4. Loop through new array of numbers and if the number on the right is larger turn number negative
5. Return array sum

#### How Long Did It Take Me

40min

#### What I learned

- How to push a value from one array to another in a loop
- Creative problem solving, how to look at a problem from a new angle
- Roman numerals 

#### What Knowledge Would Have Made This Problem Easier

- Conceptually, I was running into issues trying to wrap my mind about how to deal with the rules of roman numnerals and in general overthinking thinks with a complicated if/else ruleset. If I had had the meta strategy of rethinking problems to component parts and easier solutions this would have been easier to figure out. 

### 7. [Find Winner on a Tic Tac Toe Game](https://https://leetcode.com/problems/find-winner-on-a-tic-tac-toe-game/) - Easy - Completed on 2/11/20

#### Description

Tic-tac-toe is played by two players A and B on a 3 x 3 grid.

Here are the rules of Tic-Tac-Toe:

Players take turns placing characters into empty squares (" ").
The first player A always places "X" characters, while the second player B always places "O" characters.
"X" and "O" characters are always placed into empty squares, never on filled ones.
The game ends when there are 3 of the same (non-empty) character filling any row, column, or diagonal.
The game also ends if all squares are non-empty.
No more moves can be played if the game is over.
Given an array moves where each element is another array of size 2 corresponding to the row and column of the grid where they mark their respective character in the order in which A and B play.

Return the winner of the game if it exists (A or B), in case the game ends in a draw return "Draw", if there are still movements to play return "Pending".

You can assume that moves is valid (It follows the rules of Tic-Tac-Toe), the grid is initially empty and A will play first.

```
Example 1:

Input: moves = [[0,0],[2,0],[1,1],[2,1],[2,2]]
Output: "A"
Explanation: "A" wins, he always plays first.
"X  "    "X  "    "X  "    "X  "    "X  "
"   " -> "   " -> " X " -> " X " -> " X "
"   "    "O  "    "O  "    "OO "    "OOX"

Example 2:

Input: moves = [[0,0],[1,1],[0,1],[0,2],[1,0],[2,0]]
Output: "B"
Explanation: "B" wins.
"X  "    "X  "    "XX "    "XXO"    "XXO"    "XXO"
"   " -> " O " -> " O " -> " O " -> "XO " -> "XO " 
"   "    "   "    "   "    "   "    "   "    "O  "

Example 3:

Input: moves = [[0,0],[1,1],[2,0],[1,0],[1,2],[2,1],[0,1],[0,2],[2,2]]
Output: "Draw"
Explanation: The game ends in a draw since there are no moves to make.
"XXO"
"OOX"
"XOX"

Example 4:

Input: moves = [[0,0],[1,1]]
Output: "Pending"
Explanation: The game has not finished yet.
"X  "
" O "
"   "
```

#### Constraints
```
1 <= moves.length <= 9
moves[i].length == 2
0 <= moves[i][j] <= 2
There are no repeated elements on moves.
moves follow the rules of tic tac toe.
```
#### My Solution 

```
/**
 * @param {number[][]} moves
 * @return {string}
 */
var tictactoe = function(moves) {
    var aMoves = [];
    var bMoves = [];
    var aRow = [];
    var aColumn = [];
    var bRow = [];
    var bColumn = [];
    for (let i = 0; i < moves.length; i++ ){
        if (i % 2 === 0){
            aMoves.push(moves[i]);
        } else {
            bMoves.push(moves[i]);
        }
    }

    function isMoveThere(move, playerMoves) {
        for (var i = 0; i < playerMoves.length; i++) {
            if (playerMoves[i][0] === move[0] && playerMoves[i][1] === move[1]){
                return true;
            }
        }
        return false;
    }

    if (isMoveThere([0,0], aMoves) === true && isMoveThere([1,1], aMoves) === true && isMoveThere([2,2], aMoves) === true) {
        return 'A';
    }
    if (isMoveThere([2,0], aMoves) === true && isMoveThere([1,1], aMoves) === true && isMoveThere([0,2], aMoves) === true) {
        return 'A';
    }
    for (let i = 0; i < aMoves.length; i++ ){
        aRow.push(aMoves[i][0]);
    }
    for (let i = 0; i < aMoves.length; i++ ){
        aColumn.push(aMoves[i][1]);
    }
    for (let i = 0; i < 3; i++){
        let cCount = 0;
        let rCount = 0;
        for (let j = 0; j < aRow.length; j++){
            if (aRow[j] === i) {
                rCount++;
            }
        }
        for (let j = 0; j < aColumn.length; j++){
            if (aColumn[j] === i) {
                cCount++;
            }
        }
        if (rCount === 3 || cCount === 3){
            return 'A';
        }
    }

    
    if (isMoveThere([0,0], bMoves) === true && isMoveThere([1,1], bMoves) === true && isMoveThere([2,2], bMoves) === true) {
        return 'B';
    }
    if (isMoveThere([2,0], bMoves) === true && isMoveThere([1,1], bMoves) === true && isMoveThere([0,2], bMoves) === true) {
        return 'B';
    }
    for (let i = 0; i < bMoves.length; i++ ){
        bRow.push(bMoves[i][0]);
    }
    for (let i = 0; i < bMoves.length; i++ ){
        bColumn.push(bMoves[i][1]);
    }
    for (let i = 0; i < 3; i++){
        let cCount = 0;
        let rCount = 0;
        for (let j = 0; j < bRow.length; j++){
            if (bRow[j] === i) {
                rCount++;
            }
        }
        for (let j = 0; j < bColumn.length; j++){
            if (bColumn[j] === i) {
                cCount++;
            }
        }
        if (rCount === 3 || cCount === 3){
            return 'B';
        }
    }    
    
    if (moves.length === 9){
        return "Draw";
    }
    return "Pending";    
};


//sort all moves to A moves
//sort all moves to B moves

//check if winner is A
//    check A moves for both diagonals
//    check if 3 of same row in A moves
//    check if 3 of same column in A moves
//check if winner is B
//    check B moves for both diagonals
//    check if 3 of same row in B moves
//    check if 3 of same column in B moves
//if no winner
//    if 9 moves return draw
//    else return pending
```

#### My Original Plan

See comments

#### What I Ended Up Doing

See comments. But also, struggling for ever to figure out JS object equality.

#### How Long Did It Take Me

4hrs? Split over a few days. 

#### What I learned

- That you can't use a for loop and === to check if array is in an array because an array is an object in JS and object equality checks if it points to the same object in memory, not whether the contents of the object (array) are the same.
- So about 2.5 hrs was spent with the logic done and solid but essentially debugging why 
```
[0,0] === [0,0] is false
```
- The rest of the time was planning my approach in the beginning and then working out how to check if a target move is in an array of moves.
- On the plus side I learned a lot about debugging in the console.

#### What Knowledge Would Have Made This Problem Easier

- I reaaaaaaly wish I had known about object equality before ripping my hair out thinking I was going crazy and getting syntax wrong haha

### 8. [Number of Steps to Reduce a Number to Zero](https://leetcode.com/problems/number-of-steps-to-reduce-a-number-to-zero/) - Easy - Completed on 2/17/20

#### Description

Given a non-negative integer num, return the number of steps to reduce it to zero. If the current number is even, you have to divide it by 2, otherwise, you have to subtract 1 from it.

```
Example 1:

Input: num = 14
Output: 6
Explanation: 
Step 1) 14 is even; divide by 2 and obtain 7. 
Step 2) 7 is odd; subtract 1 and obtain 6.
Step 3) 6 is even; divide by 2 and obtain 3. 
Step 4) 3 is odd; subtract 1 and obtain 2. 
Step 5) 2 is even; divide by 2 and obtain 1. 
Step 6) 1 is odd; subtract 1 and obtain 0.

Example 2:

Input: num = 8
Output: 4
Explanation: 
Step 1) 8 is even; divide by 2 and obtain 4. 
Step 2) 4 is even; divide by 2 and obtain 2. 
Step 3) 2 is even; divide by 2 and obtain 1. 
Step 4) 1 is odd; subtract 1 and obtain 0.

Example 3:

Input: num = 123
Output: 12
```

#### Constraints

Constraints:

0 <= num <= 10^6

#### My Solution 

```
/**
 * @param {number} num
 * @return {number}
 */
var numberOfSteps  = function(num) {
    var steps = 0;
    var updatedNum = num;
    while (updatedNum > 0) {
        if (updatedNum % 2 > 0) {
            updatedNum = updatedNum - 1;
            steps++;
        } else {
            updatedNum = updatedNum / 2;
            steps++;
        }
    }
    return steps;
};
```

#### My Original Plan

1. Write logic to divide by 2 or subtract 1
2. Implement counter to track steps
3. Return counter

#### What I Ended Up Doing

Basically went according to plan.

1. Wrote a while loop with if/else statements to determine whether to divide by 2 or subtract 1
2. After each operation the number updates and steps increment 
3. Once number reaches 0, while loop stops and returns total steps

#### How Long Did It Take Me

About 15min

#### What I learned

- Save the function's argument as a variable to operate on it and update it
- If/else statement nested in a while loop
- Pretty easy question

#### What Knowledge Would Have Made This Problem Easier

- Took me a few minutes to realize all I needed was a good while loop. I think that practice would have helped me spot it sooner, and fundamentally realizing that loops with a variable amount of steps are good candidates for while loops.

### 9. [Fizz Buzz](https://leetcode.com/problems/fizz-buzz/) - Easy - Completed on 2/17/20

#### Description

Write a program that outputs the string representation of numbers from 1 to n.

But for multiples of three it should output “Fizz” instead of the number and for the multiples of five output “Buzz”. For numbers which are multiples of both three and five output “FizzBuzz”.

```
Example:

n = 15,

Return:
[
    "1",
    "2",
    "Fizz",
    "4",
    "Buzz",
    "Fizz",
    "7",
    "8",
    "Fizz",
    "Buzz",
    "11",
    "Fizz",
    "13",
    "14",
    "FizzBuzz"
]
```

#### Constraints

None.

#### My Solution 

```
/**
 * @param {number} n
 * @return {string[]}
 */
var fizzBuzz = function(n) {
    var arr = [];
    for (var i = 1; i <= n; i++) {
        if (i % 3 > 0 && i % 5 > 0) {
            arr.push(i.toString());     // proper syntax is i.toString() NOT toString(i)
        }
        if (i % 3 === 0 && i % 5 > 0) {
            arr.push('Fizz');
        }    
        if (i % 3 > 0 && i % 5 === 0) {
            arr.push('Buzz');    
        }
        if (i % 3 === 0 && i % 5 === 0) {
            arr.push('FizzBuzz');    
        }
    }
    return arr;
};
```

#### My Original Plan

1. Use a for loop that pushes to array
2. If not divisible by 3 or 5, covert to string
3. If divisible by 3 and not 5, push 'Fizz'
4. If divisible by 5 and not 3, push 'Buzz'
5. If divisible by 3 and 5, push 'FizzBuzz'

#### What I Ended Up Doing

Ah, the classic fizzbuzz. Went according to plan. There is something to be said about the number of lines of code used vs the readibility of the code. I know I could have first checked divisibility by 15, then 5 or 3, then remaining 5 or 3; but I like how readible the intention of the code is in my solution.

#### How Long Did It Take Me

About 20min

#### What I learned

- Had a few issues with .toString() syntax, as I did it from memory without looking it up first
- I first tried arr.push(toString(i)) before realizing it should be arr.push(i.toString())

#### What Knowledge Would Have Made This Problem Easier

- Remember the syntax is number.toString()!

### 10. [Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/) - Easy - Completed on 2/29/20

#### Description

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

```
Example 1:

Input: ["flower","flow","flight"]
Output: "fl"

Example 2:

Input: ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```

#### Constraints

Note: All given inputs are in lowercase letters a-z.

#### My Solution 

```
/**
 * @param {string[]} strs
 * @return {string}
 */
var longestCommonPrefix = function(strs) {
    var answer = '';
    var longestLength = 0; 
        
    // save length of longest string to longestLength
    for ( var i = 0; i < strs.length; i++ ) {
        if ( strs[i].length > longestLength ) {
            var longestLength = strs[i].length; // in case of runtime error remember to check spelling lol
        }
    }
    
    // pushes letters that match until finds letter that doesn't match
    for ( var j = 0; j < longestLength; j++ ) {       // for each letter in the longest string
        var letters = [];                           // create array for jth letters
        for ( var k = 0; k < strs.length; k++ ) {     // for each string in strs
            letters.push( strs[k][j] );               // push jth letter of kth string to letters array
        }
        if ( letters.every( ( letter, l, array ) => letter === array[0] ) ) { // if every letter is the same as the first in letters array, returns true
            answer = answer.concat(letters[0]); // if returns true, concat letter to answer string
        } else {
            break;  // stops checking letters once loop finds a letter that doesn't all match
        }
    }
    
    return answer;
};
```

#### My Original Plan

Basically strs[0][0] strs[1][0] strs[2][0]

1. Get length of longest string in given array
2. Compare first letter of first word, to first letter of second word, to first letter of third word
3. Continue with each letter
4. return string of letters

#### What I Ended Up Doing

This question was complicated and required a few complex for loops, and careful planning. Basically realizing that the order of loops is for each letter in the longest string, check each string, and use a .every() to check if all letters equal the first (which means they are all the same). See comments in code. 

#### How Long Did It Take Me

1 hr

#### What I learned

- If at first you don't succeed, check for spelling mistakes. I misspelled longestLength on line 12, which meant I wasn't getting the longest length of any string. 
- How to really think through a nested loop problem
- How the .every() method works
- Basics of => functions

#### What Knowledge Would Have Made This Problem Easier

- .every() method
- Arrow functions
- Putting the empty var on line 18, which meant that the array cleared after each letter was checked 


```
```
https://leetcode.com/problems/same-tree/
```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isSameTree(self, p: TreeNode, q: TreeNode) -> bool:
        if p:
            q_p = [p]
        else:
            q_p = []
        if q:
            q_q = [q]
        else:
            q_q = []
        
        while q_p and q_q:
            temp_p = q_p.pop(0)
            temp_q = q_q.pop(0)
            if temp_p.val != temp_q.val:
                return False
            if temp_p.left and temp_q.left:
                q_p.append(temp_p.left)
                q_q.append(temp_q.left)
            if temp_p.right and temp_q.right:
                q_p.append(temp_p.right)
                q_q.append(temp_q.right)
            if temp_p.left and not temp_q.left or temp_q.left and not temp_p.left:
                return False
            if temp_p.right and not temp_q.right or temp_q.right and not temp_p.right:
                return False
        if len(q_p) > 0 or len(q_q) > 0:
            return False
        else:
            return True
```
