## Binary Tree

### DFS(深度优先搜索)

#### 问题分类
前序、中序、后序遍历三种

#### 解法
递归法：
迭代法：使用stack，三种遍历的第一个内部循环都是只入栈左节点
后序遍历迭代法：需要记住前一个处理过的元素指针prev，再次出栈时检测右子树是否prev相同，避免重复处理左子树进入无限循环

模板如下
```
p = root
for p != nil || len(stack) != 0 {
  for p != nil {
    stack = append(stack)
    p = p.Left
  }
  
  top = stack[len(stack) - 1]
  stack = stack[:len(stack) - 1]
  if top.Right != nil {
    p = top.Right
  }
}
```

### BFS(广度优先搜索)

#### 问题分类
层次遍历、网格遍历、网格的最短路径

#### 解法
递归法：
迭代法：使用queue，每次左右子树都入队，第一个内循环把每次循环初期queue的全部元素都出队处理完毕，期间逐个入队当前层级的下一层级


### BFS和DFS对比
1. DFS比BFS代码简捷，实际使用场景多
2. BFS额外空间取决于O（w）w为树的最大宽度，DFS额外空间取决于O（h）h为树的最大深度。因此，当树更平衡时，BFS消耗空间多；当树更不平衡时，DFS消耗空间多
3. BFS从根节点开始访问节点，DFS从叶子节点开始。如果搜索更靠近根节点的东西使用BFS，搜索更靠近叶节点东西则用DFS



