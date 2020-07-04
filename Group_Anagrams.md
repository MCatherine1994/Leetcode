## **[Group Anagrams](https://leetcode.com/problems/group-anagrams/)**
### **Problem Description:**
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

### **Python Solution:**
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


### **Java Solution:**
```
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        if (strs.length == 0) return new ArrayList();
        Map<String, List> ans = new HashMap<String, List>();
        for (String s : strs) {
            char[] ca = s.toCharArray();
            Arrays.sort(ca);
            String key = String.valueOf(ca);
            if (!ans.containsKey(key)) ans.put(key, new ArrayList());
            ans.get(key).add(s);
        }
        return new ArrayList(ans.values());
    }
}
```
- [Java ArrayList](https://www.w3schools.com/java/java_arraylist.asp) - The ArrayList class is a resizable array, while elements can be added and removed from an ArrayList whenever you want
- [Java Map](http://tutorials.jenkov.com/java-collections/map.html), [Java HashMap](https://www.w3schools.com/java/java_hashmap.asp) - <data_type_of_the_key, data_type_of_the_value>
- [toCharArray](https://www.geeksforgeeks.org/java-string-tochararray-example/) - convert the string to an character array; [String.valueOf](https://www.tutorialspoint.com/java/java_string_valueof.htm) - return the string representation of the char array argument
