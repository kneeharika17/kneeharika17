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
