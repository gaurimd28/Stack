#include <iostream>

#include <cctype>

#include <algorithm>

using namespace std;

// Node class for singly linked list

class Node {

public:

    char data;

    Node* next;

    Node(char value) {

        data = value;

        next = NULL;

    }

};

// Stack using singly linked list

class Stack {

private:

    Node* top;

public:

    Stack() { top = NULL; }

    void push(char x) {

        Node* temp = new Node(x);

        temp->next = top;

        top = temp;

    }

    char pop() {

        if (isEmpty()) return '\0';

        char x = top->data;

        Node* temp = top;

        top = top->next;

        delete temp;

        return x;

    }

    char peek() {

        return (top) ? top->data : '\0';

    }

    bool isEmpty() {

        return (top == NULL);

    }

};

// Helper functions

int precedence(char op) {

    if (op == '^') return 3;

    if (op == '*' || op == '/' || op == '%') return 2;

    if (op == '+' || op == '-') return 1;

    return 0;

}

bool isOperator(char c) {

    return (c == '+' || c == '-' || c == '*' || c == '/' || c == '^' || c == '%');

}

string infixToPostfix(string infix) {

    Stack s;

    string postfix = "";

    for (char& ch : infix) {

        if (isalnum(ch)) {

            postfix += ch;

        }

        else if (ch == '(') {

            s.push(ch);

        }

        else if (ch == ')') {

            while (!s.isEmpty() && s.peek() != '(')

                postfix += s.pop();

            s.pop(); // pop '('

        }

        else if (isOperator(ch)) {

            while (!s.isEmpty() && precedence(ch) <= precedence(s.peek()))

                postfix += s.pop();

            s.push(ch);

        }

    }

    while (!s.isEmpty()) {

        postfix += s.pop();

    }

    return postfix;

}

string infixToPrefix(string infix) {

    reverse(infix.begin(), infix.end());

    for (int i = 0; i < infix.length(); i++) {

        if (infix[i] == '(') infix[i] = ')';

        else if (infix[i] == ')') infix[i] = '(';

    }

    string postfix = infixToPostfix(infix);

    reverse(postfix.begin(), postfix.end());

    return postfix;

}

// Main function to test

int main() {

    string infix;

    cout << "Enter infix expression: ";

    cin >> infix;

    string postfix = infixToPostfix(infix);

    string prefix = infixToPrefix(infix);

    cout << "Postfix: " << postfix << endl;

    cout << "Prefix: " << prefix << endl;

    return 0;

}