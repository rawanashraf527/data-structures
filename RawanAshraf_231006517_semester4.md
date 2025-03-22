# Data Structures using C++
## Fork this repositry and update your readme file to including your name, id and year.
#rawan ashraf, 231006517, semester 4

##singly linked list sorted in ascending order: 
------------------------------------------------
#include <iostream>
struct Node {
    int data;
    Node* next;

    Node(int val) : data(val), next(nullptr) {} //constructor
};

void insert(Node*& head, int value) {
    Node* newNode = new Node(value);

//1st case
    if (head == nullptr || value < head->data) {
        newNode->next = head;
        head = newNode;
    }
    //2nd case
    else {
        Node* current = head;
        while (current->next != nullptr && current->next->data < value) {
            current = current->next;
        }
        newNode->next = current->next;
        current->next = newNode;
    }
}

void printList(Node* head) {
    Node* current = head;
    while (current != nullptr) {
        std::cout << current->data << " -> ";
        current = current->next;
    }
    std::cout << "nullptr" << std::endl;
}

int main() {
    Node* head = nullptr; 

    insert(head, 54);
    insert(head, 32);
    insert(head, 81);
    insert(head, 13);
    insert(head, 60);

    printList(head);

    return 0;
}
------------------------------------------------------------------------------------------------
##doubly linked list sorted in ascending order:
-------------------------------------------------
#include <iostream>

struct Node {
    int data;
    Node* next;
    Node* prev;

    Node(int val) : data(val), next(nullptr), prev(nullptr) {}
};

void insert(Node*& head, int value) {
    Node* newNode = new Node(value);
    if (head == nullptr) {
        head = newNode;
    }
    else if (value < head->data) {
        newNode->next = head;
        head->prev = newNode;
        head = newNode;
    }
    else {
        Node* current = head;
        while (current->next != nullptr && current->next->data < value) {
            current = current->next;
        }
        newNode->next = current->next;
        if (current->next != nullptr) {
            current->next->prev = newNode;
        }
        current->next = newNode;
        newNode->prev = current;
    }
}

void print(Node* head) {
    Node* current = head;
    while (current != nullptr) {
        std::cout << current->data << " -> ";
        current = current->next;
    }
    std::cout << "nullptr" << std::endl;
}

int main() {
    Node* head = nullptr; 
    insert(head, 76);
    insert(head, 9);
    insert(head, 35);
    insert(head, 98);
    insert(head, 74);

    
    print(head);

    

    return 0;
}
---------------------------------------------------------------------------------------
##the part to add in the "make null" function:
-------------------------------------------------
void Destroy()
{
    Node* current = head; 
    while (current != nullptr) {
        Node* temp = current; 
        current = current->next; 
        delete temp; 
    }
    head = nullptr; 
    tail = nullptr; 
    counter = 0;    
}
