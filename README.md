# unique-pattern
unique pattern question solution
public class uniquePatterns {
    public static void main(String[] args) {
        int[] nums = { 1, 2, 1, 3, 4, 2, 3 };
        int maxPatternsLength = findUniquePattern(nums);
        System.out.println("Maximum unique patterns length: " + maxPatternsLength);
    }

    public static int findUniquePattern(int[] nums) {
        int n = nums.length;
        int[] freq = new int[101];
        int left = 0;
        int right = 0;
        int maxPatternsLength = 0;

        while (right < n) {
            int num = nums[right];
            freq[num]++;
            while (freq[num] > 1) {
                freq[nums[left]]--;
                left++;
            }
            maxPatternsLength = Math.max(maxPatternsLength, right - left + 1);
            right++;
        }
        return maxPatternsLength;
    }
}
