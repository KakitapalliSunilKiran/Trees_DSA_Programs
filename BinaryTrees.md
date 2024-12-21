# Trees_DSA_Programs
Trees_DSA_Programs
Today we are going to see 4 codes

1. Preorder 
2. Inorder
3. Post Order Traversal
4. Level Order Traversal
root , left , right

Recursion : 
  calling method itself is called recursion

preoder :
   Recursion 
   Iterative approach (using stack)
Inorder : 
   Recursion
   Iterative approach (Using stack) 
   
    intuition : 
             1.go left ,
             2.in this process null will come ,
             3.pop the last element, 
             4. with that go right

Post Order : 
   Recursion  (done)
    Iterative approach (Using stack) 

Level order traversal
    Recursion -----------> pending
    Iterative approach Using Queue (done)
==============================================
Recursive approaches of Inorder , preorder , postorder
public void inorderTraversal(TreeNode root) {
        if (root != null) {
            inorderTraversal(root.left);  // Traverse left subtree
            System.out.print(root.val + " "); // Visit root
            inorderTraversal(root.right); // Traverse right subtree
  }
-----------------------------------------------
   public void preorderTraversal(TreeNode root) {
        if (root != null) {
            System.out.print(root.val + " "); // Visit root
            preorderTraversal(root.left);  // Traverse left subtree
            preorderTraversal(root.right); // Traverse right subtree
        }
  }
---------------------------------------------------------
        public void postorderTraversal(TreeNode root) {
        if (root != null) {
            postorderTraversal(root.left);  // Traverse left subtree
            postorderTraversal(root.right); // Traverse right subtree
            System.out.print(root.val + " "); // Visit root
        }
    }
    -----------------------------------------------------
//Level Order traversal Iterative approach
class Solution {
    List<Integer> preorder=new ArrayList<>();
    public List<Integer> preorderTraversal(TreeNode root) {
        if(root==null)
        return new ArrayList<>();
        Stack<TreeNode> st=new Stack<>();
        st.push(root);
        while(!st.isEmpty()){
            root=st.pop();
            preorder.add(root.val);
            if(root.right!=null){
                st.add(root.right);
            }
            if(root.left!=null){
                st.add(root.left);
            }
        }
        return preorder;     
    }
}
===========================================
//Level order traversal Recursive approach
void printCurrentLevel(struct Node* root, int level) {
    if (root == NULL)
        return;
    if (level == 1)
        printf("%d ", root->data);
    else if (level > 1) {
        printCurrentLevel(root->left, level - 1);
        printCurrentLevel(root->right, level - 1);
    }
}
==========================================
//inorder iterative approach
 ArrayList<Integer> inOrder(Node root) {   
        ArrayList<Integer> in=new ArrayList<>();
        Stack<Node> st=new Stack<>();
        while(true){
            if(root!=null){
                st.add(root);
                root=root.left;
            }else{
                if(st.isEmpty()){
                    break;
                }
               root=st.pop();
                in.add(root.data);
                root=root.right;
            }
        }
        return in;     
    }
==============================================================
// Iterative approach postorder traversal of the tree.
class Solution {
    ArrayList<Integer> al=new ArrayList<>();
    ArrayList<Integer> postOrder(Node root) {
        // Your code goes here
       Stack<Node> st1=new Stack<>();
       ArrayList<Integer> al=new ArrayList<>();
       st1.add(root);
       while(!st1.isEmpty()){
           Node temp=st1.pop();
           al.add(temp.data);
           if(temp.left!=null){
               st1.add(temp.left);
           }
           if(temp.right!=null){
               st1.add(temp.right);
           }
       }
       Collections.reverse(al);
       return al;
    }  
}
===================================================
   // Function to compute the height of a tree.
    static int height(Node root) {    
        // Base case: tree is empty
        if (root == null)
            return 0;
        // If tree is not empty then height = 1 +
        // max of left height and right heights
        return 1 + Math.max(height(root.left), height(root.right));
    }
=================================================================
1. Count no of nodes in a binary tree
2. diameter of tree (all possible ways)
3. Balanced tree or not

https://leetcode.com/problems/count-complete-tree-nodes/submissions/1478608614/

class Solution {
    public int countNodes(TreeNode root) {
        if(root==null)
        return 0;
        int lftcount=countNodes(root.left); //1
        int rhtcount=countNodes(root.right);
        return 1+lftcount+rhtcount;
    }
}
=========================================================
//Diameter of the tree
Longest possible path across binary is called diameter
class Solution {
    int max=0;
    int height(TreeNode root){
        if(root==null){
            return 0;
        }
        int l=height(root.left);
        int r=height(root.right);
        return 1+Math.max(l,r);
    }
    public int diameterOfBinaryTree(TreeNode root) {
        diameter(root);
        return max;
    }
    void diameter(TreeNode root){
        if(root==null)
        return;
        int l=height(root.left);
        int r=height(root.right);
       max=Math.max(max,l+r);
       diameter(root.left);
       diameter(root.right);
    }
}
//Time complexity of this code 0(n^2)
//I want 0(n) solution
=============================================
//Optimized code for Diameter of the tree :
class Solution {
    int max=0;
    int height(TreeNode root){
        if(root==null){
            return 0;
        }
        int l=height(root.left);
        int r=height(root.right);
        max=Math.max(l+r,max);
        return 1+Math.max(l,r);
    }
    public int diameterOfBinaryTree(TreeNode root) {
        height(root);
        return max;
    }  
}
===============================================================
 //Check for Same Trees
    public boolean isSameTree(TreeNode p, TreeNode q) {
        if(p==null || q==null){
            return p==q;
        }
        boolean check1= (p.val==q.val);
        boolean check2= isSameTree(p.left,q.left); 
        boolean check3= isSameTree(p.right,q.right);
        if(check1==false || check2==false ||check3==false){
            return false;
        }else{
            return true;
        }    
    }
=================================================================
//Check for Symmertic Tree
  public boolean isSymmetric(TreeNode root) {
       return isSym(root.left,root.right);
    }
    boolean isSym(TreeNode lft,TreeNode rht){
        if(lft==null && rht==null){
            return true;
        }
         if(lft==null || rht==null){
            return false;
        }
        boolean check1= (lft.val==rht.val);
        boolean check2= isSym(lft.left,rht.right);
        boolean check3=isSym(lft.right,rht.left);
        if(check1 ==true && check2==true && check3==true){
            return true;
        }else{
            return false;
        }
    }
=============================================================
//To calculate Maximum sum path
   int max=Integer.MIN_VALUE;
    int findMaxSum(Node node)
    {
        calculateMax(node);
        return max;
    }
    int calculateMax(Node node){
        if(node==null)
        return 0;
        int lval=Math.max(0,calculateMax(node.left)); //2
         int rval=Math.max(0,calculateMax(node.right));
          max=Math.max(max,node.data+lval+rval);
         return node.data+Math.max(lval,rval);
    }
===============================================================
//ZigZag Level order traversal
class Solution {
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
         List<List<Integer>> result=new ArrayList<>();
         if(root==null){
            return result;
         }
         Queue<TreeNode> queue=new LinkedList<>();
         boolean flag=false;
         queue.add(root);
         int index=-1;
         while(!queue.isEmpty()){
            int size=queue.size(); //2
            ArrayList<Integer> al=new ArrayList<>(); 
            for(int i=0;i<size;i++){  
                TreeNode node =queue.poll();
               
                  if (flag) {
                    al.add(0, node.val);  // Add to the front for right-to-left traversal
                } else {
                    al.add(node.val);  // Add to the back for left-to-right traversal
                }
               if(node.left!=null){
                queue.add(node.left);
               }
                if(node.right!=null){
                    queue.add(node.right);
                }  
            }
            flag=!flag;
            result.add(al);

         }
         return result;
    }
}
=========================================================================
//Left View of the binary tree
class Solution {
    // Function to return list containing elements of left view of binary tree.
    ArrayList<Integer> leftView(Node root) {
        // code here
        ArrayList<Integer> al=new ArrayList<>();
         if(root==null){
            return new ArrayList<>();
         }
         Queue<Node> queue=new LinkedList<>();
         boolean flag=false;
         queue.add(root);
         int index=-1;
         while(!queue.isEmpty()){
            int size=queue.size();
           // ArrayList<Integer> al=new ArrayList<>();
            for(int i=0;i<=0;i++){
                Node node =queue.poll();
                if(i==0){
                    al.add(node.data);
                }
               if(node.left!=null){
                queue.add(node.left);
               }
                if(node.right!=null){
                    queue.add(node.right);
                }  
            }
           
         }
         return al;
   }
}
==================================================================
//  right view of binary tree.
class Solution {
    ArrayList<Integer> rightView(Node root) {
        // add code here.
         ArrayList<Integer> al=new ArrayList<>();
        // code here
          if(root==null){
            return new ArrayList<>();
         }
         Queue<Node> queue=new LinkedList<>();
         boolean flag=false;
         queue.add(root);
         while(!queue.isEmpty()){
            int size=queue.size(); //2
          //  ArrayList<Integer> al=new ArrayList<>(); 
            for(int i=0;i<size;i++){  
                Node node =queue.poll();
                if(i==size-1)
                  al.add(node.data);
               
                if(node.left!=null){
                queue.add(node.left);
               }
                if(node.right!=null){
                    queue.add(node.right);
                }  
            }          
         }
         return al;
    }
}
===============================================================




