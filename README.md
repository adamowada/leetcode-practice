## Leetcode Problems

### [Defanging an IP Address](https://leetcode.com/problems/defanging-an-ip-address/) - Completed on 1/14/20

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
    
    var newaddr = ""; // start with an empty string
    newaddr += address[0];  // add the first item of address array to string
    for (i = 1; i < address.length; i++) { // starting with 2nd item of array, add each item with [.] before it 
           newaddr += "[.]" + address[i];
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

- Array.length returns a number. this is useful in for loops

- Using += to concatenate strings

#### What Knowledge Would Have Made This Problem Easier

- If the final return is a string sometimes it's easier to string methods rather than fidle around with arrays

- The proper way to write for loops

- Sometimes jank is ok?
