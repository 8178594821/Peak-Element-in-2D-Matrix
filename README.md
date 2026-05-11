# Peak-Element-in-2D-Matrix
🚀 Approach
We use Binary Search on columns:

1. Pick middle column
2. Find maximum element in that column
3. Compare with left & right neighbors
4. Move accordingly

⏱ Complexity
Time: O(m log n)  
Space: O(1)

 💻 Code

class Solution {
    public int[] findPeakGrid(int[][] mat) {
        int m = mat.length;
        int n = mat[0].length;

        int left = 0;
        int right = n - 1;

        while (left <= right) {
            int mid = (left + right) / 2;

            int maxRow = 0;
            for (int i = 0; i < m; i++) {
                if (mat[i][mid] > mat[maxRow][mid]) {
                    maxRow = i;
                }
            }
            int leftVal = (mid - 1 >= 0) ? mat[maxRow][mid - 1] : -1;
            int rightVal = (mid + 1 < n) ? mat[maxRow][mid + 1] : -1;

            if (mat[maxRow][mid] > leftVal && mat[maxRow][mid] > rightVal) {
                return new int[]{maxRow, mid};
            }
            else if (leftVal > mat[maxRow][mid]) {
                right = mid - 1;  
            } else {
                left = mid + 1;    
            }
        }
        return new int[]{-1, -1}; 
    }
}

Input:
[[1,4],
[3,2]]

Output:
[0,1] or [1,0]

🔥 Pro Tip

👉 Always remember:
- **1D peak → binary search**
- **2D peak → binary search on column**

⭐ If you like this follow more such problem of DSA.
