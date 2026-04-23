# C-Assignment-1 

This C++ program meet all the requirements of the given instructions, including modular functional decomposition, array manipulation, and file I/O operations.

#include <iostream>
#include <fstream>
#include <string>

using namespace std;

// --- Function Prototypes ---
void inputArray(int arr[], int size);
void displayArray(const int arr[], int size);
int calculateSum(const int arr[], int size);
void writeToFile(const int arr[], int size, string filename);
void readFromFile(int arr[], int size, string filename);

/**
 * ROLE OF FUNCTIONS: 
 * Functions allow for modular programming, breaking a large problem into 
 * smaller, manageable, and reusable pieces. This improves readability 
 * and makes debugging much easier.
 */

int main() {
    const int SIZE = 10;
    int numbers[SIZE];
    string fileName = "data.txt";

    cout << "--- Part (A): Array Input ---" << endl;
    inputArray(numbers, SIZE);

    cout << "\n--- Part (B): Displaying Array ---" << endl;
    displayArray(numbers, SIZE);

    cout << "\n--- Part (C): Writing to File ---" << endl;
    writeToFile(numbers, SIZE, fileName);

    cout << "\n--- Part (D): Reading from File ---" << endl;
    // We pass the array to be refilled from the file data
    readFromFile(numbers, SIZE, fileName);

    cout << "\n--- Part (E): Sum Analysis ---" << endl;
    /**
     * PARAMETER PASSING: 
     * In C++, arrays are passed by reference (pointer) by default. This is efficient 
     * because it avoids copying the entire array. 'calculateSum' uses a value-returning 
     * pattern to return the final integer result to the caller.
     */
    int totalSum = calculateSum(numbers, SIZE);
    cout << "The sum of the array elements is: " << totalSum << endl;

    return 0;
}

// --- Function Definitions ---

// Part (A): Input logic
void inputArray(int arr[], int size) {
    cout << "Please enter " << size << " integers:" << endl;
    for (int i = 0; i < size; i++) {
        cout << "Element [" << i << "]: ";
        cin >> arr[i];
    }
}

// Part (B): Display logic
void displayArray(const int arr[], int size) {
    cout << "Array contents: ";
    for (int i = 0; i < size; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

// Part (B/E): Calculation logic (Value-returning function)
int calculateSum(const int arr[], int size) {
    int sum = 0;
    for (int i = 0; i < size; i++) {
        sum += arr[i];
    }
    return sum;
}

/**
 * FILE I/O ROLE:
 * File I/O (Input/Output) allows for data persistence. This means the 
 * data can be saved after the program ends and reloaded later.
 */

// Part (C): Write logic
void writeToFile(const int arr[], int size, string filename) {
    ofstream outFile(filename);
    if (outFile.is_open()) {
        for (int i = 0; i < size; i++) {
            outFile << arr[i] << " ";
        }
        outFile.close();
        cout << "Data successfully saved to " << filename << endl;
    } else {
        cout << "Error: Could not open file for writing." << endl;
    }
}

// Part (D): Read logic
void readFromFile(int arr[], int size, string filename) {
    ifstream inFile(filename);
    if (inFile.is_open()) {
        cout << "Reading data from " << filename << "..." << endl;
        for (int i = 0; i < size; i++) {
            inFile >> arr[i];
        }
        inFile.close();
        // Displaying immediately as per Part (D) requirements
        displayArray(arr, size);
    } else {
        cout << "Error: Could not open file for reading." << endl;
    }
}


*Key Highlights of the Solution*:

Parameter Passing: The array is passed to functions using its base address. I used the const keyword for display and write functions to ensure the data isn't accidentally modified (Read-Only access).

Modular Design: Each requirement (Input, Display, Sum, Read, Write) is encapsulated in its own function, making the main() function clean and easy to follow.

File Handling: The program uses ofstream for writing and ifstream for reading. It includes basic error checking to ensure the file exists or can be created.

Documentation: Comments are included throughout to explain the role of each component as requested in Part (E).



