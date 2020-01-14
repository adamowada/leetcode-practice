## LeetCode Problems

### 1. [Defanging an IP Address](https://leetcode.com/problems/defanging-an-ip-address/) - Completed on 1/14/20

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


### 2. [Find Numbers With Even Number of Digits](https://leetcode.com/problems/find-numbers-with-even-number-of-digits/submissions/) - Completed on 1/14/20

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
