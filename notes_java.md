

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
./FirstProgramfill
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

* We can't call function AddWidget of QLayout in grid program because this function of QLayout is different from the function of QGridLayout.

  /home/kpit/workspace/Qt/gridBoxes/mydialog.cpp:11: error: no matching function for call to ‘QLayout::addWidget(QPushButton*&, int, int)’
       layout->addWidget(firstButton,1,1);
                                        ^

### Hierarchy of Classes

see diagram in notebook

QLayout

​        -QBoxLayout

​		-QVBoxLayer

​		-QHBoxLayout

`	-QGridLayout

​		-addWidget(Qwidget)

​		-addWidget(Qwidget *,int,int)

### Alert Message

```
QMessageBox::information(this,"Your Message","Cleared successfully");
```

We don't need to create object here because information is a static method.

---------------------

### Properties

 |**Read** |

​                                           **write**

**text**                                         text()  						 SetText()

value                        	     value()						  SetValue()

enabled                  	enabled()					   SetEnabled()

  digitsCount 

* **Slot**-Whenever button clicked,event handler automatically calls it. 
* **Q_OBJECT**-not std c++ class,not function ,not variable,Represents some Qt extensions.As std c++ cannot understand signals,slot,so there is MOC(Meta Object Compiler). MOC generates windows compatible c++  code or a C++ file based on Qt extensions.Meta is something which describes some other code,Meta object that defines other object.
* main.cpp  ->  main.o
* mydialog.cpp   ->  mydialog.o------------------------------------------->MyFirstApplication
* mydialog.h ->   moc_mydialog.cpp  ->   moc_mudialog.o------>
* profile decides how to generate make file.
* qmake converts makefile into profile.

Q_Object decides wether to use MOC or not.              

* **qtcreater**     -whatever we r doing on terminal is done on qtcreater.

* **uic--ui compiler**

  mydialog.ui -> mydialog.h  //converted by uic

  rest all same process

  * Use **qmake** command on terminal to see all the conversions.
  * We include "ui_mydialog.h" in mydialog.cpp. 

* **Assistant**-gives qt documentation.

* Tools-moc,uic,assistant

* linguist for lang translation (english->spanish) not for our use.

* to generate pro file `qmake -project`(Surviving with command line argument)

   * first create main.cpp
  * Then `qmake -project`
  * `ls`
  * We need to make some additions to pro file.
  * `make`
  * `ls`
  * For purely command linea ppliaction we use QCore application,refer edu online.

```c++
Q_PROPERTY(int temperature READ temperature WRITE setTemperature NOTIFY temperatureChanged)  
Q_PROPERTY(double humidity READ humidity WRITE setHumidity NOTIFY humidityChanged)
```

* These are micros,for each property there msut be a private variable.

* **signals** ---- each notifying method.

  ```c++
  signals:
      temperatureChanged(int);//no void or data type required
      humidityChanged(double);//only declaration required,no definition
  
  ```

  

Qt Property System  : --  In Qt classes we don't need to give

---------------------------------

# QML

Qt Quick Module:

Core

gui

widgets

* Use of QML  -->  

  ```javascript
  import QtQuick 2.9
  import QtQuick.Window 2.2
  
  Window {//means a window will come
      visible: true
      width: 640
      height: 480
      title: qsTr("Hello World")//qstr is unified string handing mehanism
  ```

`ls`

`qml-demo$ qmlscene main.qml`

**Exporting properties from cpp:-**

```
QQmlEngineContext *context=engine.rootContext();

context->setContextProperty("weather",&w1);

```



in Qml:-

//weather.temperature,weather.humidity

**dbus from Terminal**

```
dbus-send --session --reply-timeout=120000 --type=method_call --dest='org.examples.ivi.dashboard' '/vehicle' 'local.qmlcppdemo.MyController.updateSpeedDBus' string:70

```

### CAN

to prepare a virtual CAN:

```
sudo modprobe vcan
sudo ip link add dev vcan0 type vcan
sudo ip link set up vcan0
sudo apt-get install can-utils
 candump vcan0
 
 cansend vcan0 064#4142 //41==A & 42==B in ASCII
 
```

can dump and sen din two different files

### Sending CAN Frames

QCANBus frame;

```c++
CANAdaptor::CANAdaptor(QObject *parent) : QObject(parent)
{
QCANBusFrame frame;
frame.setFrameId(0x128);
QByteArray data;
data.setNum(40);
frame.setPayload(data);
m_canDevice.writeFrame(frame);
}
```



* when we talk to any external agent it is done through middle ware solutions.ex:CANbus and Dbus