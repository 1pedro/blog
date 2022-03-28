---
title: "TIL: How to convert a integer (32 bit) to binary using bitwise and bit-shift"
date: 2022-03-28T00:20:06-03:00
draft: false
tags: ["js", "algorithms"]
---

Today I was exercising some competitive programming problems using [Codility](https://codility.com).
The first problem named "Binary Gap" consists in a way to determine the longest zero occurrences in a binary string.
The problem gives us a number and we should convert that number to a binary string then find the biggest 
consecutive zero occurrences in that binary string.

This problem is classified as easy and I didn't take too much time to solve it. But trying 
to solve this problem lead me to a search about how was the "best" or "correct" way to convert
an integer into a binary string in Javascript.

Searching through stack overflow the first answer was great! I just need to do ```Number(32).toString(2)```
with 32 being the input number that the problem gives to me. And it's done. 
With some logic, the problem was solved and I received 100% of Correctness.

After solving the problem a couple of questions came to my mind:  
1. *Is there another way to convert that is more efficient or more performatic?*
2. *What if I have to make this same conversion but in another programming language?*

Again these questions lead me to another search. But now, about how many ways I can convert a number to a binary string.

##### Divsion by 2
The search gave to me two different ways. The first uses a loop that get the rest of the division by 2, store the value
in a stack then get the values from the stack concatenating one by one.
For learning purpose, I read the specification of the algorithm and make a version.
This algorithm looks like this:

```js
function divBy2(number){
    let binString = ''

    while (number >= 1) {
        binString += number % 2 === 0 ? '0':'1'
        number = Math.floor(number /2) 
    }

    return binString.split('').reverse().join('')
}
```

This is what I was looking in the first question, but again it's a Javascript way. The methods `Math.floor`,
`split`, `reverse` and `join` will make no sense if I try to put this code in another language. 
Even for a C-like language.

##### Bit-shift + Bitwise way
The second search result was a bitwise + bit-shift operation. It consists in looping the number 32 times (for 32 bits)
walking from the most significant bit to the least significant bit and writing to a string.
Again I read the specification and made my own version. It looks like this:

```js
function bitwiseIntToBinaryString(number) {
    let binString = ''

    for (let i = 31; i >= 0; i--) {
        const result = number >> i;
        binString += result & 1 ? '1' : '0'
    }

    return binString
}
```

With this, I can run this code in almost any C-like language and is way more performatic. 
The biggest con with this approach is that the number should fit the loop. Converting a 64 bit integer
with this approach will lead to bugs. Besides that this algorithm always returns a 32 bit string, which means
that even a number like 100 will lead us to **00000000000000000000000001100100** instead of **1100100**.

With this in mind, I came up with a decision to remove the leading zeros of the string using a regex.  
In another time I will try to fix the number fit as well. But by now the function without leading zeros is like this:

```diff
function bitwiseIntToBinaryString(number) {
    let binString = ''

    for (let i = 31; i >= 0; i--) {
        const result = number >> i;
        binString += result & 1 ? '1' : '0'
    }

---    return binString
+++    return binString.replace(/^0+/, '')
}
```

With this minor change we have now locked to javascript again but is easy to replace only this line to deal
with a regex in another programming language. No logic change is necessary.

##### Conclusion
A simple codility problem gave me the ability to learn and implement two algorithms that are much more
performatic and reusable than the language way.