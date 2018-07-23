### Copy Constructor in Java

* humara copy constructor galat tha
* ye sahi h...read the comments

```java
public static void main(String[] args) {
        Complex c1 = new Complex(10, 15);
         
        // Following involves a copy constructor call
        Complex c2 = new Complex(c1);  
 
        // Note that following doesn't involve a copy constructor call as
        // non-primitive variables are just references.
        Complex c3 = c2;  //this is wrong
 
        System.out.println(c2); // toString() of c2 is called here
    }
}

```

```java
Complex c3 = c2;  //this is wrong
```

This is wrong, this is correct only in c++, because it refers to the same memory location in java.So if we make any changes in copied object i.e c3 , it will get reflected in c2.

However, in C++ , this syntax creates completely new memory location.

for ref-->

<https://www.geeksforgeeks.org/copy-constructor-in-java/>

-------------------

### Singleton -Private Constructor

 ```java


class Sample {
static Sample ref;
int a;
int b;
    private Sample(int c, int d) {
        a=c;
        b=d;
    }

static Sample getInstance()
{
    if(ref==null)//if this line removed it becomes factory pattern
    ref=new Sample(2,3);
    return ref;
}

public void display(Sample ref)
{
    System.out.println(""+ref);
}

@Override
public String toString() {
    return "a:"+a+"b:"+b;
}

}
public class SingletonDemo {
public static void main(String args[])
{
    Sample s1,s2;
    s1=Sample.getInstance();
    s1.display(s1);
    s2=Sample.getInstance();
    s2.display(s2);
    //Sample s3= new Sample(2,4);
}
}
 ```

### Exception Basic Example

```java
class InvalidSalaryException extends Exception{  
    private int salary;
	InvalidSalaryException(String s){  
     super(s);  
    } 
	/*public String toString()
	{
		return "happy";
	}*/
   }
////////////////////////////////////////////
//This part of code is not connected to exception hadling
class Employee {
	private int empid;
	private String name;
	//private int salary;

	public Employee(int a, String b) {
		empid = a;
		name = b;
		//salary = c;
	}
	public void display() {
		System.out.println("" + empid);
		System.out.println("" + name);
		//System.out.println("" + salary);

	}
	
	 
}
/////////////////////////////////////////////////////////

public class ExceptionEmployee41 
{
	static void checkSalary(int salary)throws InvalidSalaryException{  
        if(salary<2000)  
         throw new InvalidSalaryException("Salary not valid");  
        else  
         System.out.println("valid salary");  
      } 
	
public static void main(String argsS[]) {
    Employee e1=new Employee(432,"Divyash");
    e1.display();
    
    try{  
    	checkSalary(1003);  
        }catch(Exception m){System.out.println("Exception occured: "+m);}  
    
        System.out.println("rest of the code...");  
    }  
}
```

* With tostring() method output:

  ```
  432
  Divyash
  Exception occured: happy
  rest of the code...
  ```

* Without toString()

  ```
  432
  Divyash
  Exception occured: InvalidSalaryException: not valid
  rest of the code...
  ```

   

***Note:Static Methods cannot be overriden***

_________________________________________________

# Qt

#### To change dimensions of dialog box

```javascript
#include "mydialog.h"

MyDialog::MyDialog(QWidget *parent)
    : QDialog(parent)
{this->setWindowTitle("Simple Dialog Demo");
    this->setMinimumWidth(900);
    this->setMinimumHeight(300);
}

MyDialog::~MyDialog()
{

}

```

* For every GUI we use a parent.

* Main window is for other applications

* See naming conventions.

* No version control,None-as right now we are not using git or svn.

  ```java
  #include "mydialog.h"
  #include <QApplication>
  
  int main(int argc, char *argv[])
  {
      QApplication a(argc, argv);
      MyDialog w;
      w.show();
  
      return a.exec();
  }
  ```

* w is the object of MyDialog class.

* To add any widget we use Widget class.

* Dialog is like blank window to place anything.

* QApplication is responsible for GUI rendering and starting event loop.

* if we comment return a.exec() ,no dialog box,a is instance of class, if we don't write this we won't see any HMI.This is to for C++ appn to take support from QT /QML appn.

  ```javascript
  //mydialog.h
  #ifndef MYDIALOG_H
  #define MYDIALOG_H
  
  #include <QDialog>
  
  class MyDialog : public QDialog
  {
      Q_OBJECT
  
  public:
      MyDialog(QWidget *parent = 0);
      ~MyDialog();
  };
  
  #endif // MYDIALOG_H
  
  #endif // MYDIALOG_H
  
  ```

* Resolution is width*height

* Web Application-On browser

* Stand Alone Application- Vlc etc

  #### Simple .pro file:

  QT +=core gui widgets---->This means QT library comes from GUI library.

  TArget=hello

  TEMPLATE= app

  SOURCES+=main.cpp mydialog.cpp

  HEADERS+=mydialog.h

```linux
#linux command
make
```

 generates makefile out of pro file.

```
which qmake
```

To check version of Qmake

```
ls /opt/QtSDK/5.9.4/gcc_64/bin/qmake
export PATH=/opt/QtSDK/5.9.4/gcc_64/bin:$PATH
```

if qmake is not present -->Go to your Qt folder file (ex:FirstProgarm) and give this command.This is temperory only for one.

***To build from Terminal***

go to your project.

```
make
```

To make file executable.

```
ls
```

Now our file becomes green in colour.

```
./FirstProgram
```

To run the same.Dialog box opens.If we don't have qmake, we can execute from terminal.

```
nano ~/.bashrc
```

if we don't have qmake then add path in bashrc,but be very careful while updating the path

```
export PATH=/opt/QtSDK/5.9.4/gcc_64/bin:$PATH
```

**Parent**

```python
#include <QDialog>
class MyDialog : public QDialog
{
    Q_OBJECT
public:
    MyDialog(QWidget *parent = 0); #parent=0 means this file is parent
  
    ~MyDialog();
};
```

This used so that button to be part of dialog

-----------------------

#### Label Addition

```c++
#include "mydialog.h"
//this is .cpp file
MyDialog::MyDialog(QWidget *parent)
    : QDialog(parent)
{this->setWindowTitle("Hello Dailog");
    this->setMaximumWidth(300);
    this->setMaximumHeight(300);
    label=new QLabel("Hello",this);# this is used to create new object under Mydialog only
        lineEdit=new QLineEdit(this);
        button=new QPushButton("Submit",this);
}

MyDialog::~MyDialog()
{

}
```

***NOTE:To check documentation in sir's notes.***

```c++
        this->setGeometry(0,0,400,300);   //MyDialog instance
        label->setGeometry(10,10,100,20);
        lineEdit->setGeometry(10,40,100,20);
        button->setGeometry(10,70,100,20);
```

* 10,10->cooradinates from where it starts.

* 100,20->sizze of object/widget.

* setWindowTitle, setMaximumWidth, setMaximumHeight,QPushButton,setGeometry,these all are coming from Qwidget class and all are non-static methods as we are creating objects by non static method.

* To check the documentation of any object,click on function or class and press F1.

  ----------------------------------

  