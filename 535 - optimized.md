public class Codec {
    String alphabet = "0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ";
    HashMap<String, String> map = new HashMap<>();
    Random rand = new Random();
    String key = getRand();

    public String getRand(){
        StringBuilder randKey = new StringBuilder();
        for(int i = 0; i < 6; i ++){
            randKey.append(alphabet.charAt(rand.nextInt(62)));  // 随机产生[0, 62) 中的一个整数作为index
        }
        return randKey.toString();
    }

    // Encodes a URL to a shortened URL.
    public String encode(String longUrl) {
        // if hashCode collision happens, it will has a new random key 
        while(map.containsKey(key)){
            key = getRand();
        }
        map.put(key, longUrl);
        return "http://tinyurl.com/" + key;
    }

    // Decodes a shortened URL to its original URL.
    public String decode(String shortUrl) {
        return map.get(shortUrl.replace("http://tinyurl.com/", ""));
    }
}

// Your Codec object will be instantiated and called as such:
// Codec codec = new Codec();
// codec.decode(codec.encode(url));