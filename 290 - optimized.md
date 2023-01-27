class Solution {
    public boolean wordPattern(String pattern, String s) {
        String[] words = s.split(" ");
        if(words.length != pattern.length()) return false;
        HashMap map = new HashMap();   // not using HashMap<>
        for(Integer i = 0; i < words.length; i++){    // failed if using ""int i = 0"" 
            char c = pattern.charAt(i);
            String word = words[i];
            if(!map.containsKey(c)){
                map.put(c, i);      
            }
            if(!map.containsKey(word)){
                map.put(word, i);      
            }
            if(map.get(c) != map.get(word)){
                return false;
            }
        }
        return true;
    }
}

// HashMap map = new HashMap(); 
// pay attention to "Integer i = 0"