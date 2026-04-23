C++ Assignment: Arrays, Functions, and File Handling
Objective
This program demonstrates:
° Use of 1D arrays
° Function decomposition
° Parameter passing
° File input/output (write and read)
° Value-returning functions

#include <iostream>
#include <fstream> // Required for file handling
using namespace std;

// Constant for array size
const int SIZE = 10;

/*
 Function: inputArray()
 Purpose: Takes input from the user and stores values in the array.
 Parameter Passing: The array is passed as an argument so the function
                    can directly modify the original array.
*/
void inputArray(int arr[], int size)
{
    cout << "Enter " << size << " integers:\n";

    for (int i = 0; i < size; i++)
    {
        cout << "Element " << i + 1 << ": ";
        cin >> arr[i];
    }
}

/*
 Function: displayArray()
 Purpose: Displays elements of the array.
 Parameter Passing: Array is passed to read its values.
*/
void displayArray(int arr[], int size)
{
    cout << "\nArray Elements:\n";

    for (int i = 0; i < size; i++)
    {
        cout << arr[i] << " ";
    }

    cout << endl;
}

/*
 Function: calculateSum()
 Purpose: Calculates and returns the sum of array elements.
 Type: Value-returning function
*/
int calculateSum(int arr[], int size)
{
    int sum = 0;

    for (int i = 0; i < size; i++)
    {
        sum += arr[i];
    }

    return sum;
}

/*
 Function: writeToFile()
 Purpose: Writes array elements into a text file.
 File I/O: Uses ofstream to create/write file.
*/
void writeToFile(int arr[], int size)
{
    ofstream outFile("arrayData.txt");

    if (!outFile)
    {
        cout << "Error opening file for writing!\n";
        return;
    }

    for (int i = 0; i < size; i++)
    {
        outFile << arr[i] << " ";
    }

    outFile.close();

    cout << "\nData successfully written to file.\n";
}

/*
 Function: readFromFile()
 Purpose: Reads array elements from file and stores them back into array.
 File I/O: Uses ifstream to read file.
*/
void readFromFile(int arr[], int size)
{
    ifstream inFile("arrayData.txt");

    if (!inFile)
    {
        cout << "Error opening file for reading!\n";
        return;
    }

    for (int i = 0; i < size; i++)
    {
        inFile >> arr[i];
    }

    inFile.close();

    cout << "\nData successfully read from file.\n";

    // Display array after reading
    displayArray(arr, size);
}

/*
 Main Function
 Coordinates the execution of all functions.
 Demonstrates modular programming using functions.
*/
int main()
{
    // Part (A): Declare 1D array
    int numbers[SIZE];

    // Input values
    inputArray(numbers, SIZE);

    // Part (B): Display array
    displayArray(numbers, SIZE);

    // Part (C): Write array to file
    writeToFile(numbers, SIZE);

    // Clear array before reading (optional demonstration)
    for (int i = 0; i < SIZE; i++)
    {
        numbers[i] = 0;
    }

    // Part (D): Read data from file
    readFromFile(numbers, SIZE);

    // Part (E): Calculate and display sum
    int total = calculateSum(numbers, SIZE);

    cout << "\nSum of array elements: " << total << endl;

    return 0;
}




Explanation of Key Concepts

1. Role of Functions
Functions divide the program into smaller reusable parts:
inputArray() → Takes user input
displayArray() → Displays values
calculateSum() → Returns total
writeToFile() → Stores data into file
readFromFile() → Reads data from file

This improves:
°Readability
°Reusability
°Maintainability

2. Parameter Passing
Arrays are passed to functions like:

void inputArray(int arr[], int size)


This means:
°The function works on the original array
°No duplicate copy is created
°Changes affect the main array

3. File Input/Output (File I/O)
Writing to File
  
    ofstream outFile("arrayData.txt");


Used to:
° Create file
° Store array data


Reading from File

  ifstream inFile("arrayData.txt");

Used to:
°Open file
°Read stored values back into array

4. Value-Returning Function

 int calculateSum(int arr[], int size)

Returns:
°Total sum of array elements
°Used in main() like:

    int total = calculateSum(numbers, SIZE);


Expected Output Example

Enter 10 integers:
Element 1: 5
Element 2: 3
...
Element 10: 7

Array Elements:
5 3 2 8 6 9 1 4 0 7

Data successfully written to file.

Data successfully read from file.

Array Elements:
5 3 2 8 6 9 1 4 0 7

Sum of array elements: 45

