# Roman to Integer
## https://leetcode.com/problems/roman-to-integer

Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.

```
Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
```

For example, two is written as II in Roman numeral, just two one's added together. Twelve is written as, XII, which is simply X + II. The number twenty seven is written as XXVII, which is XX + V + II.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX. 

There are six instances where subtraction is used:

1. I can be placed before V (5) and X (10) to make 4 and 9. 
2. X can be placed before L (50) and C (100) to make 40 and 90. 
2. C can be placed before D (500) and M (1000) to make 400 and 900.

Given a roman numeral, convert it to an integer. Input is guaranteed to be within the range from 1 to 3999.

```
Example 1:

Input: "III"
Output: 3

Example 2:

Input: "IV"
Output: 4

Example 3:

Input: "IX"
Output: 9

Example 4:

Input: "LVIII"
Output: 58
Explanation: L = 50, V= 5, III = 3.

Example 5:

Input: "MCMXCIV"
Output: 1994
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.
```

## Implementation :

```java
public int romanToInt(String s) {
        if(s == null || s.length() == 0)
            return 0;
        
        Map<Character,Integer> map = new HashMap<Character,Integer>();
        map.put('I', 1);
        map.put('V', 5);
        map.put('X', 10);
        map.put('L', 50);
        map.put('C', 100);
        map.put('D', 500);
        map.put('M', 1000);
        
        int sum = map.get(s.charAt(0));
        
        for(int i = 1; i < s.length(); i++){
            int current = map.get(s.charAt(i));
            int previous = map.get(s.charAt(i - 1));
            
            if (current > previous){
                sum += current - 2 * previous;
            } else{
                sum += current;
            }
        }
        return sum;
}
```
Above implementation have runtime complexity of O(n) and space complexity of O(1), where n is the length of the input string.

```
Runtime Complexity = O(n)
Space Complexity   = O(1)
```

## References :
https://www.youtube.com/watch?v=hEhf_oz3wsM
