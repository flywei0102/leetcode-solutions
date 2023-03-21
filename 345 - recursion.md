class Solution {
    String vowels = "aeiouAEIOU";
    public String reverseVowels(String s) {
        if(s.length() == 0 || s == null) return null;
        char[] chars = s.toCharArray();
        helper(chars, 0, s.length() - 1);
        return new String(chars);
    }
    private void helper(char[] chars, int left, int right){
        if(left >= right) return;   
        while(left < right && !vowels.contains(chars[left] + "")) left ++;
        while(left < right && !vowels.contains(chars[right] + "")) right --;
        swap(chars, left, right);
        helper(chars, left + 1, right - 1);
    }

    private void swap(char[] chars, int i, int j){
        char temp = chars[i];
        chars[i] = chars[j];
        chars[j] = temp;
    }
}

// recursive Solution