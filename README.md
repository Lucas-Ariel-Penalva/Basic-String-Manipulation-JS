# String manipulation techniques

&nbsp;

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

&nbsp;

### 2) Creating a character array

Since strings are immutable, many solutions require making a linear pass to read the input string while you build the output. However, on some occassions it might be easier to transform a string into an array to work with it. Once you transformed a string into an array, you use *map* over it or *filter* it as desired before you put it back together with *join*.

It's very common to use [*String.prototype.split()*](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split) to transform a string into an array:

```javascript
const str = "Hello world";

const charArray = str.split("");

const wordArray = str.split(" ");

// Using an empty string as the separator on Split, charArray = [ 'H', 'e', 'l', 'l', 'o', ' ', 'w', 'o', 'r', 'l', 'd' ] 
// Using a space as the separator on Split, wordArray = ['Hello', "world"]
```

#### ⚠ However, [**using split with an empty string as the separator can introduce bugs**](https://stackoverflow.com/questions/4547609/how-to-get-character-array-from-a-string/34717402#34717402) if the string has symbols, emojis or other special characters.

#### Instead of using *split*, you can **deestructure the string inside an array literal**, which is cleaner and less likely to produce bugs:

```javascript
const str = "Hello world";

const charArray = [...str];

// Destructuring the string, charArray =  [ 'H', 'e', 'l', 'l', 'o', ' ', 'w', 'o', 'r', 'l', 'd' ] 

```

You can see the usefulness of using the [*destructuring assignment*](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment) instead of *split* here:

```javascript
const str = "🦋💖🔆";

const destructureCharArr = [...str];

const splitCharArr = str.split("");

// destructureCharArr = [ '🦋', '💖', '🔆' ]
// splitCharArr will be ['�', '�', '�', '�', '�', '�'] or [ '\ud83e', '\udd8b', '\ud83d', '\udc96', '\ud83d', '\udd06' ]
```
&nbsp;
### 3) Generating an alphabet reliably

There are many programming tasks that can be made easier by referencing an alphabet. To name a few:

* Rotation ciphers, like [**Caesar Cipher**](https://en.wikipedia.org/wiki/Caesar_cipher) and all its variations.
* Detection of [**Pangrams**](https://en.wikipedia.org/wiki/Pangram) and alphabetical substrings.
* Exclusively checking the keys of a dictionary that are letters.
* Solving problems in which each letter has a numeric value associated with its position in the alphabet.

All of these are relatively common coding challenges and possible interview questions, and working with an alphabet can be part of a viable solution. For example:

* For rotation ciphers, you have to change each character in the string by the character that is *X index positions* ahead or before in the alphabet.
* To detect pangrams or alphabetical substrings, you can loop over the alphabet to check if all its letters are present in the string you are inspecting.
* For problems in which letters have a value related to their alphabet position, you have to change each letter in the input string by the *index* of that letter in the alphabet array/string you created.

#### And so on...

If you can generate a whole alphabet, you are on your way to solving those tasks.

One could simply do this:
```javascript
const alphabet = 'abcdefghijklmnopqrstuvwxyz';
```

The problem is that manually typing the alphabet can be unreliable, as each of the 26 keystrokes introduces the possibility of an error that is harder to detect than a typo on a Javascript keyword. If you write the alphabet wrong, your function is likely to run without throwing any exceptions, but your program will produce the wrong output.

A more reliable solution involves using the fact that the alphabet begins at *97* on [ASCII code](https://www.ascii-code.com/), and knowing that you can access those letters using [String.fromCharCode()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/fromCharCode).

#### The code is:

```javascript
const alphabet = [...Array(26)].map((c,i) => String.fromCharCode(i + 97));
```

> * Use the [Array constructor](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Array) to create an array of size 26.
> * Spread it inside an array literal because you can't map over an array that you just created with the Array constructor.
> * Use **Map** to change each element in the array to equal the String generated by ***String.fromCharCode(index + 97)***.

Text unfinished...
