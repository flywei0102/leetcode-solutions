class Solution {
    public boolean isValidSudoku(char[][] board) {
        int n = 9;
        
        HashSet<Integer>[] rows = new HashSet[n];
        HashSet<Integer>[] cols = new HashSet[n];
        HashSet<Integer>[] boxes = new HashSet[n];    
        for(int i = 0; i < n; i ++){
            rows[i] = new HashSet<Integer>();
            cols[i] = new HashSet<Integer>();
            boxes[i] = new HashSet<Integer>();   // 分为9个区域，每个区域3*3
        }
        for(int r = 0; r < n; r++){
            for(int c = 0; c < n; c++){
                int a = board[r][c];
                if(Integer.valueOf(a) == '.'){
                    continue;
                }
                if(rows[r].contains(a)){
                    return false;
                }
                rows[r].add(a);
                if(cols[c].contains(a)){
                    return false;
                }
                cols[c].add(a);
                int idx = (r/3)*3 + c/3;
                if(boxes[idx].contains(a)){
                    return false;
                }
                boxes[idx].add(a);
            }
        }
        return true;
        
    }
}