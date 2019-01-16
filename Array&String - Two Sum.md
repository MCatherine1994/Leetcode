#### **Question:**  
Given an array of integers, find two numbers such that they add up to a specific target number.  
Return two indices, where index1 must be less than index2 and they are not zero-based.   
Assume there is only one solution.  

#### **Solution in Java:**  
```
public int[] twoSum(int[] numbers, int target) {
  Map<Integer, Integer> map = new HashMap<>();
  for(int i = 0; i < numbers.length - 1; i++) {
    int x = numbers[i];
    if(map.containsKey(target - x)) {
      return new int[] {map.get(target - x) + 1, i + 1};
    }
    map.put(x, i);
  }
  throw new IllegalArgumentException("No two sum solution");
}
```

#### **Question:**  
If the input array is sorted in ascending order?  

#### **Solution:**  
```
public int[] twoSum(int[] numbers, int target) {
  int i = 0, j = numbers.length - 1;
  while(i < j) {
    int sum = numbers[i] + numbers[j];
    if(sum < target) {
      i++ ;
    } else if (sum > target) {
      j-- ;
    } else {
      return new int[] {i + 1, j + 1};
    }
  }
  throw new IllegalArgumentException("No two sum solution");
}
```
