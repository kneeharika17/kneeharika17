## Hi there 👋

int* twoSum(int* nums, int numsSize, int target, int* returnSize) {
    int* result = (int*)malloc(2 * sizeof(int));
    *returnSize = 2;
    
    for (int i = 0; i < numsSize; i++) {
        for (int j = i + 1; j < numsSize; j++) {
            if (nums[i] + nums[j] == target) {
                result[0] = i;
                result[1] = j;
                return result;
            }
        }
    }
    
    result[0] = 0;
    result[1] = 1;
    return result;
}

bool isPalindrome(int x) {
double rev=0, rem, orignal=x;
    
    
        while(x>0)
        {
            rem = x % 10;
            rev = rev * 10 + rem;
            x/=10;
        }

        if(rev == orignal)
            return true;
        
         else
       return false;    
}

int romanToInt(char * s)
{
    int t['X' + 1] = {
        ['I'] = 1,
        ['V'] = 5,
        ['X'] = 10,
        ['L'] = 50,
        ['C'] = 100,
        ['D'] = 500,
        ['M'] = 1000,
    };
    int res = 0;
    for (int i = 0; s[i]; i++) {
        if (t[s[i]] < t[s[i+1]])
            res -= t[s[i]];
        else
            res += t[s[i]];
    }
    return res;
}

char* prefix = strs[0]; // take the first string to be the longest possible prefix
    int lengthcurrent = strlen(prefix); // only do this once for extra speed
    for (int i = 1; i < strsSize; i++) {
        char* string = strs[i];
        for (int j = 0; j < lengthcurrent; j++) {
            if (string[j] != prefix[j]) {
                prefix[j] = '\0'; // Null terminater trick
                lengthcurrent = j;
            }
        }
    }
    return prefix;
}

int len =strlen(s);
    char stack[len];
    int top = -1;
    for(int i=0;i<len;i++){
        if(s[i]=='(' || s[i] == '{' || s[i] == '[' ){
            stack[++top] = s[i];
        }else{
            if(top == -1 ||( s[i]==')'&&stack[top] != '(')||(s[i]=='}'&&stack[top] != '{')||(s[i]==']'&&stack[top]!='[')){
                return false;
            } 
            top--;
        } 
    }  
    return top == -1; 
}

void insert (struct ListNode** head,int num){
    struct ListNode* new = (struct ListNode*)malloc(sizeof(struct ListNode));
    new->val = num;
    new->next = NULL;

    if(*head == NULL){
        *head = new;
    }else{
        struct ListNode* temp = *head;
        while(temp->next != NULL){
            temp =temp->next;
        }
        temp->next = new;
    }
}

struct ListNode* mergeTwoLists(struct ListNode* list1, struct ListNode* list2) {
    struct ListNode* head = NULL;
    while(list1 != NULL && list2 != NULL){
        if(list1->val < list2->val){
            insert(&head,list1->val);
            list1 = list1->next;
        }else{
            insert(&head,list2->val);
            list2 = list2->next;
        }
    }
    while(list1 != NULL){
        insert(&head,list1->val);
        list1 = list1->next;
    }
    while(list2 != NULL){
        insert(&head,list2->val);
        list2 = list2->next;
    }

    return head;
}

int removeDuplicates(int* nums, int numsSize) {
   int c=1;
  for(int i=0;i<numsSize;i++){
    if( nums[i]!=nums[c-1]){
        nums[c]=nums[i];
        c++;
    }
  }
  return c;
} 

int removeElement(int* a, int n, int val) {
    int c=0,t;
    for(int i=0;i<n;i++){
        if(a[i]==val){
            c++;
        }
        else{a[i-c]=a[i];}}
        return (n-c);
}

int strStr(char* str, char* substr) {
    int substr_len = 0;
    while (substr[substr_len] != '\0') {
        substr_len++;
    }

    int i, j;

    for (i = 0; str[i] != '\0'; i++) {
        for (j = 0; j < substr_len && str[i + j] == substr[j]; j++)
            ;
        if (j == substr_len) {
            return i;
        }
    }

    return -1;
}

int searchInsert(int* nums, int numsSize, int target) {
  int low = 0;
    int high = numsSize - 1;

    while (low <= high) {
        int mid = low + (high - low) / 2;

        if (nums[mid] == target) {
            return mid; 
        }
        if (nums[mid] < target) {
            low = mid + 1;  
        } else {
            high = mid - 1; 
        }
    }
    
    return low;  
}

int lengthOfLastWord(char* s) {
    int length=0,i,wordcounter=0;
    for(i=0;s[i]!='\0';i++)
    {
        length++;
    }
    for(i=(length-1);s[i]==' ';i--)
    {
        if(s[i]==' ')
        s[i]='\0';
    }
    for(i=0;s[i]!='\0';i++)
    {
        if(s[i]==' ')
        {
            wordcounter=0;
            continue;
        }
        else
        {
            wordcounter++;
        }
    }
    return wordcounter;
}

int* plusOne(int* digits, int digitsSize, int* returnSize) {
  *returnSize = digitsSize;
    int *plusOne = malloc(digitsSize * sizeof(int));
    if (plusOne == NULL)
        return (NULL);
    for (int i = 0; i < digitsSize; i++)
        plusOne[i] = digits[i];
    
    plusOne[digitsSize - 1]++;
    for (int i = digitsSize - 1; i - 1 >= 0; i--)
        if (plusOne[i] == 10) {
            plusOne[i] = 0;
            plusOne[i - 1]++;
        }

    if (plusOne[0] == 10) {
        (*returnSize)++;
        plusOne = realloc(plusOne, *returnSize * sizeof(int));
        if (plusOne == NULL)
            return (NULL);
        memmove(plusOne + 1, plusOne, digitsSize * sizeof(int));
        plusOne[0] = 1;
        plusOne[1] = 0;
    }
    return (plusOne);  
}

char * addBinary(char * a, char * b){
    int sizeA = strlen(a);
    int sizeB = strlen(b);
    int sizeOutput = (sizeA > sizeB ? sizeA : sizeB) + 1;
    char * output = (char *)malloc(sizeOutput + 1);
    int sum = 0;
    
    output[sizeOutput] = '\0';
    
    while(sizeA > 0 || sizeB > 0 || sum > 0) {
        
        if(sizeA > 0) {
            sum += a[--sizeA] - '0';
        }
        if(sizeB > 0) {
            sum += b[--sizeB] - '0';
        }
        output[--sizeOutput] = sum % 2 + '0';
        sum /= 2;
    }
    return output + sizeOutput;   
}

int mySqrt(int x) {
  if(x==0||x==1){
        return x;
    }
    for(long long int i=1;i<=x;i++){
        if(i*i>x){
            return i-1;
        }

    }
return 0;  
}

struct ListNode* deleteDuplicates(struct ListNode* head) {
    struct ListNode* temp=head;
    while (temp&&temp->next)
    {
        if (temp->next->val==temp->val)
        {
            temp->next=temp->next->next;
            continue;
        }
        temp=temp->next;
    }
    return head;
}

int climbStairs(int n) {
   if (n == 1) return 1;

    int dp[n + 1]; // Array to store results
    dp[1] = 1;
    dp[2] = 2;

    for (int i = 3; i <= n; i++) {
        dp[i] = dp[i - 1] + dp[i - 2];
    }

    return dp[n];
}

void merge(int* nums1, int nums1Size, int m, int* nums2, int nums2Size, int n) {
    if(n == 0)return;
    int len1 = nums1Size;
    int end_idx = len1-1;
    while(n > 0 && m > 0){
        if(nums2[n-1] >= nums1[m-1]){
        nums1[end_idx] = nums2[n-1];
        n--;
        }else{
            nums1[end_idx] = nums1[m-1];
            m--;
        }
        end_idx--;
    }
    while (n > 0) {
        nums1[end_idx] = nums2[n-1];
        n--;
        end_idx--;
    }
}

int i=0;
int arr[101]={0};
void inorder(struct TreeNode* s)
{
    if(s!=NULL)
    {
        inorder(s->left);
        arr[i++]=s->val;
        inorder(s->right);
    }
}
int* inorderTraversal(struct TreeNode* root, int* returnSize){
    inorder(root);
    int* ans=malloc(i*sizeof(int));
    for(int j=0;j<i;j++) ans[j]=arr[j];
    *(returnSize)=i;
    i=0;
    return ans;
}

bool isSameTree(struct TreeNode* p, struct TreeNode* q) {
    if (p == NULL && q == NULL) return true;
    if (p == NULL || q == NULL) return false;
    if (p->val != q->val) return false;
    return isSameTree(p->left, q->left) && isSameTree(p->right, q->right);
}

bool isSymmetricHelp(struct TreeNode* left, struct TreeNode* right) {
    if (left == NULL || right == NULL) {
        return left == right;
    }
    if (left->val != right->val) {
        return false;
    }

    return isSymmetricHelp(left->left, right->right) && isSymmetricHelp(left->right, right->left);
}

bool isSymmetric(struct TreeNode* root) {
    return root == NULL || isSymmetricHelp(root->left, root->right);
}

int max(int a, int b) { return (a > b) ? a : b; }
int depth(struct TreeNode* root) {
    if(root==NULL)
    {
        return 0;
    }
    return 1+max(depth(root->left),depth(root->right));
}
int maxDepth(struct TreeNode* root) { return depth(root); }

struct TreeNode* createNewNode(int val) {
    struct TreeNode* newNode = (struct TreeNode*)malloc(sizeof(struct TreeNode));
    newNode->val = val;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

struct TreeNode* res(int* nums, int l, int r) {
    if (l > r)
        return NULL;
    int mid = l + (r - l) / 2; 
    struct TreeNode* node = createNewNode(nums[mid]);
    node->left = res(nums, l, mid - 1);
    node->right = res(nums, mid + 1, r);
    return node;
}

struct TreeNode* sortedArrayToBST(int* nums, int numsSize) {
    return res(nums, 0, numsSize - 1);
}

int depth(struct TreeNode *root);

bool isBalanced(struct TreeNode *root) {
    if (root == NULL)
        return true;
        
    return isBalanced(root->left) && 
           isBalanced(root->right) &&
           !(abs(depth(root->left) - depth(root->right)) > 1);
}

int depth(struct TreeNode *root) {
    if (root == NULL)
        return 0;
        
    return fmax(depth(root->left), depth(root->right)) + 1;
}

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     struct TreeNode *left;
 *     struct TreeNode *right;
 * };
 */
int minDepth(struct TreeNode* root){
    int x,y;
    if(root == NULL)
        return 0;
    else{
    x=minDepth(root->left);
    y=minDepth(root->right);
    if ((x==0) ^ (y==0)) 
    return (x>y?x:y)+1 ;
    if(x > y)
    return y + 1;
    else
    return x + 1;
    }

}

bool hasPathSum(struct TreeNode* root, int targetSum) {
    if (!root)
        return false;

    if (!root->left && !root->right)
        return root->val == targetSum;

    targetSum -= root->val;
    return hasPathSum(root->left, targetSum) || hasPathSum(root->right, targetSum);
}

int** generate(int numRows, int* returnSize, int** returnColumnSizes){
    *returnSize = numRows;
    int **output = calloc(1, sizeof(int *[numRows]));
    *returnColumnSizes = calloc(1, sizeof(int [numRows]));
    
    //Allocate memory for the whole triangle
    for (int i=0; i<numRows; i++) {
        (*returnColumnSizes)[i] = i + 1;
        output[i] = calloc(1, sizeof(int [i + 1]));
    }
    
    //the first row will always be 1
    output[0][0] = 1;
    
    for (int i=1; i<numRows; i++) {
        output[i][0] = 1;
        for (int j=1; j<i; j++) {
            output[i][j] = output[i-1][j-1] + output[i-1][j];
        }
        output[i][i] = 1;
    }
    return output;
}

int maxProfit(int* prices, int pricesSize) {
    // If we are selling on one day then the buying rate should be the minimum
    int min = INT_MAX;
    int ans = 0;

    for (int i = 1; i < pricesSize; i++) {
        min = (min < prices[i - 1]) ? min : prices[i - 1];
        int cpro = prices[i] - min;
        ans = (ans > cpro) ? ans : cpro;
    }

    return ans;
}
int isAlphanum(char c){
    return (c >= 'a' && c <= 'z') || (c >= 'A' && c <= 'Z') || (c >= '0' && c <= '9'); 
}

int convertAlphaLower(char c){
    return (c >= 'A' && c <= 'Z') ? c + 32 : c;
}

int isPalindrome(char* s) {
    int l, r;

    r = strlen(s) - 1;

    l = 0;
    while (l < r){
        if(isAlphanum(s[l])){

            if(isAlphanum(s[r])){
                
                if (convertAlphaLower(s[l]) != convertAlphaLower(s[r])){

                    return 0;
                }

                l++;
                r--;
            }
            else 
                r--;
        }
        else 
            l++;
    }

    return (1);
}


