# Question 1

```js
function validateString(str) {
  if (str.toLowerCase().indexOf("superman") === -1) {
    throw new Error("String does not contain superman");
  } else {
    console.log("String does contain superman");
  }
}
```

This happens because the .indexOf () function returns the position where the string that was passed in the parameter begins, in the case of "superman ..." it starts at 0 and this in the if (! ...) instruction takes a true value since it denies 0 (false in Boolean) to 1 (true).

So the way to compare in the if statement is with the absolute equality of -1, since this will be the value that the indexOf () function will return if it does not contain the parameter.

# Question 2

```js
function isContained(array, integer) {
  if (array.includes(integer)) {
    return true;
  }
  return false;
}
```

Well the solution is simple, using the native function includes() of the array that lets you know if an element is included.

# Question 3

```js
function formatStandar(phone, delimiter = "-") {
  //string to array
  phone = phone.split("");
  //iterate array
  for (i = 0; i < phone.length; i++) {
    //I check if the character is not a number
    if (!Number.parseInt(phone[i]) && phone[i] != "0") {
      //change the value for empty
      phone[i] = "";
    }
  }
  //array to string
  phone = phone.toString();

  //remove comma
  phone = phone.replace(/,/g, "");

  if (phone.length === 10) {
    //String to array
    phone = phone.split("");
    //include delimiter in the format USA phone
    phone[2] = phone[2] + delimiter;
    phone[5] = phone[5] + delimiter;
    //array to string
    phone = phone.toString();
    //remove comma
    phone = phone.replace(/,/g, "");
    return phone;
  } else {
    throw new Error("Does not meet as valid phone number for 3-3-4 format");
  }
}
```

# Question 4

```js
function fizzBuzz(start = 1, stop = 100) {
  let result = "";

  if (stop < start || start < 0 || stop < 0) {
    throw new Error("Invalid arguments");
  }

  for (let i = start; i <= stop; i++) {
    if (i % 3 === 0 && i % 5 === 0) {
      result += "FizzBuzz";
      continue;
    }

    if (i % 3 === 0) {
      result += "Fizz";
      continue;
    }

    if (i % 5 === 0) {
      result += "Buzz";
      continue;
    }

    result += i;
  }

  return result;
}

//success case
var test = fizzBuzz();
console.log(test);
test = fizzBuzz(2);
console.log(test);
test = fizzBuzz(2, 6);
console.log(test);
test = fizzBuzz(2, 6);
console.log(test);
test = fizzBuzz("a", "b");
console.log(test);
test = fizzBuzz(1, 1);
console.log(test);
test = fizzBuzz("1", 2);
console.log(test);
test = fizzBuzz(1, "3");
console.log(test);
test = fizzBuzz("3", 1);
console.log(test);
test = fizzBuzz([1, 2], [3, 4]);
console.log(test);
//error case
test = fizzBuzz(200);
console.log(test);
test = fizzBuzz("a");
console.log(test);
test = fizzBuzz(-1);
console.log(test);
test = fizzBuzz(6, 2);
console.log(test);
test = fizzBuzz(-1, -4);
console.log(test);
test = fizzBuzz(-1, 3);
console.log(test);
test = fizzBuzz(0, -3);
console.log(test);
test = fizzBuzz("3", 1);
console.log(test);
test = fizzBuzz([1, 2], [3, 4]);
console.log(test);
```

# Question 5

```js
function exclude() {
  const files = [
    "/src/common/api.js",
    "/src/common/preferences.js",
    "/src/styles/main.css",
    "/src/styles/base/_base.scss",
    "/src/assets/apple-touch-icon-57.png"
  ];

  const exclude = ["/src/styles/", "/src/assets/apple-touch-icon-57.png"];

  //remove specific files
  var newFiles = files.filter(function(file) {
    if (exclude.indexOf(file) < 0) {
      return exclude.indexOf(file) < 0;
    }
  });

  //find files belonging to directories
  filesEquals = newFiles.filter(function(file) {
    for (var i = 0; i < exclude.length; i++) {
      if (file.indexOf(exclude[i]) >= 0) {
        return file;
      }
    }
  });

  //remove files belonging to directories
  newFiles = newFiles.filter(function(file) {
    if (exclude.indexOf(file) < 0) {
      return filesEquals.indexOf(file) < 0;
    }
  });

  return newFiles;
}
```

# Question 6

```js
function getColorName(name = "Gabriel Ortega") {
  //delete space
  name = name.replace(/ /g, "");
  //Hexadecimal numbers array
  var hexadecimal = new Array(
    "0",
    "1",
    "2",
    "3",
    "4",
    "5",
    "6",
    "7",
    "8",
    "9",
    "A",
    "B",
    "C",
    "D",
    "E",
    "F"
  );
  //integer number of the number of characters that the string should divide
  var numbercharacters = Math.trunc(name.length / 6);
  //Intance array that will contain the color hexadecimal
  var arrayHexadecimal = new Array();
  var begin = 0;
  // loop until arrangement has size 6
  for (var i = 0; i < 6; i++) {
    if (i == 5) {
      arrayHexadecimal.push(name.substr(begin, name.length - 1));
    } else {
      arrayHexadecimal.push(name.substr(begin, numbercharacters));
    }

    begin = begin + numbercharacters;
  }

  //iterating the array
  for (i = 0; i < arrayHexadecimal.length; i++) {
    //intence sum ASCII character values
    var quantityAscii = 0;
    for (var j = 0; j < arrayHexadecimal[i].length; j++) {
      quantityAscii += arrayHexadecimal[i].charCodeAt(j);
    }
    //integer to string
    quantityAscii = quantityAscii.toString();
    //intence add char
    var addChar = 0;
    //iterating string
    for (var k = 0; k < quantityAscii.length; k++) {
      //sum of unit quantities char
      addChar += parseInt(quantityAscii.charAt(k));
    }
    quantityAscii = addChar;
    while (quantityAscii > 15) {
      quantityAscii = Math.trunc(quantityAscii / 16);
    }
    //value positional of  hexadecimal (Array)
    arrayHexadecimal[i] = hexadecimal[quantityAscii];
  }
  var colorHexadecimal = "#";
  //array to string
  arrayHexadecimal = arrayHexadecimal.toString();
  //remove comma
  arrayHexadecimal = arrayHexadecimal.replace(/,/g, "");
  colorHexadecimal += arrayHexadecimal;
  return colorHexadecimal;
}
```

The solution was taking into account the number of characters that have a hexadecimal number and the ASCII value of the characters in a text string. Apply a series of transformations and loops to always arrive at a unique answer according to the given text string

# Question 7

```js
(function() {
  for (var i = 0, l = 10; i < l; i++) {
    document.getElementById("button-" + i).onclick = function(e) {
      var number = e.path[0].id.replace("button-", "");
      console.log("Line %s", number);
    };
  }
})();
```

listen to the click event and depending on the button that activates it you reach the number

# Question 8

```js
function iterable(argument) {
  if (argument === null) {
    return false;
  }
  if (argument[Symbol.iterator]) {
    return true;
  }
  return false;
}
```
