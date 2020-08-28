# Table of Contents:-

[TOC]





### 1). Build Binary Tree given Preorder and Inorder

https://www.youtube.com/watch?v=GeltTz3Z1rw

 inStart = inStart =0
 inEnd = inorder.size() - 1

  
      Node* builBTee(int preorder[], int inorder[], int preStart, int inStart, int inEnd) {
            if(inStart > inEnd || preStart > preorder.size()-1 ) 
               return NULL;
                
            Node* root = new Node(preorder[preStart]);
         
            int inorderIndex = 0;
            for(int i=inStart; i < inEnd; i++) {
                if(inorder[i] == preorder[preStart]) {
                   inorderIndex = i;
                   break; 
                }
            }
    
            root->left = buildBTree( preorder, inorder, preStart+1, inStart, inorderIndex-1);
            root->right = buildBTree( preorder, inorder,
                                      preStart + (inorderIndex - inStart) + 1,
                                      inorderIndex + 1, inEnd);
    
            return root;
    }



### 2). Build Binary Tree given Postorder and Inorder  

    postOrderindex = postOrder.size() - 1
    Start = 0
    End = inorder.size() - 1

https://www.youtube.com/watch?v=TblhNX9AQ3M
         

     Node* builBTee(int postorder[], int inorder[], int postOrderindex, int Start, int End)
     {
        if(Start > End || index < 0 || index > end ) 
           return NULL;
        
        Node* root = new Node(postorder[postOrderindex]);
         
        int inorderIndex = 0;
        for(int i= Start; i < End; i++) {
            if(inorder[i] == postorder[postOrderindex]) {
               inorderIndex = i;
               break; 
            }
        }
    
        current->left = buildBTree( postorder, inorder, 
                                    postOrderindex-(End-inorderIndex)-1, 
                                    inStart, inorderIndex - 1);
        current->right = buildBTree( postorder, inorder, 
                                     postOrderindex-1, 
                                     inorderIndex + 1, inEnd);
    
         return root;
    }     



### 3). Build Binary Tree given Postorder and PreOrder  

https://www.youtube.com/watch?v=3XYxGKeC_Ew         
         

    Node* builBTee(int preorder[], int postorder[], int preStart, int preEnd, int postStart, int postEnd)
    {
         if(preStart > preEnd ) 
            return NULL;    
         
         Node* root = new Node(preorder[preStart]);
       
         if(preStart == preEnd) 
            return root;
         
         int postIndex = postStart;
         while(post[postIndex] != preorder[preStart + 1]) {
              postIndex ++;
         }
    
         int len = (postIndex- postStart) + 1;
         
         current->left = buildBTree( preorder, postorder,
                                     preStart + 1, preStart + len, 
                                     postStart,postIndex );
         current->right = buildBTree( preorder, postorder, 
                                      preStart + len +1, preEnd, 
                                      postIndex+1, posEnd-1);
         return root;
    }     


### 4). Build Binary Search Tree given PreOrder traversal

<https://www.youtube.com/watch?v=9sw8RRsBw6s>

