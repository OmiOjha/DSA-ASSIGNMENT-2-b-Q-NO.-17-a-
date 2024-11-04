To manage a student database with fields for register number, name, age, and CGPA, we can define a structure in C to store individual student records. We’ll then store multiple student records in an array of structures, allowing us to perform operations on the records.

The program will:

1.Take input for five student records.
2.Find and display the name of the student with the highest CGPA.

C Program Implementation:

#include <stdio.h>
#include <string.h>

#define NUM_STUDENTS 5  // Define the number of students

// Define the structure for student information
struct Student {
    int reg_no;
    char name[50];
    int age;
    float cgpa;
};

// Function to find the student with the highest CGPA
int findTopStudent(struct Student students[], int n) {
    
    int topIndex = 0;
    for (int i = 1; i < n; i++) {
        if (students[i].cgpa > students[topIndex].cgpa) {
            topIndex = i;
        }
    }
    return topIndex;
}

int main() {
    
    struct Student students[NUM_STUDENTS];  // Array of Student structures

    // Get user input for 5 students
    printf("Enter details for %d students:\n", NUM_STUDENTS);
    for (int i = 0; i < NUM_STUDENTS; i++) {
        printf("\nStudent %d:\n", i + 1);
        printf("Enter Register Number: ");
        scanf("%d", &students[i].reg_no);
        printf("Enter Name: ");
        scanf(" %[^\n]", students[i].name);  // Read string with spaces
        printf("Enter Age: ");
        scanf("%d", &students[i].age);
        printf("Enter CGPA: ");
        scanf("%f", &students[i].cgpa);
    }

    // Find the student with the highest CGPA
    int topStudentIndex = findTopStudent(students, NUM_STUDENTS);

    // Display the name of the student with the highest CGPA
    printf("\nStudent with the highest CGPA:\n");
    printf("Name: %s\n", students[topStudentIndex].name);
    printf("Register Number: %d\n", students[topStudentIndex].reg_no);
    printf("Age: %d\n", students[topStudentIndex].age);
    printf("CGPA: %.2f\n", students[topStudentIndex].cgpa);

    return 0;
}


Explanation:

1.Structure Definition:
We define a structure Student with members reg_no (register number), name (name), age (age), and cgpa (CGPA).

2.Data Input:
We use a loop to get user input for each student’s details and store it in an array of Student structures.

3.Finding the Student with the Highest CGPA:
The findTopStudent function iterates over the array to find the student with the highest CGPA and returns the index of that student.

4.Display the Result:
The program outputs the details of the student with the highest CGPA.
