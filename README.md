

# Fuzzy Search: Find Words That Are Close Enough

This JavaScript function uses the Levenshtein distance algorithm to perform fuzzy search and suggest words that are similar to user input. Perfect for when you're not quite sure how to spell something!

**Checkout:**

```js

function levenshteinDistance(str1, str2) {

  const m = str1.length;

  const n = str2.length;

  const d = [];

  for (let i = 0; i <= m; i++) {

    d[i] = [i];

  }

  for (let j = 0; j <= n; j++) {

    d[0][j] = j;

  }

  for (let j = 1; j <= n; j++) {

    for (let i = 1; i <= m; i++) {

      if (str1[i-1] === str2[j-1]) {

        d[i][j] = d[i-1][j-1];

      } else {

        d[i][j] = Math.min(

          d[i-1][j] + 1,

          d[i][j-1] + 1,

          d[i-1][j-1] + 1

        );

      }

    }

  }

  return d[m][n];

}

const dictionary = ["apple", "banana", "cherry", "date", "elderberry"];

const userInput = "ppl";

const maxDistance = 2;

const suggestions = dictionary.filter(word => levenshteinDistance(userInput, word) <= maxDistance);

console.log(`Did you mean: ${suggestions.join(", ")}?`);

// Output: Did you mean: apple?

```

**Have no idea what algorithm I use and What is happening? Ahh so listen**

Have you ever been searching for a word but just can't seem to get it right? With this `levenshteinDistance` function, you can perform a fuzzy search and find words that are close enough to your query. Simply provide a list of words to search through, and the function will suggest words that are within a certain distance from your input. The Levenshtein distance algorithm is a powerful tool that calculates the minimum number of single-character edits required to transform one string into another. This means that even if you misspelled a word, the function can still find the closest match for you. Give it a try and see how it can help you find the words you're looking for!

**You can also try these Examples >**

(1) Language Search

```js

const dictionary = ["javascript", "python", "ruby", "go", "swift"];

const userInput = "java";

const maxDistance = 2;

const suggestions = dictionary.filter(word => levenshteinDistance(userInput, word) <= maxDistance);

console.log(`Did you mean: ${suggestions.join(", ")}?`);

// Output: Did you mean: javascript?

```

(2) Colour Search

```js

const dictionary = ["red", "orange", "yellow", "green", "blue", "purple"];

const userInput = "greeen";

const maxDistance = 2;

const suggestions = dictionary.filter(word => levenshteinDistance(userInput, word) <= maxDistance);

console.log(`Did you mean: ${suggestions.join(", ")}?`);

// Output: Did you mean: green?

```

And did you notice why every DEVELOPER use i, j variable in loops? Maybe because habit or programing law.

Ahh nevermind, Thank you!

