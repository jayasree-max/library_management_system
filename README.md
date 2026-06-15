# library_management_system
#include <iostream>
using namespace std;

class Library {
private:
    string book[100], author[100];
    bool issued[100];
    int total = 0;

public:
    void addBook() {
        cout << "\nEnter Book Title: ";
        cin.ignore();
        getline(cin, book[total]);

        cout << "Enter Author Name: ";
        getline(cin, author[total]);

        issued[total] = false;
        total++;

        cout << "Book Added Successfully!\n";
    }

    void issueBook() {
        string name;
        cin.ignore();
        cout << "\nEnter Book Title to Issue: ";
        getline(cin, name);

        for (int i = 0; i < total; i++) {
            if (book[i] == name && !issued[i]) {
                issued[i] = true;
                cout << "Book Issued Successfully!\n";
                return;
            }
        }

        cout << "Book Not Available!\n";
    }

    void returnBook() {
        string name;
        cin.ignore();
        cout << "\nEnter Book Title to Return: ";
        getline(cin, name);

        for (int i = 0; i < total; i++) {
            if (book[i] == name && issued[i]) {
                issued[i] = false;
                cout << "Book Returned Successfully!\n";
                return;
            }
        }

        cout << "Book Not Found!\n";
    }

    void searchBook() {
        string name;
        cin.ignore();
        cout << "\nEnter Book Title: ";
        getline(cin, name);

        for (int i = 0; i < total; i++) {
            if (book[i] == name) {
                cout << "\nBook Found\n";
                cout << "Title: " << book[i] << endl;
                cout << "Author: " << author[i] << endl;

                if (issued[i])
                    cout << "Status: Issued\n";
                else
                    cout << "Status: Available\n";

                return;
            }
        }

        cout << "Book Not Found!\n";
    }

    void display() {
        cout << "\n--- Library Books ---\n";

        for (int i = 0; i < total; i++) {
            cout << "\nTitle: " << book[i];
            cout << "\nAuthor: " << author[i];

            if (issued[i])
                cout << "\nStatus: Issued\n";
            else
                cout << "\nStatus: Available\n";
        }
    }
};

int main() {
    Library l;
    int choice;

    do {
        cout << "\n===== LIBRARY MANAGEMENT SYSTEM =====";
        cout << "\n1. Add Book";
        cout << "\n2. Issue Book";
        cout << "\n3. Return Book";
        cout << "\n4. Search Book";
        cout << "\n5. Display Books";
        cout << "\n6. Exit";

        cout << "\nEnter Choice: ";
        cin >> choice;

        switch (choice) {
        case 1:
            l.addBook();
            break;

        case 2:
            l.issueBook();
            break;

        case 3:
            l.returnBook();
            break;

        case 4:
            l.searchBook();
            break;

        case 5:
            l.display();
            break;

        case 6:
            cout << "Thank You!";
            break;

        default:
            cout << "Invalid Choice!";
        }

    } while (choice != 6);

    return 0;
}