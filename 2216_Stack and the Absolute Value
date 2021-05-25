#include <stdio.h>
#include <malloc.h>
#include <string.h>

typedef struct Node Node;
typedef struct Stack Stack;

Stack *createStack();

void push(Stack *stack, int item);
int pop(Stack *stack);
int isEmpty(Stack *stack);
int highestValue(int v, int nv);
int lowerValue(int v, int nv);
void updateHighestAndLowerValues(Stack *stack);

int setValue = 0;
int hValue = 0;
int lValue = 0;


int main() {
    char str[20];
    int value;

    Stack *stack = createStack();

    while (scanf("%s", str) != EOF) {
        if (strcmp(str, "push") == 0) {
            scanf("%d", &value);
            push(stack, value);

            if (setValue == 0) {
                setValue = 1;
                hValue = value;
                lValue = value;
                continue;
            }

            hValue = highestValue(hValue, value);
            lValue = lowerValue(lValue, value);
        } else if (strcmp(str, "pop") == 0) {
            printf("%d\n", pop(stack));
            updateHighestAndLowerValues(stack);
        } else if (strcmp(str, "abs") == 0) {
            printf("%d\n", hValue - lValue);
        }
    }

    return 0;
}


struct Node {
    int item;
    Node *nextNode;
};

struct Stack {
    Node *top;
};

Stack *createStack() {
    Stack *stack = malloc(sizeof(Stack));
    stack->top = NULL;
    return stack;
}

void push(Stack *stack, int item) {
    Node *newTop = malloc(sizeof(Node));
    newTop->item = item;
    newTop->nextNode = stack->top;
    stack->top = newTop;
}

int pop(Stack *stack) {
    if (!isEmpty(stack)) {
        int value = stack->top->item;
        stack->top = stack->top->nextNode;
        return value;
    }

    return 0;
}

int isEmpty(Stack *stack) {
    if (stack->top == NULL) {
        return 1;
    } else {
        return 0;
    }
}

int highestValue(int v, int nv) {
    if (v < nv) {
        return nv;
    } else {
        return v;
    }
}

int lowerValue(int v, int nv) {
    if (v < nv) {
        return v;
    } else {
        return nv;
    }
}

void updateHighestAndLowerValues(Stack *stack) {
    int value;
    setValue = 0;
    hValue = 0;
    lValue = 0;

    Node *n;

    for (n = stack->top; n != NULL; n = n->nextNode) {
        value = n->item;

        if (setValue == 0) {
            setValue = 1;
            hValue = value;
            lValue = value;
        } else {
            hValue = highestValue(hValue, value);
            lValue = lowerValue(lValue, value);
        }
    }
}
