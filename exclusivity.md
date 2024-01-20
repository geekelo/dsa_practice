
# QUESTION
// Compare arrays and return a new array with any items only found in one of the two given arrays, 
// but not both. In other words, return the symmetric difference of the two arrays.

// You can return the array with its elements in any order.

// arr1 = [1, 2, 3]
// arr2 = [5, 2, 1, 4]

/// input = 2 arrays
// output - singe array with items that ar unique to both ararys
// chck  the items in arr1 if they are present n array 2 = 3
// chck  the items in arr2 if they are present n array 1=  5, 4
// expected to return [ 3, 5, 4]

## JS
```
function solution(arr1, arr2){
  let result = [];
  arr1 = arr1.sort();
  arr2 = arr2.sort();
  
  if (arr1.length === 0) {
    result = arr2;
  } else if (arr2.length === 0) {
    result = arr1;
  } else if (arr1 === arr2) {
    result = [];
  } else {
  
  
  for (i = 0; i < arr1.length; i++) {
    if (!arr2.includes(arr1[i])){
      result.push(arr1[i])
    }
  }
    for (i = 0; i < arr2.length; i++) {
    if (!arr1.includes(arr2[i])){
      result.push(arr2[i])
    }
  }
  }
  return result;
}

console.log(solution([5], [5, 1]));

```
