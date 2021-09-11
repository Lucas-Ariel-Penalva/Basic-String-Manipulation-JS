# Essential String manipulation techniques

### 1) Creating a Dictionary with character counts

There are countless situations in which it's useful to know exactly which characters are present in a string and how many of them there are.

One of the most practical ways to do this involves creating a *dictionary/hashmap*, since they are easy to implement and good for performance. You can instantly access the values within a Javascript object (in *O(1)* constant time), unlike arrays, which often force you to traverse them fully before you can find what you are looking for. This is why using Javascript dictionaries is essential to solve complex problems without timing out.

#### Steps to create a dictionary with the count of each character in a String:

> * Create a dictionary variable and initialize it to a Javascript object.
> * Loop through the string and check if the current character is present in the dictionary:
>   * If the current character is undefined within the dictionary, set that character to 1.  
>   * If the current character is already defined within the dictionary, increase it by one.
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

...Text unfinished.
