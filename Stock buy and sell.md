### Stock Buy and Sell
🔸 Example:
Input: prices = [7, 1, 5, 3, 6, 4]

Output: 5

Explanation: Buy on day 2 (price = 1), sell on day 5 (price = 6) → profit = 6 - 1 = 5
```
public class StockBuySell {
    public static int maxProfit(int[] prices) {
        int maxProfit = 0;
        int bestBuy = prices[0];

        for (int i = 1; i < prices.length; i++) {
            if (prices[i] > bestBuy) {
                maxProfit = Math.max(maxProfit, prices[i] - bestBuy);
            } else {
                bestBuy = Math.min(bestBuy, prices[i]);
            }
        }
        return maxProfit;
    }

    public static void main(String[] args) {
        int[] prices = {7, 1, 5, 3, 6, 4};
        int profit = maxProfit(prices);
        System.out.println("Max Profit : " + profit);
    }
}
```

**Time Complexity:** `O(n)` – single pass through array
**Space Complexity:** `O(1)` – only using two variables

For `{7, 1, 5, 3, 6, 4}` → **Max Profit = 5** (buy at 1, sell at 6).

If you want, I can also give you a **two-pointer version** for the same problem. That’s another neat way to think about it.
