public class SingleNumber {
    public static int singleNumber(int[] nums) {
        int result = 0;
        for (int num : nums) {
            result ^= num;  // XOR accumulates here
        }
        return result;
    }
    public static void main(String[] args) {
        int[] nums = {2, 3, 2, 4, 3};
        System.out.println("The single number is: " + singleNumber(nums));
    }
}

OUTPUT
4.
