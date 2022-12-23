// 自己的解法，可惜超时了

class TimeMap {
    // create a HashMap<key, HashMap<timestamp, value>>
    HashMap<String, TreeMap<Integer, String>> map; 
    

    public TimeMap() {
        map = new HashMap<String, TreeMap<Integer, String>>();
    }
    
    public void set(String key, String value, int timestamp) {
        // create a treemap<timestamp, value>, sorting based on the timestamp
        
        if(!map.containsKey(key)){
            map.put(key, new TreeMap<Integer, String>());
        }
        // based on key to find its treeMap and insert (timestamp, value)
        TreeMap<Integer, String> subMap = map.get(key);
        subMap.put(timestamp, value);           
    }
    
    public String get(String key, int timestamp) {
        if(!map.containsKey(key)){
            return "";
        }
    // HashMap.get()
        TreeMap<Integer, String> cur = new TreeMap<Integer, String>();
        cur = map.get(key);   
    // search the timestamp, the target timestamp in the subMap should be equal to or just less than the given timestamp
    // get the key(timestamp) set, convert to an array   
        List<Integer> timeList = new ArrayList<Integer>(cur.keySet());
        int[] timeArray = new int[timeList.size()];
        for(int i = 0; i < timeArray.length; i++){
            timeArray[i] = timeList.get(i);
        }
        int left = 0;
        int right = timeArray.length;
        while(left < right){
           // int pivot = left + (right - left)/2;
            int pivot = (right + left)/2;          //注意
            if(timestamp >= timeArray[pivot]){
                left = pivot + 1;
            }else if(timestamp < timeArray[pivot]) {
                right = pivot;
            }
        }
        if(right == 0) return ""; 
        return map.get(key).get(timeArray[right - 1]);   
    }
}


// 思路：HashMap<key, treeMap<timestamp, value>>

/**
 * Your TimeMap object will be instantiated and called as such:
 * TimeMap obj = new TimeMap();
 * obj.set(key,value,timestamp);
 * String param_2 = obj.get(key,timestamp);
 */