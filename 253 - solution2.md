class Solution {
    public int minMeetingRooms(int[][] intervals) {
        TreeMap<Integer, Integer> map = new TreeMap<>();
        for(int[] interval : intervals){
            int count = map.getOrDefault(interval[0], 0);
            map.put(interval[0], count + 1);
            count = map.getOrDefault(interval[1], 0);
            map.put(interval[1], count - 1);
        }
        int maxcount = 0;
        int count = 0;
        for(Map.Entry<Integer, Integer> entry : map.entrySet()){
            count += entry.getValue();
            maxcount = Math.max(maxcount, count);
        }
        return maxcount;
    }
}

// this solution（扫描线算法） is easy to understand but less efficient than minheap, 
// solution: 找出某一段时间需要会议室数目的最大值
// 将intervals从左到右扫描，如果遇到一个会议开始，会议室的个数就加一个；如果遇到了一个会议的结束，会议室的个数就减一个；最后取这个过程中会议室数量的最大值
// 扫描的过程不需要排序，直接用一个map<timestamp, count>来记录每一个时间点的会议室数量，如果是开始时间就+1，如果是结束时间就-1