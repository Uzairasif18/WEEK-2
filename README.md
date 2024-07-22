# WEEK-2
#include <iostream>
#include <string>
using namespace std;

// Base class
class Person {
protected:
    string name;
    int age;

public:
    // Default constructor
    Person() : name(""), age(0) {}

    // Setter functions
    void setName(const string& name) {
        this->name = name;
    }

    void setAge(int age) {
        this->age = age;
    }

    // Getter functions
    string getName() const {
        return name;
    }

    int getAge() const {
        return age;
    }

    // Virtual functions for polymorphism
    virtual void Save_Information() = 0;
    virtual void Display_Information() const = 0;
};

// Derived class: Teacher
class Teacher : public Person {
private:
    string subject;
    double salary;

public:
    // Default constructor
    Teacher() : subject(""), salary(0.0) {}

    // Setter functions
    void setSubject(const string& subject) {
        this->subject = subject;
    }

    void setSalary(double salary) {
        this->salary = salary;
    }

    // Getter functions
    string getSubject() const {
        return subject;
    }

    double getSalary() const {
        return salary;
    }

    // Implementing virtual functions
    void Save_Information() override {
        cout << "Enter Teacher's Name: ";
        getline(cin, name);
        cout << "Enter Teacher's Age: ";
        cin >> age;
        cin.ignore(); // To consume the newline character left by cin
        cout << "Enter Teacher's Subject: ";
        getline(cin, subject);
        cout << "Enter Teacher's Salary: ";
        cin >> salary;
        cin.ignore();
    }

    void Display_Information() const override {
        cout << "Teacher's Name: " << name << endl;
        cout << "Teacher's Age: " << age << endl;
        cout << "Teacher's Subject: " << subject << endl;
        cout << "Teacher's Salary: " << salary << endl;
    }
};

// Derived class: Student
class Student : public Person {
private:
    string major;
    double gpa;

public:
    // Default constructor
    Student() : major(""), gpa(0.0) {}

    // Setter functions
    void setMajor(const string& major) {
        this->major = major;
    }

    void setGPA(double gpa) {
        this->gpa = gpa;
    }

    // Getter functions
    string getMajor() const {
        return major;
    }

    double getGPA() const {
        return gpa;
    }

    // Implementing virtual functions
    void Save_Information() override {
        cout << "Enter Student's Name: ";
        getline(cin, name);
        cout << "Enter Student's Age: ";
        cin >> age;
        cin.ignore(); // To consume the newline character left by cin
        cout << "Enter Student's Major: ";
        getline(cin, major);
        cout << "Enter Student's GPA: ";
        cin >> gpa;
        cin.ignore();
    }

    void Display_Information() const override {
        cout << "Student's Name: " << name << endl;
        cout << "Student's Age: " << age << endl;
        cout << "Student's Major: " << major << endl;
        cout << "Student's GPA: " << gpa << endl;
    }
};

int main() {
    Person* person;
    int choice;

    cout << "Enter 1 to input Teacher's information or 2 to input Student's information: ";
    cin >> choice;
    cin.ignore(); // To consume the newline character left by cin

    if (choice == 1) {
        person = new Teacher();
    } else if (choice == 2) {
        person = new Student();
    } else {
        cout << "Invalid choice." << endl;
        return 1;
    }

    person->Save_Information();
    person->Display_Information();

    delete person; // Free the allocated memory
    return 0;
}
