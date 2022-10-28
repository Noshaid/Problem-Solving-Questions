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

2. You are given n numbers as well as n probabilities that sum up to 1. Write a function to generate one of the numbers with its corresponding probability.
For example, given the numbers [1, 2, 3, 4] and probabilities [0.1, 0.5, 0.2, 0.2], your function should return 1 10% of the time, 2 50% of the time, and 3 and 4 20% of the time.
You can generate random numbers between 0 and 1 uniformly.

```
let numbers = [1, 2, 3, 4]
let probabilities = [0.1, 0.4, 0.3, 0.2]
//output = your function should return 1 10% of the time, 2 50% of the time, and 3 and 4 20% of the time

let probabilityPercentages = []

for(let i=0; i<numbers.length; i++) {
    probabilityPercentages.push(probabilities[i]*100/1+"%")
}

console.log(numbers)
console.log(probabilities)
console.log(probabilityPercentages)
```

3. Given an arithmetic expression in Reverse Polish Notation, write a program to evaluate it. The expression is given as a list of numbers and operands.

```
//let input = [5, 3, '+']
//output = 8

let input = [15, 7, 1, 1, '+', '-', '/', 3, '*', 2, 1, 1, '+', '+', '-']
//output = 5

const DMAS = (stackArr, expression) => {
    if (stackArr.length <= 1) {
        return []
    }
    
    let num2 = stackArr.pop()
    let num1 = stackArr.pop()
    
    if (expression === '+') {
        stackArr.push(num1 + num2)
    } else if (expression === '-') {
        stackArr.push(num1 - num2)
    } else if (expression == '*') {
        stackArr.push(num1 * num2)
    } else if (expression == '/') {
        stackArr.push(num1 / num2)
    }
    
    return stackArr
}

const evaluateExpression = (input) => {
    if (input.length < 3 || input.includes('+','-', '*', '/') == false) {
        return "Input is not valid!"
    }
    
    let stackArr = []
    
    for(let i=0; i<input.length; i++) {
        if (input[i] === '+' || input[i] === '-' || input[i] === '*' || input[i] === '/') {
            stackArr = DMAS(stackArr, input[i])
        } else {
            stackArr.push(input[i])
        }
    } 
    
    if (stackArr.length > 1 || stackArr.length == 0) {
        return "Input is not valid!"
    } else {
        return stackArr[0]
    }
}

console.log(evaluateExpression(input))
```

4. Given a list of words, return the shortest unique prefix of each word.

```
//let input = ["dog", "cat", "apple", "apricot", "fish"]
//output = ["d", "c", "app", "apr", "f"] 

// let input = ["zebra", "dog", "duck", "dove"]
//output = [z, dog, du, dov]

//let input = ["geeksgeeks", "geeksquiz", "geeksforgeeks"]
//output = [geeksg, geeksq, geeksf]

// let input = ["dog", "apple", "apricot", "fish"]
//output = ["d", "app", "apr", "f"] 

let input = ["dog", "cat", "apple", "apricot", "fish", "do"]
// output = [ 'dog', 'c', 'app', 'apr', 'f', 'do' ]

const getShortestUniquePrefix = (input) => {
    let uniquePrefixArr = []
    for(let i=0; i<input.length; i++) {
        for(let j=0; j<input[i].length; j++) {
            let prefix = input[i].substring(0, j+1)
            let ok = checkUniquePrefix(prefix, i)
            if (ok === true || ok === false && j === input[i].length-1) {
                uniquePrefixArr.push(prefix) 
                break;
            }
        }
    }
    console.log(uniquePrefixArr)
}

const checkUniquePrefix = (prefix, index) => {
    var ok = true
    for(let i=0; i<input.length; i++) {
        if (i !== index) {
            if(input[i].startsWith(prefix) == true) {
                ok = false
            } 
        }
    }
    return ok
}

getShortestUniquePrefix(input)
```
