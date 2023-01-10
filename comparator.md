Arrays.sort(nums, (a, b) -> a - b);    等同于   Arrays.sort(nums);            // 将数组nums按升序排序

Java的内置静态方法Arrays.sort()中，有 static <T> void sort(T[] nums, Comparator<? super T> c)这个方法；
此方法有两个输入参数，数组nums 和 比较器c;
可以通过自己定义比较器c，实现对sort排序规则的改变；sort()默认是对nums进行升序（从小到大）排序。

🌟 🌟  对整数型数组nums实现**从大到小（降序）**排序
Arrays.sort(nums, new Comparator<>(){
        public int compare(int a, int b){
                return b - a;
        }
});

或者用lambda表达，-> Arrays.sort(nums, (a, b) -> b - a);
🌟 以上的降序写法中，假设b为Integer.MIN_VALUE, a为正数时，计算a-b时会溢出，返回有误。
        _降序_推荐以下写法：
        Arrays.sort(nums, (a, b) -> Integer.compare(b, a));
        _升序_：
        Arrays.sort(nums, (a, b) -> Integer.compare(a, b));



理解：
（1）实现了Compareable接口的compare(a, b) 方法
（2）若a > b, 输出正数；若a < b, 输出负数；若 a = b, 输出0。 return a - b 
             -> 要从小到大，那么要a < b; return a - b 为负数；相当于false，表示不想调整顺序
             -> 要从小到大，那么要a > b; return a - b 为正数；相当于true，表示想调整顺序

-> 降序



-------------------
排序二维数组 int[][]
nums = int[n][2];    // 假定
Arrays.sort();
Arrays.sort(nums, new Comparator<int[]>(){
        **public int compare(int[] a, int[] b){
                if(a[0] == b[0]){               // 如果a和b第一个数一样大，那么比较第二个数，并从小到大排序
                        return a[1] - b[1];
                }else{                                 // 如果a和b的第一个数不一样大，那么就比较第一个数，从小到大排序
                        return a[0] - b[0];
                }
        }**
});



------------—
**默认为从小到大排序，用参数a减参数b。若需要从大到小排序，则用参数b减参数a。（同②，不一定是相减，从小到大排按正常思路，参数a大则返回正数；若要从大到小排，则按相反思路，参数a大则返回负数）
-----------**

if(o1.compareTo(o2) < 0){           // o1在o2之前， o1比o2小
    return ?;
}

// 要升序， 那么o1要比o2小；返回-1 (相当于false), 表示不想调整顺序
// 要降序， 那么o1要比o2大；返回1 (相当于true), 表示想调整顺序



🌟 --------------------------------—
PriorityQueue<Integer> heap = new PriorityQueue<>();    默认为小顶堆
PriorityQueue<Integer> heap = new PriorityQueue<>(Comparator.reverseOrder());    大顶堆

example:
- 1834  single-threaded CPU
