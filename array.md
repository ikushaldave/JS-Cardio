# Array

Array is a object collection of data in order form where key is always defined by JS.

## Properties

1. `length`

    - This property return a length of an array

    ```js
    [].length[(1, 2)].length; // 0 // 2
    ```

## Methods

### **Static Method**

This method is applied on Array object itself.

1. `Array.from()`

    - This static method create a shallow-copied Array instance from array like or iterable object
    - This take 1 parameter and 2 Optional
        - arrayLike - An array-like or iterable object to convert to an array.
        - mapFn - the function which behave like map method of array
        - thisArgs
    - Return a shallow copied array

    ```js
    Array.from("hello"); // ["h", "e", "l", "l", "o"] As string is iterable object

    Array.from([1, 2, [3, 4], 5]); // [1, 2, [3, 4], 5] it is shallow copied of pass array

    Array.from([1, 2, 3], (x) => x + x);
    [2, 4, 6]; // New array returned and 2nd optional argument map the passed array
    ```

2. `Array.isArray()`

    - The Array.isArray() method determines whether the passed value is an Array.
    - it take one parameter a value who had to check is array or not
    - Return true or false

    ```js
    Array.isArray([1, 2, 3]); // true
    Array.isArray({ foo: 123 }); // false
    Array.isArray("foobar"); // false
    Array.isArray(undefined); // false
    ```

3. `Array.of()`

    - Create a new array from n passed argument
    - It takes n arguments
    - Return a new array

    ```js
    Array.of(7); // [7]
    Array.of(1, 2, 3); // [1, 2, 3]

    Array(7); // array of 7 empty slots
    Array(1, 2, 3); // [1, 2, 3]
    ```

> The difference between Array.of() and the Array constructor is in the handling of integer arguments: Array.of(7) creates an array with a single element, 7, whereas Array(7) creates an empty array with a length property of 7

### **Methods**

4. `concat()`

    - This method is used to merge two or more array into single array
    - This method takes n value as argument
    - This method return a new array

    ```js
    [1, 2, 3]
    	.concat(["A", "B", "C"]) // [1, 2, 3 , "A", "B", "C"] This method concat the passed array to array at method get called

    	[(1, 2, 3)].concat(["A", "B", "C"], [22, 23, ["a", "b"]]) // [1, 2, 3, "A", "B", "C", 22, 23, ["a", "b"]]

    	[(1, 2, 3)].concat(1, 2); // [1, 2, 3, 1, 2] This also take all datatypea as argument and return new array
    ```

> Object references (and not the actual object): concat copies object references into the new array. Both the original and new array refer to the same object. That is, if a referenced object is modified, the changes are visible to both the new and original arrays.

> Data types such as strings, numbers and booleans (not String, Number, and Boolean objects): concat copies the values of strings and numbers into the new array.

5. `every()`

    - This method check whether a every element passed a test implemented by the provided function.
    - This method take one argument (+ One optional)
        - callback - a function to test for each element, taking 3 arguments (element, index (optional), array (optional)).
        - thisArgs
    - This method return true or false based on condition statisfied by each element or not.

    ```js
    [1, 30, 39, 29, 10, 13]
    	.every((x) => x > 0) // true as each element statisfied the test implemented and all are true return true

    	[(1, 30, 39, 29, 10, 13)].every((x) => x > 1); // false as when a cb function run for 1st element and check condition on that as it false so it return false
    ```

6. `fill()`

    - This method change all element of array to a static value
    - This method accept 1 parameter and 2 optional parameter
        - value - value to fill a array with
        - start - start index Defalut 0
        - end - end index Default arr.length
    - Modified array filled with static value

    ```js
    [1, 2, 3]
    	.fill() // [undefined, undefined, undefined] if fill value is not passed it fill with undefind
    	[(1, 2, 3)].fill(0) // [0, 0, 0] if fill all array element with a 0
    	[(1, 2, 3, 4, 5)].fill(0, 2) // [1, 2, 3, 0, 0] it started filling from index 2 to arr.length
    	[(1, 2, 3, 4, 5)].fill(0, 1, 3); // [1, 0, 0, 4, 5] it started filling from index 1 to 2
    ```

7. `find()`

    - The find() method returns the value of the first element in the provided array that satisfies the provided testing function.
    - This method take one parameter + 1 Optional
        - callback - Function to execute on each value in the array, taking 3 arguments:(element, index(Optional), array(optional))
        - thisArgs
    - Return value of the first element in the array that satisfies the provided testing function. Otherwise, undefined is returned.

    ```js
    [2, 4, 6, 8].find((ele) => ele > 6); // 8 Here the test condition is return first element which is > 6
    [2, 4, 6, 8].find((ele) => ele > 8); // undefined if a test condition is not satisfies it return undefined
    [2, 4, 6, 8].find((ele, idx, arr) => {
    	console.log(ele, idx, arr);
    	return ele > 6;
    }); // 8 3 [2, 4, 6, 8] & 8 as here I am console.log all the parameters and return first satifies test value
    ```

8. `findIndex()`

    - The findIndex() method returns the index of the first element in the array that satisfies the provided testing function. Otherwise, it returns -1, indicating that no element passed the test.
    - This method take one parameter + 1 Optional
        - callback - A function to execute on each value in the array until the function returns true, indicating that the satisfying element was found. taking 3 arguments:(element, index(Optional), array(optional))
        - thisArgs
    - Return The index of the first element in the array that passes the test. Otherwise, -1

    ```js
    [2, 4, 6, 8].findIndex((ele) => ele > 6); // 3 Here the test condition is return index of first element which staisfies > 6
    [2, 4, 6, 8].findIndex((ele) => ele > 8); // -1 if a test condition is satisfies it return -1
    [2, 4, 6, 8].find((ele, idx, arr) => {
    	console.log(ele, idx, arr);
    	return ele > 6;
    }); // 8 3 [2, 4, 6, 8] & 3 as here I am console.log all the parameters and return index of first satifies test value
    ```

9. `flat()`

    - The flat() method creates a new array with all sub-array elements concatenated into it recursively up to the specified depth.
    - This method accept one parameter depth (The depth level specifying how deep a nested array structure should be flattened. Defaults to 1.)
    - A new array with the sub-array elements concatenated into it.

    ```js
    [1, 2, 3, [4, 5, [6]]]
    	.flat() //  [1, 2, 3, 4, 5, [6]] As all subarray get concatenated in new array as default depth is 1 so [6] not get concatenated as it depth level is 2 as we used default value depth 1

    	[(1, 2, 3, [4, 5, [6]])].flat(2) // [1, 2, 3, 4, 5, 6] Here all subarray get concatenated as we pass a depth limit of 2 which flat till depth 2

    	[[1, [2, [3, [4, [5, [6]]]]]]].flat(Infinity); // [1, 2, 3, 4, 5, 6] Here all subarray get concatenated as we pass a depth limit of Infinity (the max value) which flat till depth Infinity
    ```

10. `forEach()`

    - This method execute a provided function to each element of array
    - This method take 1 parameter and 1 optional
        - callback - Function to execute on each element. It accepts between one and three arguments: element, index, array
        - thisArgs (optional)
    - Return undefined

    ```js
    [1, 2, 3].forEach((ele) => console.log(ele)); // it log 1, 2, 3 as it return undefined

    // As we can use as for...of loop this method but provide more information than for...of it provide index and array too
    ```

11. `include()`

    - The includes() method determines whether an array includes a certain value among its entries
    - This method take one parameter & one optional
        - valueToFind - The value to search for.
        - fromIndex - The position in this array at which to begin searching for valueToFind. Default to 0
    - Return true or false

    ```js
    [1, 2, 3]
    	.includes(2) // true as array include value 2
    	[(1, 2, 3)].includes(5) // false as array not include value 5
    	[(1, 2, 3, 4, 5, 6)].includes(5, 2); // true as array include value 5 here search begin from index 2
    ```

> When comparing strings and characters, includes() is case-sensitive.

12. `indexOf()`

    -   The indexOf() method returns the first index at which a given element can be found in the array, or -1 if it is not present.
    -   This method take one parameter & one optional
        -   searchElement - Element to locate in the array.
        -   fromIndex - The index to start the search at.
    -   Return first index of the searchElement if found or -1 if not

    ```js
    [1, 2, 3]
    	.indexOf(2) // 1 as array include value 2 and index of 2 is 1
    	[(1, 2, 3)].indexOf(5) // -1 as array not include value 5 they return -1 if not found
    	[(1, 2, 3, 4, 5, 6)].indexOf(5, 2); // 4 as array include value 5 here search begin from index 2 and index of 5 is 4
    ```

13. `join()`

    -   The join() method creates and returns a new string by concatenating all of the elements in an array (or an array-like object), separated by commas or a specified separator string.
    -   This method take only one parameter (seperator)
        -   seperator - if a seperator is not provided it will be separated by commas(,) & if a seperator is a empty string it will be joined without any character and if a sepertor is a anything it will converted to string
    -   Return a string with all array joined with seperator. if arr.length is 0 it return empty string

    ```js
    ["A", "B", "C"]
    	.join() // "A,B,C" if a seperator is not passed it will be joined by commas
    	[("A", "B", "C")].join("") // "ABC" if a seperator is a empty string it will be joined without any character
    	[("A", "B", "C")].join(" ") // "A B C" is a seperator is white space it will joned b/w adjacent element
    	[("A", "B", "C")].join("-"); // "A-B-C" here a seperator is -
    ```

14. `lastIndexOf()`

    -   The lastIndexOf() method returns the last index at which a given element can be found in the array, or -1 if it is not present.
    -   The array is searched backwards, starting at fromIndex
    -   This method accept one parameter and one optional
        -   searchElement - Element to locate in the array.
            -fromIndex - The index at which to start searching backwards
    -   Return the last index of the element in the array; -1 if not found.

    ```js
    [1, 2, 3, 2, 1]
    	.lastIndexOf(2) // 3 as array include value 2 and it search from backward and return last value 2 index
    	[(1, 2, 3, 2, 1)].lastIndexOf(5) // -1 as array not include value 5 they return -1 if not found
    	[(1, 2, 3, 4, 5, 6)].lastIndexOf(5, 2); // -1 as array include value 5 here search begin from backward of index 2 and its has not 5 so it return -1
    ```

15. `pop()`

    -   The pop() method removes the last element from an array and returns that element. This method changes the length of the array.
    -   It doesn't take any parameter
    -   return last element from a array and it mututae a origin array by removing last element

    ```js
    const arr = [1, 2, 3];
    arr.pop(); // 3 it return last removing last element from original array
    console.log(arr); // [1, 2]
    ```

16. `push()`

    -   The push() method adds one or more elements to the end of an array and returns the new length of the array.
    -   it accept n element to add in end of array
    -   return new length of a array

    ```js
    const arr = [1, 2, 3];
    arr.push(4, 5); // 5 return a new length of original array
    console.log(arr); // [1, 2, 3, 4, 5]
    ```

17. `shift()`

    -   The shift() method removes the first element from an array and returns that removed element. This method changes the length of the array.
    -   It doesn't accept any parameter
    -   return a first element of array and removes the first element from the original array and mutate a length of array

    ```js
    const arr = [1, 2, 3];
    arr.shift(); // 1 it return first element and removing first element from original array
    console.log(arr); // [2, 3]
    ```

18. `unshift()`

    -   The unshift() method adds one or more elements to the beginning of an array and returns the new length of the array.
    -   it accept n element to add in starting of array
    -   return new length of a array

    ```js
    const arr = [1, 2, 3];
    arr.unshift(4, 5); // 5 return a new length of original array
    console.log(arr); // [4, 5, 1, 2, 3,] new element added to starting of array
    ```

19. `filter()`

    -   The filter() method creates a new array with all elements that pass the test implemented by the provided function
    -   This method accept one parameter and one optional
        -   callback - Function is a used to test each element of the array. Return true to keep the element, false otherwise.
            (element, index, array)
        -   thisArgs (optional)
    -   Return a new array with the elements that pass the test. If no elements pass the test, an empty array will be returned.

    ```js
    [1, 2, 3, 4, 5, 6]
    	.filter((ele) => ele % 2 == 0) // [2, 4, 6] it return a new array in which element which statisfied a test are pushed

    	[
    		("spray", "limit", "elite", "exuberant", "destruction", "present")
    	].filter((ele) => ele.length > 6); // ["exuberant", "destruction", "present"] it return a new array in which element which has length > 6
    ```

20. `map()`

    -   This method poupulated a expression in each element and return a new array
    -   This method take one parameter & one optional
        -   callback - Function that is called for every element of arr. Each time callback executes, the returned value is added to new_array. (element, index, array)
        -   thisArgs
    -   Return a new array without mutating a original array

    ```js
    [1, 2, 3, 4, 5].map((ele) => ele * 2); // [2, 4, 6, 8, 10] here each element get through a expression of call back and return from call back pushed to array and return a new array
    ```

21. `reverse()`

    -   The reverse() method reverses an array in place. The first array element becomes the last, and the last array element becomes the first.
    -   This method doesn't have any parameter
    -   Return a reversed array

    ```js
    [1, 2, 3, 4, 5, 6].reverse(); // [6, 5, 4, 3, 2, 1] return reversed array

    const arr = [5, 12, 8, 130, 44];
    arr.reverse();
    console.log(arr); // [44, 130, 8, 12, 5] It mutate a original array
    ```

22. `some()`

    -   The some() method tests whether at least one element in the array passes the test implemented by the provided function. It returns a Boolean value.
    -   This method take one parameter and one optional
        -   callback - A function to test for each element, taking three arguments:(element, index, arr)
        -   thisArgs (Optional)
    -   return true or false

    ```js
    [1, 2, 3, 4, 5]
    	.some((ele) => ele % 2 === 0) // true it  tests whether at least one element in the array passes the test.
    	[(1, 2, 3, 4, 5)].some((ele, index) => index > 8); // false here we test is this array has index > 8 which is false
    ```

23. `slice()`

    -   The slice() method returns a shallow copy of a portion of an array into a new array object.
    -   This method accept two optional parameter
        -   start - Zero-based index at which to start extraction.
        -   end - Zero-based index before which to end extraction. slice extracts up to but not including end. For example, slice(1,4) extracts the second element through the fourth element (elements indexed 1, 2, and 3).
    -   Return a new array contain extracted element

    ```js
    [1, 2, 3, 4, 5]
    	.slice() // [1, 2, 3, 4, 5] It will create all shallow copy.
    	[(1, 2, 3, 4, 5)].slice(2) // [3, 4, 5] It will create shallow copy from index 2 to arr.length
    	[(1, 2, 3, 4, 5)].slice(2, 4); // [3, 4] It will return shallow copy from index 2 to end index 4
    ```

24. `splice()`

    -   This method change the content by removing or replacing existing element and or adding new element
    -   This method accept 1 parameter and 2 optional parameter
        -   start - the index when to start changing a array
        -   deleteCount - An integer indicating the number of elements in the array to remove from start.
        -   item1, item2, ... - The elements to add to the array, beginning from start.
    -   Return a array of deleted item, if no item is deleted it return empty array. It mutate the original array

    ```js
    const arr = [1, 2, 3, 4, 5];
    arr.splice(0); // [1, 2, 3, 4, 5] here we seen it start removing item from 0 index to arr.length and return array of removed item
    console
    	.log(arr) // [] // it mutate the original array

    	[(1, 2, 3, 4, 5)].splice(1, 3); // [2, 3, 4] it will remove item fron index 1 to 3 and return array of removed item

    const arr = [1, 2, 3, 4, 5];
    arr.splice(5, 0, 6, 7, 8); // [] Here we pass start at index 5 and remove 0 item and add 6,7,8 from a start index
    console.log(arr); // const arr = [1, 2, 3, 4, 5];
    arr.splice(4, 0, 6, 7, 8); // [] Here we pass start at index 4 and remove 0 item and add 6,7,8 after a start index
    console.log(arr); // [1, 2, 3, 4, 6, 7, 8, 5]
    ```

25. `reducer`

    -   The reduce() method executes a reducer function (that you provide) on each element of the array, resulting in single output value.
    -   This method take 1 parameter and 1 optional

        -   callback - A function to execute on each element in the array (except for the first, if no initialValue is supplied).
            This method take 2 parameter and 2 optional

                - accumulator -  The value of accumlator is a return value of callback function if a initial value is present if initial value is not passed the value of accumlator is set to 0 index of array.
                - element (current value)
                - index
                - array

        -   initial value (optional) - A value to use as the first argument to the first call of the callback. If no initialValue is supplied, the first element in the array will be used as the initial accumulator value and skipped as currentValue.

    -   This method return a single value after reduction

    ```js
    [1, 2, 3, 4, 5].reduce((acc, element) => (acc += element), 0); // 15 Here we set a initial value to 0 and when a call back function be called the value of accumlator is set to 0 and elment get add to accumlator value and return value get set to accumator 1 and current value to 2 and it goes on and return final reduced value

    ["a", "b", "c", "a", "b"].reduce((a, e) => {
    	if (a[e]) {
    		a[e]++;
    	} else {
    		a[e] = 1;
    	}
    	return a;
    }, {});

    // { a: 2, b: 2, c: 1 } Here we are passing a initial value as {} and when a callback function get called the value of accumulator will be reference of initial value and it will check the condition is object has that key or not if not it will return undefined and if statement get false and else statement will get executed and setting value to a object and return accumulator value reference to next call to set same reference and keep executing
    ```
