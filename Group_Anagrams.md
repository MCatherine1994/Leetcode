#### **[Group Anagrams](https://leetcode.com/problems/group-anagrams/)**
Given an array of strings, group anagrams together
```
Input: ["eat", "tea", "tan", "ate", "nat", "bat"]
Output:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]
```

Python  
```
def groupAnagrams(strs):
    ans = collections.defaultdict(list)
    for s in strs:
        ans[tuple(sorted(s))].append(s)
    return ans.values()
```
- Algorithm Explain
    - For each string in the list, sort it and convert it to a tuple like ('a', 'b', 't'), so for the string with the same letter will have the same tuple
    - When try to store them into the dictionary, use the sorted tuple as the key so anagrams have the same key, could be append to the same list
    - Dictionary "ans" looks like
        ```
        {  
            ('a','b','t'): ['bat'],  
            ('a','n','t'): ["nat","tan"],  
            ('a','e','t'): ["ate","eat","tea"]  
        } 
        ```
- [collection.defaultdict](https://docs.python.org/2/library/collections.html#collections.defaultdict) - create a dictionary and by given (list), it means the value will be a list. So for every key in this dictionay, its value will be a list, then there is no need to declare the list when access to the key, could use append directly
- [difference between sorted() and .sort](https://discuss.codecademy.com/t/what-is-the-difference-between-sort-and-sorted/349679) - "sorted()" will not modify the original string while ".sorted" will. Can sort list, tuple, string. Order based on "reverse=True or False"
- [python dictionary method](https://www.w3schools.com/python/python_ref_dictionary.asp)    
    - "dict.values()" returns a list of all values
    - "dict.keys()" returns a list of all keys
    - "dict.items()" returns a list of (key, value) tuples