## 42. Trapping Rain Water
```Java
class Solution {
    public int trap(int[] height) {
        //Time O(n), Space O(n)
        int[] maxLeft = new int[height.length];
        int[] maxRight = new int[height.length];
        int lMax = Integer.MIN_VALUE;
        int rMax = Integer.MIN_VALUE;
        int res = 0;
        
        for (int i = 0; i < height.length; i++) {
            if (height[i] > lMax) {
                maxLeft[i] = height[i];
                lMax = height[i];
            }
            else {
                maxLeft[i] = lMax;
            }
        }
        
        for (int i = height.length - 1; i >= 0; i--) {
            if (height[i] > rMax) {
                maxRight[i] = height[i];
                rMax = height[i];
            }
            else {
                maxRight[i] = rMax;
            }
        }
        for (int i = 0; i < maxLeft.length; i++) {
            res += Math.min(maxLeft[i], maxRight[i]) - height[i];
        }
        return res;
    }
}
```
