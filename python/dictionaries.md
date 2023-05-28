cars = {
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
Dictioanries are mutable, so entries can be added, removed, and changed. They are ordered.

Built-in methods for dictionary:
1. fromkeys(key_tuple, value) : Returns a dictionary with the specified keys and value
```
x = ('key1', 'key2', 'key3')
y = 0
thisdict = dict.fromkeys(x, y)
print(thisdict)
```
Output:
```
{'key1':0, 'key2':0, 'key3':0}
```
2. get()  : Returns the value of the specified key

`dictionary.get(keyname, value)`

keyname	: Required. The keyname of the item you want to return the value from

value : 	Optional. A value to return if the specified key does not exist.

Default value : None

```
cars.get("Brand", "")
```
Output: 
`Ford`
items() : Returns a list containing a tuple for each key value pair
The view object contains the key-value pairs of the dictionary, as tuples in a list.
```
print(cars.items())
```
Output: 
`dict_items([('brand', 'Ford'), ('model', 'Mustang'), ('year', 1964)])`
```
car["year"] = 2018

print(x)
```
Output:
`dict_items([('brand', 'Ford'), ('model', 'Mustang'), ('year', 2018)])`

3. keys() :	Returns a list containing the dictionary's keys
```
x = car.keys()
print(x)
```
Output: `dict_keys(['brand', 'model', 'year'])`

4. pop(keyname, defaultvalue): Removes the element with the specified key

5. popitem() : Removes the last inserted key-value pair

6. setdefault(keyname, value)	: Returns the value of the specified key. If the key does not exist: insert the key, with the specified value
7.  update(iterable)	: Updates the dictionary with the specified key-value pairs. A dictionary or an iterable object with key value pairs, that will be inserted to the dictionary.
8. values() : Returns a list of all the values in the dictionary

Ref: https://www.w3schools.com/python/python_ref_dictionary.asp

Some Observations: 

1.
```
class Solution(object):
    def containsDuplicate(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        d = {}
        for num in nums:
            if num in d:
                return True
            else:
                d[num] = 1
        return False
 ```
 2.
 ```
 class Solution(object):
    def containsDuplicate(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        d = {}
        for num in nums:
            if num in d.keys():
                return True
            else:
                d[num] = 1
        return False
 ```
 Code block 2 gave time limit exceeded error but code bloc 1 did not. Difference? 
 The only difference is in the line `if num in d.keys():` vs `if num in d:`
 
 Ref: https://leetcode.com/problems/contains-duplicate/submissions/958483481/
