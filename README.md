# OOP-04
EXPERIMENT NO.4/*
Write a C++ program that creates an output file, writes information to it, closes the file and
open it again as an input file and read the information from the file.
*/

#include<iostream>
#include<fstream>
using namespace std;

class Employee
{
    char Name[20];
    int ID;
    double salary;
    public:
        void accept()
        {
            cin>>Name;
            cin>>ID;
            cin>>salary;
        }
        void display()
        {
            cout<<"\n Enter Name:"<<Name;
            cout<<"\n Enter Id:"<<ID;
            cout<<"\n Enter Salary:"<<salary;
        }
};
       
int main()
{
    Employee o[5];
    fstream f;
    int i,n;
   
    f.open("b16.txt");
    cout<<"\n How many employee information do you need to store?";
    cin>>n;
    cout<<"\n Enter information of employee in this format(NAME/ID/SALARY)";
    for(i=0;i<n;i++)
    {
        cout<<"\n Enter information of:"<<i<<"\n Employee";
        o[i].accept();
        f.write((char*)&o[i],sizeof o[i]);
    }
   
    f.close();
  f.open("b16.txt");    cout<<"\n Information of Employees is as follows:";
    for(i=0;i<n;i++)
    {
        f.write((char*)&o[i],sizeof o[i]);
        o[i].display();
    }
    f.close();

        return 0;
}

output-
How many employee information do you need to store?3

 Enter information of employee in this format(NAME/ID/SALARY)
 Enter information of:0
 Employee xyz 123 50000

 Enter information of:1
 Employee abc 234 6000

 Enter information of:2
 Employee lmn 565 70000

 Information of Employees is as follows:
 Enter Name:xyz
 Enter Id:123
 Enter Salary:50000
 Enter Name:abc
 Enter Id:234
 Enter Salary:6000
 Enter Name:lmn
 Enter Id:565
 Enter Salary:70000

b16.txt file:
as i'm writing file in binary format
so my file looks like:-
