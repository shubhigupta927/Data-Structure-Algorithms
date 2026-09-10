# Implement 'N' Stacks In An Array
```cpp
class NStack
{
public:
    int *arr;
    int *top;
    int *next;
    int freeSpot;
    NStack(int N, int S)
    {
        arr=new int[S];
        top=new int[N];
        next=new int[S];

        for(int i=0; i<N; i++){
            top[i]=-1;
        }

        for(int i=0; i<S-1; i++){
            next[i]=i+1;
        }
        next[S-1]=-1;        

        freeSpot=0;
    }

    // Pushes 'X' into the Mth stack. Returns true if it gets pushed into the stack, and false otherwise.
    bool push(int x, int m)
    {
        //check for overflow
        if (freeSpot==-1){
            return false;
        }
        int index = freeSpot;     //find index

        freeSpot=next[index];     //update freeSpot

        arr[index]=x;             //insert in array

        next[index]=top[m-1];     //update next for index
        
        top[m-1]=index;           //update top of Mth stack
        return true;
    }

    // Pops top element from Mth Stack. Returns -1 if the stack is empty, otherwise returns the popped element.
    int pop(int m)
    {
        //check for underflow
        if(top[m-1]==-1){
            return -1;
        }
        
        int deletedIndex=top[m-1];
        int result = arr[deletedIndex];

        top[m-1] = next[deletedIndex];

        next[deletedIndex]=freeSpot;
        freeSpot=deletedIndex;

        return result;

    }
};
```