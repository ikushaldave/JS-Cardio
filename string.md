# String

The `String` object is used to represent and manipulate a sequence of characters.

## Properties -

1. `String Length`

    - This property used to print a length of a `string`
    - This property return a numeric value of length
    - Example

    ```js
    "Hello".length; // 4
    "".length; // 0
    " ".length; // 1
    ```

## Methods -

1. `charAt()`

    - This method **return a new string** located at passed index
    - If a index is not passed it return a string at index `0`
    - This string accept only one parameter (index)

    ```js
    const greet = "Hello AltCampus";

    greet.charAt(); // return "H" when a index is not passed it return a 0 index value of string

    greet.charAt(1); // return "e"

    greet.charAt(greet.length - 1); // return "s" which will return last value of string

    greet.charAt(20); // return "" if we passed index which is not available it will return a empty string
    ```

2. `concat()`

    - concat method concatenates the string arugment to the calling string.
    - This method accept n number of argument that to be concatenated
    - This method return a new string

    ```js
    const firstName = "Kushal";
    const lastName = "Dave";

    firstName.concat(lastName); // "KushalDave"

    firstName.concat(" " + lastName); // "Kushal Dave"

    firstName.concat(" ", lastName); // "Kushal Dave"

    firstName.concat(); // "Kushal"

    "".concat("A", "B", "C"); // "ABC"

    "".concat(1, 2, 3); // "123" Here argument passed is type of number but js try to implict converted into string type

    "".concat(true, null, false); // "truenullfalse"
    ```

3. `endsWith()`

    - This method determine whether a string ends with the characters passed as argument
    - This method have two argument
        - searchString - The string we have to search
        - length - The length used to search endsWith that particular length (Default - string.length)
    - This method return true or false.

    ```js
    const sentence = "Hey, I am Kushal Dave";

    sentence.endsWith("Dave"); // true

    sentence.endsWith("Kushal"); // false

    sentence.endsWith("Dave", 10); // false this will check in bewteen "Hey, I am "

    sentence.endsWith(); // false
    ```

4. `includes()`

    - This method determine one string is with the other string.
    - This method accept 1 argument + 1 optional
        - searchString - The string which we have find within other string
        - position (optional) - This is a index from where to search should begin (default is 0)
    - This method return true or false

    ```js
    const searchIn =
    	"Hey I am Kushal Dave, Currently learning full stack development in altcampus";

    searchIn.includes(); // false
    searchIn.includes(" "); // true
    searchIn.includes("am Kushal"); // true

    searchIn.includes("am kushal"); // false This method is case sensitive
    ```

5. `indexOf()`

    - This method is used to get a index of searched string if it found it will return a starting index of that string.
    - This method take 1 arugument + 1 optional
        - searchValue - The string which index we are looking for
        - fromIndex - This is optional used to begin serach from a passed index
    - The method return index of the first occurrence of searchValue, or -1 if not found.
    - If we pass serach index less lower than 0 and greater than str.length, then starts from index 0 to str.length.

    `"Hello World".indexOf("o", -5) // 4` as it starts search from 0 index.

    ```js
    const searchIndex =
    	"Hey I am Kushal Dave, Currently learning full stack development in altcampus";

    searchIndex.indexOf(); // -1 if this not found a index it return -1
    searchIndex.indexOf("Kushal"); // 9
    searchIndex.indexOf("kushad"); // -1 This method find index based of passed value with === and is case sensitive too.
    searchIndex.indexOf(" "); // 3 This method return 1st find index

    // TO Find from a particular index we can pass optional argument

    searchIndex.indexOf(" ", 10); // 15 In this it will start looking a string from index 10

    searchIndex.indexOf("He"); // 0 In this it checked only first two index and compared with "He" and it return 0
    ```

6. `lastIndexOf()`

    - This method is used to find a string from the last index and return its index.
    - if the index is not found it return -1.
    - This method take 1 argument + optional arguments
        - searchValue - The first argument is a string that we have to search.
        - fromIndex

7. `match()`

    - This method return a result of matching string against a regular expression.
    - This method take a regular expression object. if no regex object is found then it will implicitly convert it to RegExp.
    - This method return a array if it not found a string it return _null_
        - But if the g flag is set it will return all result matching to that in form of array but capturing group will not.
        - If the g is not set it will return only first complete group.

    ```js
    const info =
    	"Hello I am a Kushal Dave currently learning full stack development";

    info.match(); // [""] and other properties avilable with it
    info.match("I"); // ["I"] ["I", index: 6, input: "Hello I am a Kushal Dave currently learning full stack development", groups: undefined]

    info.match("Tinkal"); // null if match is not found it return null

    info.match(/[A-Z]/); // ["H"] and other properties avaibale with it in this regular expression we want to search anything starting with A-Z which it found first return it which was "H"

    info.match(/[A-Z]/g); // [ 'H', 'I', 'K', 'D' ] which result all the match it found in form of array.
    ```

> If you need to know if a string matches a regular expression RegExp, use RegExp.test().

8. `matchAll()`

    - This is similar to match() method but it will return array of all found result against regular expression including capturing group.
    - This method take a regular expression object. if no regex object is found then it will implicitly convert it to RegExp.
    - The RegExp object must have the /g flag, otherwise a TypeError will be thrown.
    - Return Iterator

    ```js
    const info =
    	"Hello I am a Kushal Dave currently learning full stack development";
    let matchAll = info.matchAll(/[A-Z]/g);
    console.log(...matchAll);

    /* OutPut ==========================
    [
    'H',
    index: 0,
    input: 'Hello I am a Kushal Dave currently learning full stack development',
    groups: undefined
    ] [
    'I',
    index: 6,
    input: 'Hello I am a Kushal Dave currently learning full stack development',
    groups: undefined
    ] [
    'K',
    index: 13,
    input: 'Hello I am a Kushal Dave currently learning full stack development',
    groups: undefined
    ] [
    'D',
    index: 20,
    input: 'Hello I am a Kushal Dave currently learning full stack development',
    groups: undefined
    ]
    ==================================== */
    ```

9. `padEnd()`

    - This method pads(fills or cover) the current string with the given string so that the resulting string reaches a given length.
    - The padding is applied from the end of the current string.
    - This method take two argument (1 Optional)
        - targetLength - The length of the resulting string once the current str has been padded. If the value is lower than str.length, the current string will be returned as-is.
        - padString - The string to pad the current str with.
        - The default value for this parameter is " "
    - It return a new string with padded.

    ```js
    const greet = "Hello";

    greet.padEnd(8); // "Hello   " Here one argument is defined what should the length after padded so return string is length of 8 and as I don't passed a optional parameter tso it padded with default " "

    greet.padEnd(8, "."); // "Hello..." Here second parameter is passed so it padded to end of greet string and return with length of 8.

    greet.padEnd(3); // "Hello" if we passed less than string length it will return original string
    ```

10. `padStart()`

    - The padStart() method pads the current string with another string (multiple times, if needed) until the resulting string reaches the given length.
    - The padding is applied from the start of the current string.
    - This method take two argument (1 Optional)
        - targetLength - The length of the resulting string once the current str has been padded. If the value is lower than str.length, the current string will be returned as-is.
        - padString - The string to pad the current str with.
        - The default value for this parameter is " "
    - It return a new string with padded.

    ```js
    const greet = "Hello";

    greet.padStart(8); // "   Hello" Here one argument is defined what should the length after padded so return string is length of 8 and as I don't passed a optional parameter tso it padded with default " "

    greet.padStart(8, "."); // "...Hello" Here second parameter is passed so it padded to end of greet string and return with length of 8.

    greet.padStart(3); // "Hello" if we passed less than string length it will return original string
    ```

11. `repeat()`

    - This method repeat the string and concatenated it.
    - This method take one parameter number of time to repeat.
    - Return a new String

    ```js
    "Hello".repeat(); // "" If we not pass parameter it return a empty string
    "Hello".repeat(2); // "HelloHello" The string "Hello" is repeated two time and get concatenated
    ```

12. `replace()`

    - The method help us to replace a pattern to a replacement.
    - This Method take two argument.
        - regexp|substr - We a pass substring or regex to match a pattern but they have samll difference if we pass substr it will replace first match but using regex it can be more powerful we can pass g flag to replace all the match pattern
        - newSubstr|function - This is replacement which is replaced in place of match pattern we can also pass a function for a replacement.
    - This method return a new string

    ```js
    "aabbcc".replace("b", "."); // "aa.bcc" here we passed a substring which we want to replace and a replacement it get replaced as we pass substring it replaced first match only.

    "aabbcc".replace(/b/g, "."); // "aabbcc" here we also passed global flag which we match all and replce it
    ```

13. `search()`

    - This method search the pattern or substring.
    - It is faster execution than match()
    - it take regex as a parameter or implicit convert a regex.
    - This method return first matched pattern index if it not found return -1.

    ```js
    "aaabbbcc".search("b"); // 3 if return first found index
    "aaabbcc".search("d"); // -1 if search not found return -1.
    "aaabbbccc".search(/c/g); // 6 it only return first match index
    ```

14. `slice()`

    - This method extract a section of string and return a new string
    - This method take two parameter
        - beginIndex - The index when to start begin extraction.
        - endIndex(Optional) - When to end the extraction. if this not passed the extraction will be default to string.length

    ```js
    "aaabbbccc".slice(3); // "bbbccc" here it start the extraction of sctring from index 3 to end of string.length
    "aaabb".slice(); // "aaabb" if not passed any argument it will extract all.
    "aaabbbccc".slice(3, 6); // "bbb" here we passed both begin and end index
    ```

15. `split()`

    - The split() method divides a String into an ordered list of substrings, puts these substrings into an array, and returns the array.
    - Parameters
        - seperator - it is a pattern we want string should split on
        - limit (Optional) - it is limit index till which a split should be part.
    - It return a array

    ```js
    "Hello I am Kushal".split(); // ["Hello I am Kushal"] if a parameter is not passed it return a array of string method called at.

    "Hello".split(""); // "Hello".split("") if a seperator is empty string ,str is converted to an array of each of its UTF-16 "characters".

    "Hello I am Kushal".split(" "); // ["Hello", "I", "am", "Kushal"] Here we passed a space as sperator.

    "Hello I am Kushal".split("a"); // ["Hello I ", "m Kush", "l"] here a seperator is string "a"
    ```

16. `startsWith()`

    - The startsWith() method determines whether a string begins with the characters of a specified string, returning true or false as appropriate.
    - Parameter
        - searchString - he characters to be searched for at the start of this string.
        - position (Optional) - position where to begin searching
    - return true or false

    ```js
    "I am Kushal".startsWith("I"); // true
    "I am Kushal".startsWith("am", 5); // false
    ```

17. `substring()`

    - The substring() method returns the part of the string between the start and end indexes, or to the end of the string.
    - Parameter
        - indexStart - The index of the first character to include in the returned substring.
        - indexEnd(Optional) - The index of the first character to exclude from the returned substring. if it miss it will goes till last index.
    - return a new substring

    ```js
    "Hello".substring(); // "hello"
    "Hello".substring(2); // "llo" the substring start from index 2
    "Hello".substring(1, 4); // "ell" the substring start from index 1 end to index 4
    ```

18. `toLowerCase()`

    - it convert a string to lowercase and return a new string with lowercase
    - it does not take any parameter
    - if it called on null and undefined it will throw and error

    ```js
    "HeLLo".toLowerCase(); // "hello"
    ```

19. `toUpperCase()`

    - it convert a string to uppercase and return a new string with uppercase
    - it does not take any parameter
    - if it called on null and undefined it will throw and error

    ```js
    "HeLLo".toUpperCase(); // "HELLO"
    ```

20. `trim()`

    - The trim() method removes whitespace from both ends of a string.
    - & return a new string representing the str stripped of whitespace from both ends.
    - It not take any parameter

    ```js
    "   Hello  ".trim(); // "Hello" here a white space is removed from both ends
    "Hello World   ".trim(); // "Hello World" Here a white space is removed from end
    ```

21. `trimEnd()` & `trimStrat()`

    - `trimEnd()` removes white space from the end of string and return new string
    - `trimStart()` removes white space from the start of string and return new string
    - Both method does not take any parameter

    ```js
    "   Hello World   ".trimStart(); // "Hello World   " Here white space is removed from the start

    "   Hello World   ".trimEnd(); // "   Hello World" Here white space is removed from the send
    ```
