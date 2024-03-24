#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <conio.h> 

#define MAX_RECORDS 100
#define MAX_NAME_LENGTH 50
#define MAX_EMAIL_LENGTH 50

struct Record 
{
    char name[MAX_NAME_LENGTH];
    char email[MAX_EMAIL_LENGTH];
};

void addRecord(struct Record records[], int *numRecords) 
{
 
    if (*numRecords < MAX_RECORDS) 
    {
        printf("Enter name: ");
        scanf("%s", records[*numRecords].name);
        printf("Enter email: ");
        scanf("%s", records[*numRecords].email);
        (*numRecords)++;
        printf("Record added successfully!\n");
    } else 
    {
        printf("Database is full!\n");
    }
}


void displayRecords(struct Record records[], int numRecords) 
{
    if (numRecords > 0) 
    {
        printf("Records in the database:\n");
        for (int i = 0; i < numRecords; i++) 
        {
            printf("Name: %s, Email: %s\n", records[i].name, records[i].email);
        }
    } else 
    {
        printf("Database is empty!\n");
    }
}

int main() 
{
    struct Record records[MAX_RECORDS];
    int numRecords = 0;
    int choice;

    do 
    {
        printf("\nDatabase Management System\n");
        printf("1. Add a record\n");
        printf("2. Display all records\n");
        printf("3. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) 
        {
            case 1:
                addRecord(records, &numRecords);
                break;
            case 2:
                displayRecords(records, numRecords);
                break;
            case 3:
                printf("Exiting... Thank you!\n");
                break;
            default:
                printf("Invalid choice! Please try again.\n");
        }
    } while (choice != 3);

    return 0;
}
