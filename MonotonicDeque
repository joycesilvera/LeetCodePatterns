import java.util.*;

public class MonotonicDeque {
    public static int longestSubarray(int[] nums, int limit) {
        Deque<Integer> decQ = new LinkedList<>();
        Deque<Integer> incQ = new LinkedList<>();

        int left = 0, maxLen = 0;

        for (int right = 0; right < nums.length; right++) {
            int num = nums[right];

            while (!decQ.isEmpty() && num > decQ.peekLast()) {
                decQ.pollLast();
            }
            decQ.add(num);

            while (!incQ.isEmpty() && num < incQ.peekLast()) {
                incQ.pollLast();
            }
            incQ.add(num);

            // Shrinking the window
            while (decQ.peekFirst() - incQ.peekFirst() > limit) {
                if (decQ.peekFirst() == nums[left]) {
                    decQ.pollFirst();
                }
                if (incQ.peekFirst() == nums[left]) {
                    incQ.pollFirst();
                }
                left++;
            }

            maxLen = Math.max(maxLen, right - left + 1);
        }

        return maxLen;
    }

    public static void main(String[] args) {
        int[] test1 = {8, 2, 4, 7};
        int limit1 = 4;
        System.out.println("Test 1: " + longestSubarray(test1, limit1)); // Expected: 2

        int[] test2 = {10, 1, 2, 4, 7, 2};
        int limit2 = 5;
        System.out.println("Test 2: " + longestSubarray(test2, limit2)); // Expected: 4

        int[] test3 = {4, 2, 2, 2, 4, 4, 2, 2};
        int limit3 = 0;
        System.out.println("Test 3: " + longestSubarray(test3, limit3)); // Expected: 3

        int[] test4 = {1, 5, 6, 7, 8, 10, 6, 5, 6};
        int limit4 = 4;
        System.out.println("Test 4: " + longestSubarray(test4, limit4)); // Expected: 5

        int[] test5 = {1, 2, 3, 4, 5};
        int limit5 = 10;
        System.out.println("Test 5: " + longestSubarray(test5, limit5)); // Expected: 5
    }
}
