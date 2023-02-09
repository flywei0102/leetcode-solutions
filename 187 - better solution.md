class Solution {
    public List<String> findRepeatedDnaSequences(String s) {
        List<String> ans;
        Set<String> set = new HashSet<>();
        Set<String> setRepeat = new HashSet<>();

        for(int i = 0; i + 10 <= s.length(); i++){
            String sub = s.substring(i, i + 10);
            if(!set.contains(sub)){
                set.add(sub);
            }else{
                if(!setRepeat.contains(sub)){
                    setRepeat.add(sub);
                }               
            }
        }
        ans = new LinkedList<>(setRepeat);
        return ans;
    }
}

// optimal solution