# Essential String manipulation techniques

### 1) Creating a Dictionary with character counts

There are countless situations in which it's useful to know exactly which characters are present in a string and how many of them there are.

One of the most practical ways to do this involves creating a *dictionary/hashmap*, since they are easy to implement and good for performance. You can instantly access the values within a Javascript object (in *O(1)* constant time), unlike arrays, which often force you to traverse them fully before you can find what you are looking for. This is why using Javascript dictionaries is essential to solve complex problems without timing out.

#### Steps to create a dictionary with the count of each character in a String:

> * Create a dictionary variable and initialize it to a Javascript object.
> * Loop through the string and check if the current character is present in the dictionary:
>   * If the current character is undefined within the dictionary, set "**dictionary[character]**" to **1**.  
>   * If the current character is defined within the dictionary, increase the current value of "**dictionary[character]**" by one.
> * Return the dictionary.

#### Here's an example of how to do that in Javascript.

```javascript
function createDictionary(str) {
  let dictionary = {};

  for (let i = 0; i < str.length; i++) {
    if (dictionary[str[i]] === undefined) {
      dictionary[str[i]] = 1;
    } else dictionary[str[i]]++;
  }

  return dictionary;
}
```

#### You can also write this in an even shorter way using a [*ternary operator*](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator) and a [*for...of*](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of) loop.

```javascript
function createDictionary(str) {
  let dict = {};
  for (const char of str) {
    !dict[char] ? dict[char] = 1 : dict[char]++;
  }
  return dict;
}
```

This simple tactic is *extremely useful* and part of the solution of many programming challenges. Anybody seeking to be confident and successful in coding interviews should learn this technique, specially if they are expecting questions about algorithms.


### 2) Generating an alphabet reliably

There are many common programming tasks that can be made easier by having a complete alphabet for reference. To name a few:

* Rotation ciphers, like [**Caesar Cipher**](https://en.wikipedia.org/wiki/Caesar_cipher) and all it's variations.
* Detection of [**Pangrams**](https://en.wikipedia.org/wiki/Pangram) and alphabetical substrings.
* Exclusively checking the keys of a dictionary that are letters.
* Solving problems in which each letter has a numeric value associated with it's position in the alphabet.

All of these are common beginner to intermediate coding challenges and possible interview questions, and working with an alphabet can be part of a viable solution. For example:

* For rotation ciphers, you have to change each character in the string by the character that is *X index positions* ahead or before in the alphabet.
* To detect pangrams or alphabetical substrings, you can do one loop over the alphabet to check if all it's letters are present in the string you are inspecting.
* For problems in which letters have some value related to their alphabet position, you usually just have to change each letter in the input string by the *(index + 1)* of that letter in the alphabet array/string you created.

#### And so on...

If you can generate a whole alphabet, you are on your way to solving those tasks.

One could simply do this:
```javascript
const alphabet = 'abcdefghijklmnopqrstuvwxyz';
```

The only problem is that manually typing the alphabet can be unreliable, as each of the 26 key strokes introduces the possibility of an error that is harder to detect than a typo on a Javascript keyword. If you write the alphabet wrong in any way, your function is likely to run without throwing any exceptions but your program will just produce the wrong output.

A more reliable solution involves using the fact that the alphabet begins at *97* on [ASCII code](https://www.ascii-code.com/), and knowing that you can access those letters using [String.fromCharCode()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/fromCharCode).

#### The code is:

```javascript
const alphabet = [...Array(26)].map((c,i) => String.fromCharCode(i + 97));
```

> * Use the [Array constructor](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Array) to create an array of size 26.
> * Spread it inside an array literal because you can't map over an array that you just created with the Array constructor.
> * Use **Map** to change each element in the array to equal the String generated by ***String.fromCharCode(index + 97)***.

Text unfinished...

