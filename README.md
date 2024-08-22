# Binary-tree-using-array
#include <stdio.h>
int binarySearch(int arr[], int size, int target) {
 int left = 0;
 int right = size - 1;
 while (left <= right) {
 int mid = left + (right - left) / 2;
 if (arr[mid] == target) {
 return mid; 
 }
 if (arr[mid] < target) {
 left = mid + 1;
 }
 else {
 right = mid - 1;
 }
 }
 return -1;
}
int main() {
 int arr[] = {2, 4, 6, 8, 10, 12, 14, 16, 18, 20};
 int size = sizeof(arr) / sizeof(arr[0]);
 int target = 1;
 int result = binarySearch(arr, size, target);
 if (result != -1) {
 printf("Element %d is present at index %d.\n", target, result);
 } else {
 printf("Element %d is not present in the array.\n", target);
 }
 return 0;
}



# Binary-tree-using-linked-list
#include <stdio.h>
#include <stdlib.h>
typedef struct Node {
 int data;
 struct Node* next;
} Node;
Node* createNode(int data) {
 Node* newNode = (Node*)malloc(sizeof(Node));
 newNode->data = data;
 newNode->next = NULL;
 return newNode;
}
void linkedListToArray(Node* head, int* arr, int* size) {
 Node* current = head;
 *size = 0;
 while (current != NULL) {
 arr[(*size)++] = current->data;
 current = current->next;
 }
}
int binarySearch(int arr[], int size, int target) {
 int left = 0;
 int right = size - 1;
 while (left <= right) {
 int mid = left + (right - left) / 2;
 if (arr[mid] == target) {
 return mid;
 }
 if (arr[mid] < target) {
 left = mid + 1;
 } else {
 right = mid - 1;
 }
 }
 return -1; 
}
int main() {
 Node* head = createNode(1);
 head->next = createNode(3);
 head->next->next = createNode(5);
 head->next->next->next = createNode(7);
 head->next->next->next->next = createNode(9);
 int arr[5];
 int size;
 linkedListToArray(head, arr, &size);
 int target = 7;
 int result = binarySearch(arr, size, target);
 if (result != -1) {
 printf("Element %d found at index %d in the array.\n", target, 
result);
 } else {
 printf("Element %d not found in the array.\n", target);
 }
 Node* current = head;
 Node* nextNode;
 while (current != NULL) {
 nextNode = current->next;
 free(current);
 current = nextNode;
 }
 return 0;
}
