
# Priority Queue


1. Top K frequent words: https://leetcode.com/problems/top-k-frequent-words/

```java
class Solution {
    public List<String> topKFrequent(String[] words, int k) {
        List<String> rst = new ArrayList<>();
        if (words == null || words.length == 0) {
            return rst;
        }

        Map<String, Integer> map = new HashMap<String, Integer>();
        for (String s : words) {
            map.put(s, map.getOrDefault(s, 0) + 1);
        }

        PriorityQueue<Map.Entry<String, Integer>> maxHeap = new PriorityQueue<>(k,
                (a, b) -> a.getValue() != b.getValue() ? b.getValue() - a.getValue()
                        : a.getKey().compareTo(b.getKey()));
        for (Map.Entry<String, Integer> set : map.entrySet()) {
            maxHeap.add(set);
        }

        while (k > 0) {
            rst.add(maxHeap.poll().getKey());
            k--;
        }
        return rst;
    }
}
```

2. Kth Largest Element in a Stream: https://leetcode.com/problems/kth-largest-element-in-a-stream/

```java
class KthLargest {

    private PriorityQueue<Integer> pq;
    private int k;

    public KthLargest(int k, int[] nums) {
        this.k = k;
        pq = new PriorityQueue<>();

        for (int num : nums) {
            pq.add(Integer.valueOf(num));

            if (pq.size() > k) pq.poll();
        }
    }

    public int add(int val) {
        pq.add(val);

        if (pq.size() > k) pq.poll();
        return pq.peek().intValue();
    }
}
```

3. Top K Frequent Elements: https://leetcode.com/problems/top-k-frequent-elements/description/

```java
public class TopKFrequentElement {
    public int[] topKFrequent(int[] nums, int k) {
        Map<Integer, Integer> map = new HashMap<>();

        for (int num : nums) {
            map.put(Integer.valueOf(num), map.getOrDefault(num, 0) + 1);
        }

        PriorityQueue<Map.Entry<Integer, Integer>> pq = new PriorityQueue<>(k, (a, b) -> b.getValue() - a.getValue());

        for (Map.Entry<Integer, Integer> set : map.entrySet()) {
            pq.add(set);
        }

        List<Integer> res = new ArrayList<>();

        while (k > 0) {
            res.add(pq.poll().getKey());
            k--;
        }

        return res.stream().mapToInt(Integer::intValue).toArray();
    }
}
```