#### [面试题32 - III. 从上到下打印二叉树 III](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-iii-lcof/)

>  请实现一个函数按照之字形顺序打印二叉树，即第一行按照从左到右的顺序打印，第二层按照从右到左的顺序打印，第三行再按照从左到右的顺序打印，其他行以此类推。

```c++
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        queue<TreeNode*> temque;
        vector<vector<int>> ans;
        if (root == nullptr) return ans;
        temque.push(root);
        int isodd = 0;
        while (!temque.empty()) {
            deque<int> temdqu;
            int size = temque.size();
            isodd++;
            for (int i = 0; i < size; i++) {
                TreeNode* tem = temque.front();
                if (isodd % 2) {
                    temdqu.push_back(tem->val);
                } else {
                    temdqu.push_front(tem->val);
                }
                temque.pop();
                if (tem->left) {
                    temque.push(tem->left);
                }
                if (tem->right) {
                    temque.push(tem->right);
                }   
            }
            ans.push_back(vector<int>(temdqu.begin(), temdqu.end()));
        }
        return ans;
    }
};
```

