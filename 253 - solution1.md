class Solution {
    public int minMeetingRooms(int[][] intervals) {
        Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));  // sorted by the start time
        PriorityQueue<int[]> minheap = new PriorityQueue<>((a, b) -> Integer.compare(a[1], b[1]));   // <starttime, endtime>， sorted by the end time
        
        for(int[] interval : intervals){
            // 如果下一个meeting的开始时间晚于最早可以结束的会议（minheap.peek）, 意味着可以结束之前的一个会议室，而加入一个新的会议室，实际上会议室的数量是不变的，只是改变了timestamp
            // [那么就可以将之前结束的会议poll出去，将新的meeting推进minheap]
            if(!minheap.isEmpty() && interval[0] >= minheap.peek()[1] ){
                    minheap.poll();
            }
            // 如果下一个meeting开始时间要早于/等于最早结束的会议的结束时间，那就要新开一个会议室
            minheap.offer(interval);
        }
        
        return minheap.size();       
    }
}

