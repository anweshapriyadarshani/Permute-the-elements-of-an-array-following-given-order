# Permute-the-elements-of-an-array-following-given-order
A permutation can be specified by an array P, where P[i] represents the location of the element at i in the permutation. For example, [2, 1, 0] represents the permutation where elements at the index 0 and 2 are swapped.  Given an array and a permutation, apply the permutation to the array. For example, given the array ["a", "b", "c"] and the permutation [2, 1, 0], return ["c", "b", "a"].

#include <bits/stdc++.h> 
using namespace std; 
  
// Function to permute the the given 
// array based on the given conditions 
int permute(int A[], int P[], int n) 
{ 
    // For each element of P 
    for (int i = 0; i < n; i++) { 
        int next = i; 
  
        // Check if it is already 
        // considered in cycle 
        while (P[next] >= 0) { 
  
            // Swap the current element according 
            // to the permutation in P 
            swap(A[i], A[P[next]]); 
            int temp = P[next]; 
  
            // Subtract n from an entry in P 
            // to make it negative which indicates 
            // the corresponding move 
            // has been performed 
            P[next] -= n; 
            next = temp; 
        } 
    } 
} 
  
// Driver code 
int main() 
{ 
    int A[] = { 5, 6, 7, 8 }; 
    int P[] = { 3, 2, 1, 0 }; 
    int n = sizeof(A) / sizeof(int); 
  
    permute(A, P, n); 
  
    // Print the new array after 
    // applying the permutation 
    for (int i = 0; i < n; i++) 
        cout << A[i] << " "; 
  
    return 0; 
} 
