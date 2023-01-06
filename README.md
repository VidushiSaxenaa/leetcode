# leetcode
class Solution {
    public int romanToInt(String s) {
        if (s == null)
            return 0;
        
        int prev = getValue(s.charAt(0));
        int res = prev;
        
        for (int i = 1; i < s.length(); i++) {
            int cur = getValue(s.charAt(i));
            res += cur > prev ? cur - 2*prev : cur;
            prev = cur;
        }
            
        return res;
    }
    
    public int getValue(char c){
        switch (c) {
                case 'I':
                    return 1;
                case 'V':
                    return 5;
                case 'X':
                    return 10;
                case 'L':
                    return 50;
                case 'C':
                    return 100;
                case 'D':
                    return 500;
                case 'M':
                    return 1000;
                default:
                    return 0;
            }
    }
}

Second solution (a little bit worse)

class Solution {
    public int romanToInt(String s) {
        if (s == null)
            return 0;
        
        Map<Character, Integer> rn = new HashMap<Character, Integer>(){
            {
                put('I', 1);
                put('V', 5);
                put('X', 10);
                put('L', 50);
                put('C', 100);
                put('D', 500);
                put('M', 1000);
            }
        };

        int prev = rn.get(s.charAt(0));
        int res = prev;
        
        for (int i = 1; i < s.length(); i++) {
            int cur = rn.get(s.charAt(i));
            res+= cur;
            
            if (cur > prev) {
                res -= 2*prev;
            }   
            prev = cur;    
        }
            
        return res;
    }
}
