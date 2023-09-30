# DSA-Problems

/* .........Problem 1............... */

// function findPairsWithSum(arr, targetSum) {
//   const seenNumbers = new Set();
//   const result = [];

//   for (let i = 0; i < arr.length; i++) {
//     const currentNumber = arr[i];
//     const complement = targetSum - currentNumber;

//     if (seenNumbers.has(complement)) {
//       result.push([currentNumber, complement]);
//     }

//     seenNumbers.add(currentNumber);
//   }

//   return result;
// }

// const arr = [1, 2, 3, 4, 5, 6];
// const targetSum = 7;
// const pairs = findPairsWithSum(arr, targetSum);

// console.log(`Pairs with sum ${targetSum}:`);
// pairs.forEach(pair => {
//   console.log(pair);
// });


/* .........Problem 2............... */

// function reverseArrayInPlace(arr) {
//   let left = 0;
//   let right = arr.length - 1;

//   while (left < right) {
//     const temp = arr[left];
//     arr[left] = arr[right];
//     arr[right] = temp;
//     left++;
//     right--;
//   }
// }

// const myArray = [1, 2, 3, 4, 5];
// reverseArrayInPlace(myArray);
// console.log(myArray); 


/* .........Problem 3............... */

// function rotations(str1, str2) {
//   if (str1.length !== str2.length) {
//     return false;
//   }

//   const concatenateStr = str1 + str1;
//   if (concatenateStr.includes(str2)) {
//     return true;
//   }

//   return false;
// }

// const string1 = "hello";
// const string2 = "lohel";
// const string3 = "world";
// const string4 = "rldwo"

// console.log(rotations(string1, string2)); 
// console.log(rotations(string1, string3)); 
// console.log(rotations(string3, string4));

/* .........Problem 4............... */

// function firstNonRepeatedCharacter(str) {
//   const charCount = {};
//   for (let i = 0; i < str.length; i++) {
//     const char = str[i];
//     if (charCount[char]) {
//       charCount[char]++;
//     } else {
//       charCount[char] = 1;
//     }
//   }

//   for (let i = 0; i < str.length; i++) {
//     const char = str[i];
//     if (charCount[char] === 1) {
//       return char;
//     }
//   }
//   return null;
// }

// const inputString = "javascript";
// const result = firstNonRepeatedCharacter(inputString);
// console.log(result); 

/* .........Problem 5............... */

// function towerOfHanoi(n, source, auxiliary, destination) {
//   if (n === 1) {
//     console.log(`Move disk 1 from ${source} to ${destination}`);
//     return;
//   }

//   towerOfHanoi(n - 1, source, destination, auxiliary);
//   console.log(`Move disk ${n} from ${source} to ${destination}`);
//   towerOfHanoi(n - 1, auxiliary, source, destination);
// }
// const numDisks = 3;
// towerOfHanoi(numDisks, "A", "B", "C");

/* .........Problem 6............... */

// function postfixToPrefix(postfixExpression) {
//   const stack = [];
//   const operators = "+-*/^";

//   for (const token of postfixExpression.split(' ')) {
//     if (operators.includes(token)) {
//       const operand2 = stack.pop();
//       const operand1 = stack.pop();
//       const prefixExpression = token + " " + operand1 + " " + operand2;
//       stack.push(prefixExpression);
//     } else {
//       stack.push(token);
//     }
//   }

//   return stack.pop();
// }
// const postfixExpression = "4 11 /";
// const prefixExpression = postfixToPrefix(postfixExpression);
// console.log(prefixExpression); 


/* .........Problem 7............... */

// function prefixToInfix(prefixExpression) {
//   const stack = [];

//   for (let i = prefixExpression.length - 1; i >= 0; i--) {
//     const char = prefixExpression[i];

//     if (/[a-zA-Z0-9]/.test(char)) {
//       stack.push(char);
//     } else if (/[\+\-\*\/\^]/.test(char)) {
//       const operand1 = stack.pop();
//       const operand2 = stack.pop();

//       const infixExpression = `(${operand1}${char}${operand2})`;

//       stack.push(infixExpression);
//     }
//   }
//   return stack.pop();
// }

// const prefixExpression = "+ * 1 5 6" ;
// const infixExpression = prefixToInfix(prefixExpression);
// console.log(infixExpression); 


/* .........Problem 8............... */

// function areBracketsClosed(codeSnippet) {
//   const stack = [];
//   const brackets = "[]{}()";

//   for (const char of codeSnippet) {
//     if (brackets.includes(char)) {
//       if (char === "[" || char === "{" || char === "(") {
//         stack.push(char);
//       } else {
//         const lastBracket = stack.pop();
//         if (
//           (char === "]" && lastBracket !== "[") ||
//           (char === "}" && lastBracket !== "{") ||
//           (char === ")" && lastBracket !== "(")
//         ) {
//           return false;
//         }
//       }
//     }
//   }

//   return stack.length === 0;
// }
// const code = 'if (x > 0) { console.log("Positive"); }';
// console.log(areBracketsClosed(code)); 

// const invalidCode = 'if (x > 0) { console.log("Negative"; }';
// console.log(areBracketsClosed(invalidCode)); 


/* .........Problem 9............... */

// function reverseStack(stack) {
//   const reversedStack = [];
//   while (stack.length > 0) {
//     reversedStack.push(stack.pop());
//   }
//   return reversedStack;
// }
// const myStack = [1, 2, 3, 4];
// const reversedStack = reverseStack(myStack);

// console.log("Original Stack:", myStack); 
// console.log("Reversed Stack:", reversedStack); 


/* .........Problem 10............... */

class MinStack {
  constructor() {
    this.dataStack = [];
    this.minStack = [];
  }

  push(value) {
    this.dataStack.push(value);
    if (this.minStack.length === 0 || value <= this.getMin()) {
      this.minStack.push(value);
    }
  }

  pop() {
    if (this.isEmpty()) {
      return null;
    }

    const poppedValue = this.dataStack.pop();

    if (poppedValue === this.getMin()) {
      this.minStack.pop();
    }

    return poppedValue;
  }

  top() {
    if (this.isEmpty()) {
      return null;
    }
    return this.dataStack[this.dataStack.length - 1];
  }

  getMin() {
    if (this.isEmpty()) {
      return null;
    }
    return this.minStack[this.minStack.length - 1];
  }

  isEmpty() {
    return this.dataStack.length === 0;
  }
}

const stack = new MinStack();
stack.push(4);
stack.push(7);
stack.push(2);
stack.push(1);

console.log("smallest Element:", stack.getMin()); 
stack.pop();
stack.pop();

console.log("Top Element:", stack.top()); 
console.log("Minimum Element:", stack.getMin()); 






