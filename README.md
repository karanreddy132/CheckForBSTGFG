# CheckForBSTGFG
bool isBST(Node* root) 
    {
        // Your code here
        if(root->left==nullptr && root->right==nullptr){
            return true;
        }
        //minimum value of right subtree should be greater than current node value
        else if(root->left==nullptr){
            if(minNode(root->right)->data <= root->data)
                return false;
            else
                return isBST(root->right);
        }
        //maximum value of left subtree should be less than current node value
        else if(root->right==nullptr){
            if(maxNode(root->left)->data >= root->data)
                return false;
            else
                return isBST(root->left);
        }
        else{
            if(minNode(root->right)->data <= root->data || maxNode(root->left)->data >= root->data)
                return false;
            else
                return (isBST(root->left) && isBST(root->right));
        }
    }
    
    Node* maxNode(Node* r){
        if(r->right==nullptr)
            return r;
        return maxNode(r->right);
    }
    
    Node* minNode(Node* r){
        if(r->left==nullptr)
            return r;
        return minNode(r->left);
    }
