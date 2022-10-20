# Problem Solving Questions


1. Find an efficient algorithm to find the smallest distance (measured in number of words) between any two given words in a string. For example, given words "hello", and "world" and a text content of "dog cat hello cat dog dog hello cat world", return 1 because there's only one word "cat" in between the two words.

```
let word1 = "hi"
let word2 = "cat"
let text = "cat world hi"
//output = return 1 because there's only one word "world" in between the two words.

//let word1 = "hello"
//let word2 = "world"
//let text = "dog cat hello cat dog dog hello cat world"
//output = return 1 because there's only one word "cat" in between the two words.


let words = text.split(' ')
let firstIndex = 0
let lastIndex = 0

for(let i=0; i<words.length; i++) {
    if(words[i] == word1) {
        firstIndex = i+1
    } else if(words[i] == word2) {
        lastIndex = i+1
    }
}

console.log("smallest distance: ", Math.abs(lastIndex-firstIndex)-1)
```
