/*********************************************************************************************************
* Eduardo Dally, Juan Medina, Mohamad Alsabbaghe, Alain Hernandez							4/18/2016    *
* Geometric Calculator v1.2   UPDATES: Make code more concise and organized. Use more files.             *
* This calculator gives the use the ability to calculate the area and volume of different geometric      *
* shapes with a very clean user interface.                                                               *
**********************************************************************************************************/
//HEADER
#include <iostream>
#include <cmath>
#include <string>
#include "Functions.h"
#include <algorithm>
#include <ctype.h>
#include <Windows.h>
#include <fstream>

using namespace std;


//PROTOTYPE
//GEOMETRIC
double parallelogram(double number1, double number2);
double triangle(double number1, double number2);
double trapezoid(double number1, double number2, double number3);
double circle(double number1);
double rectangular(double number1, double number2, double number3);
double cylinder(double number1, double number2);
double pyramid(double number1, double number2);
double cone(double number1, double number2);
//ALGEBRAIC
double add(double number1, double number2);
double subt(double number1, double number2);
double mult(double number1, double number2);
double divi(double number1, double number2);
double sqr(double number1);
long long int fact(long long int factorial);

//MAIN FUNCTION
int main()
{
	//VARIABLES
	string name;
	string lname;
	int choice;
	int page;
	double number1, number2, number3, number4;
	char answer;
	char mainmenu;
	int i;
	long long int factorial;
	ofstream result;
	string filename;
	int prism_v = 0;
	int cylinder_v = 0;
	int pyramid_v = 0;
	int cone_v = 0;
	int answer_v;

	//STRUCTURE ARRAY
	struct shapeDataType
	{
		string shape;
		double volume[20];
	};

	struct shapeDataType arrayofshapes[4];

	arrayofshapes[0].shape = "Rectangular Prism";
	arrayofshapes[1].shape = "Right Circular Cylinder";
	arrayofshapes[2].shape = "Right Square Pyramid";
	arrayofshapes[3].shape = "Right Circular Cone";

	cout.precision(15);


	//WELCOME MENU
MENU:cout << "Welcome to Geometric Calculator v1.2" << endl << endl;
	cout << "Please enter your first and last name separated by a space: " << endl;
	cin >> name >> lname;
	transform(name.begin(), name.end(), name.begin(), toupper);
	transform(lname.begin(), lname.end(), lname.begin(), toupper);
	system("CLS");
	cout << "Welcome Back: " << name << " " << lname << endl << endl;

	//FILE NAME
	cout << "Name a file to backup information: " << endl;
	cin >> filename;
	filename.append(".txt");
	result.open(filename);
	system("PAUSE");
	system("CLS");

menu1://CALCULATOR SELECTION
	cout << "CALCULATOR SELECTION" << endl;
	cout << "1. Algebraic" << endl;
	cout << "2. Geometric" << endl;
	cout << "0. |EXIT|" << endl;
	cin >> page;

	if (page == 0)
	{
		result.close();
		system("CLS");
		cout << arrayofshapes[0].shape << endl;
		cout << "You calculated the volume of a prism " << prism_v << " times. These are your results. " << endl;
		for (int i = 0; i < prism_v; i++)
		{	
			cout << arrayofshapes[0].volume[i] << endl;
		}

		cout << arrayofshapes[1].shape << endl;
		cout << "You calculated the volume of a cylinder " << cylinder_v << " times. These are your results. " << endl;
		for (int i = 0; i < cylinder_v; i++)
		{	
			cout << arrayofshapes[1].volume[i] << endl;
		}

		cout << arrayofshapes[2].shape << endl;
		cout << "You calculated the volume of a pyramid " << pyramid_v << " times. These are your results. " << endl;
		for (int i = 0; i < pyramid_v; i++)
		{	
			cout << arrayofshapes[2].volume[i] << endl;
		}

		cout << arrayofshapes[3].shape << endl;
		cout << "You calculated the volume of a cone " << cone_v << " times. These are your results. " << endl;
		for (int i = 0; i < cone_v; i++)
		{	
			cout << arrayofshapes[3].volume[i] << endl;
		}

		system("PAUSE");
		return 0;

	}
	else
		if (page == 1)
		{
			system("CLS");
			goto ALGEBRAIC;
		}
		else
			if (page == 2)
			{
				system("CLS");
				goto GEOMETRIC;
			}

ALGEBRAIC://ALGEBRAIC
	cout << "MAIN MENU" << endl;
	cout << "Page 1                 Page 2" << endl;
	cout << "1. Addition            1. Cosine" << endl;
	cout << "2. Subtraction         2. Sine" << endl;
	cout << "3. Multiplication      3. Tangent" << endl;
	cout << "4. Division            4. Arc Cosine" << endl;
	cout << "5. Square              5. Arc Sine" << endl;
	cout << "6. Square Root         6. Arc Tangent" << endl;
	cout << "7. Factorial          " << endl << endl;
	cout << "0. GO BACK" << endl << endl;
	cout << "Select a page." << endl;
	cin >> page;

	if (page == 0)
	{
		system("CLS");
		goto menu1;
	}
	else
		if (page == 1)
		{
			system("CLS");
			goto firstswitcha;
		}
		else
			if (page == 2)
			{
				system("CLS");
				goto secondswitcha;
			}
			else
				cout << "ERROR: The page you have selected does not exist." << endl;
	system("pause");
	system("CLS");
	goto ALGEBRAIC;
	//SWITCH1
firstswitcha:cout << "Select a number:" << endl << endl;
	cout << "0. GO BACK" << endl << endl;
	cout << "Page 1" << endl;
	cout << "1. Addition" << endl;
	cout << "2. Subtraction" << endl;
	cout << "3. Multiplication" << endl;
	cout << "4. Division" << endl;
	cout << "5. Square" << endl;
	cout << "6. Square Root" << endl;
	cout << "7. Factorial" << endl << endl;
	cin >> choice;
	if (choice == 0)
	{
		system("CLS");
		goto ALGEBRAIC;
	}
	else
		system("CLS");
switch1:switch (choice)
{
	//ADDITION
add:case 1:
{cout << "Enter 2 numbers:" << endl;
cin >> number1;
cin >> number2;
cout << "The result is: " << add(number1, number2) << endl;
result << "Addition:" << endl;
result << "The result is: " << add(number1, number2) << endl << endl;
cout << "Would you like to go to the main menu?" << endl;
cout << "'y' = Main Menu | 'n' = Algebraic Menu" << endl;
cin >> answer;
if (answer == 'y')
{
	system("CLS");
	goto menu1;
}

else
{
	system("CLS");
	goto ALGEBRAIC;
}
break;

//SUBTRACTION
sub:case 2:
{
	cout << "Enter 2 numbers:" << endl;
	cin >> number1;
	cin >> number2;
	cout << "The result is: " << subt(number1, number2) << endl;
	result << "Subtraction:" << endl;
	result << "The result is: " << subt(number1, number2) << endl << endl;
	cout << "Would you like to go to the main menu?" << endl;
	cout << "'y' = Main Menu | 'n' = Algebraic Menu" << endl;
	cin >> answer;
	if (answer == 'y')
	{
		system("CLS");
		goto menu1;
	}

	else
	{
		system("CLS");
		goto ALGEBRAIC;
	}
}
break;

//MULTIPLICATION
mult:case 3:
{
	cout << "Enter 2 numbers:" << endl;
	cin >> number1;
	cin >> number2;
	cout << "The result is: " << mult(number1, number2) << endl;
	result << "Multiplication:" << endl;
	result << "The result is: " << mult(number1, number2) << endl << endl;
	cout << "Would you like to go to the main menu?" << endl;
	cout << "'y' = Main Menu | 'n' = Algebraic Menu" << endl;
	cin >> answer;
	if (answer == 'y')
	{
		system("CLS");
		goto menu1;
	}

	else
	{
		system("CLS");
		goto ALGEBRAIC;
	}
}
break;

//DIVISION
divi:case 4:
{
	cout << "Enter 2 numbers:" << endl;
	cin >> number1;
	cin >> number2;
	if (divi(number1, number2) == -1)
		cout << "ERRO: Cannot divide by 0." << endl;
	else
		cout << "The result is: " << divi(number1, number2) << endl;
	result << "Division:" << endl;
	result << "The result is: " << divi(number1, number2) << endl << endl;
	cout << "Would you like to go to the main menu?" << endl;
	cout << "'y' = Main Menu | 'n' = Algebraic Menu" << endl;
	cin >> answer;
	if (answer == 'y')
	{
		system("CLS");
		goto menu1;
	}

	else
	{
		system("CLS");
		goto ALGEBRAIC;
	}
}
break;

//SQUARE
sqr:case 5:
{
	cout << "Enter a number:" << endl;
	cin >> number1;
	cout << " The result is: " << sqr(number1) << endl;
	result << "Square:" << endl;
	result << " The result is: " << sqr(number1) << endl << endl;
	cout << "Would you like to go to the main menu?" << endl;
	cout << "'y' = Main Menu | 'n' = Algebraic Menu" << endl;
	cin >> answer;
	if (answer == 'y')
	{
		system("CLS");
		goto menu1;
	}

	else
	{
		system("CLS");
		goto ALGEBRAIC;
	}
}
break;

//SQUAREROOT
sqrt:case 6:
{
	cout << "Enter a number:" << endl;
	cin >> number1;
	if (number1 < 0)
		cout << "ERROR: The square root of a negative number is an imaginery number" << endl;
	else
		cout << "The result is: " << sqrt(number1) << endl;
	result << "Square Root:" << endl;
	result << "The result is: " << sqrt(number1) << endl << endl;
	cout << "Would you like to go to the main menu?" << endl;
	cout << "'y' = Main Menu | 'n' = Algebraic Menu" << endl;
	cin >> answer;
	if (answer == 'y')
	{
		system("CLS");
		goto menu1;
	}

	else
	{
		system("CLS");
		goto ALGEBRAIC;
	}
}
break;

// FACTORIAL
fact:case 7:
{
	cout << "Enter a number:" << endl;
	cin >> number1;
	cout << "The result is: " << fact(number1) << endl;
	result << "Factorial:" << endl;
	result << "The result is: " << fact(number1) << endl << endl;
	cout << "Would you like to go to the main menu?" << endl;
	cout << "'y' = Main Menu | 'n' = Algebraic Menu" << endl;
	cin >> answer;
	if (answer == 'y')
	{
		system("CLS");
		goto menu1;
	}

	else
	{
		system("CLS");
		goto ALGEBRAIC;
	}
}
break;

//DEFAULT
default:
{
	cout << "Your choice does not match any of the presented options. Please try again." << endl;
	system("pause");
	system("CLS");
	goto firstswitcha;
}
}
//SWITCH2
secondswitcha:cout << "Select an number:" << endl << endl;
cout << "0. GO BACK" << endl << endl;
cout << "Page 2" << endl;
cout << "1. Cosine" << endl;
cout << "2. Sine" << endl;
cout << "3. Tangent" << endl;
cout << "4. Arc Cosine" << endl;
cout << "5. Arc Sine" << endl;
cout << "6. Arc Tangent" << endl << endl;
cin >> choice;
if (choice == 0)
{
	system("CLS");
	goto ALGEBRAIC;
}
else
switch2:switch (choice)
{
	//COSINE
cos:case 1:
{
	cout << "Enter a number:" << endl;
	cin >> number1;
	cout << "The result is: " << cos(number1 * PI / 180.0) << endl;
	result << "Cosine:" << endl;
	result << "The result is: " << cos(number1 * PI / 180.0) << endl << endl;
	cout << "Would you like to go to the main menu?" << endl;
	cout << "'y' = Main Menu | 'n' = Algebraic Menu" << endl;
	cin >> answer;
	if (answer == 'y')
	{
		system("CLS");
		goto menu1;
	}

	else
	{
		system("CLS");
		goto ALGEBRAIC;
	}
}
break;

//SINE
sin:case 2:
{
	cout << "Enter a number:" << endl;
	cin >> number1;
	cout << "The result is: " << sin(number1 * PI / 180.0) << endl;
	result << "Sine:" << endl;
	result << "The result is: " << sin(number1 * PI / 180.0) << endl << endl;
	cout << "Would you like to go to the main menu?" << endl;
	cout << "'y' = Main Menu | 'n' = Algebraic Menu" << endl;
	cin >> answer;
	if (answer == 'y')
	{
		system("CLS");
		goto menu1;
	}

	else
	{
		system("CLS");
		goto ALGEBRAIC;
	}
}
break;

//TANGENT
tan:case 3:
{
	cout << "Enter a number:" << endl;
	cin >> number1;
	cout << "The result is: " << tan(number1 * PI / 180.0) << endl;
	result << "Tangent:" << endl;
	result << "The result is: " << tan(number1 * PI / 180.0) << endl << endl;
	cout << "Would you like to go to the main menu?" << endl;
	cout << "'y' = Main Menu | 'n' = Algebraic Menu" << endl;
	cin >> answer;
	if (answer == 'y')
	{
		system("CLS");
		goto menu1;
	}

	else
	{
		system("CLS");
		goto ALGEBRAIC;
	}
}
break;

//ARC COSINE
acos:case 4:
{
	cout << "Enter a number:" << endl;
	cin >> number1;
	cout << "The result is: " << acos(number1) * 180.0 / PI << endl;
	result << "Arc Cosine" << endl;
	result << "The result is: " << acos(number1) * 180.0 / PI << endl << endl;
	cout << "Would you like to go to the main menu?" << endl;
	cout << "'y' = Main Menu | 'n' = Algebraic Menu" << endl;
	cin >> answer;
	if (answer == 'y')
	{
		system("CLS");
		goto menu1;
	}

	else
	{
		system("CLS");
		goto ALGEBRAIC;
	}
}
break;

//ARC SINE
asin:case 5:
{
	cout << "Enter a number:" << endl;
	cin >> number1;
	cout << "The result is: " << asin(number1) * 180.0 / PI << endl;
	result << "Arc Sine" << endl;
	result << "The result is: " << asin(number1) * 180.0 / PI << endl << endl;
	cout << "Would you like to go to the main menu?" << endl;
	cout << "'y' = Main Menu | 'n' = Algebraic Menu" << endl;
	cin >> answer;
	if (answer == 'y')
	{
		system("CLS");
		goto menu1;
	}

	else
	{
		system("CLS");
		goto ALGEBRAIC;
	}
}
break;

//ARC TANGENT
atan:case 6:
{
	cout << "Enter a number:" << endl;
	cin >> number1;
	cout << "The result is: " << atan(number1) * 180.0 / PI << endl;
	result << "Arc Tangent" << endl;
	result << "The result is: " << atan(number1) * 180.0 / PI << endl << endl;
	cout << "Would you like to go to the main menu?" << endl;
	cout << "'y' = Main Menu | 'n' = Algebraic Menu" << endl;
	cin >> answer;
	if (answer == 'y')
	{
		system("CLS");
		goto menu1;
	}

	else
	{
		system("CLS");
		goto ALGEBRAIC;
	}
}
break;

//DEFAULT
default:
{
	cout << "Your choice does not match any of the presented options please try again." << endl;
	system("pause");
	system("CLS");
	goto secondswitcha;
}
}

//GEOMETRIC
GEOMETRIC://MAIN MENU
LOOP:cout << "MAIN MENU" << endl;
cout << "Select one of the following options: " << endl;
cout << "1. Area" << endl;
cout << "2. Volume" << endl;
cout << "0. GO BACK" << endl;
cin >> page;

if (page == 0)
{
	system("CLS");
	goto menu1;
}
else
if (page == 1)
{
	system("CLS");
	goto firstswitch;
}
else
if (page == 2)
{
	system("CLS");
	goto secondswitch;
}
else
{
	cout << "ERROR: Your selection did not match any of the given options. " << endl;
	system("PAUSE");
	system("CLS");
	goto LOOP;
}

//AREA MENU
firstswitch:cout << "AREA MENU" << endl;
cout << "Select one of the following options: " << endl << endl;
cout << "1. Parallelogram" << endl;
cout << "2. Triangle" << endl;
cout << "3. Triangle" << endl;
cout << "4. Circle" << endl;
cout << "0. GO BACK" << endl << endl;
cin >> choice;

switch (choice)//AREA
{
case 1:
{//PARALLELOGRAM
	cout << "PARALLELOGRAM" << endl << endl;
	cout << "Base: "; cin >> number1;
	cout << "Height: "; cin >> number2;
	cout << "Area: " << parallelogram(number1, number2) << endl;
	result << "Parallelogram:" << endl;
	result << "Area: " << parallelogram(number1, number2) << endl << endl;
	system("PAUSE");
	system("CLS");
	cout << "Would you like to go to the main menu?" << endl;
	cout << "'y' = Main Menu | 'n' = Geometric Menu" << endl;
	cin >> answer;
	if (answer == 'y')
	{
		system("CLS");
		goto menu1;
	}

	else
	{
		system("CLS");
		goto firstswitch;
	}

}
break;
case 2:
{//TRIANGLE
	cout << "TRIANGLE" << endl << endl;
	cout << "Base: "; cin >> number1;
	cout << "Height: "; cin >> number2;
	cout << "Area: " << triangle(number1, number2) << endl;
	result << "Triangle:" << endl;
	result << "Area: " << triangle(number1, number2) << endl << endl;
	system("PAUSE");
	system("CLS");
	cout << "Would you like to go to the main menu?" << endl;
	cout << "'y' = Main Menu | 'n' = Geometric Menu" << endl;
	cin >> answer;
	if (answer == 'y')
	{
		system("CLS");
		goto menu1;
	}

	else
	{
		system("CLS");
		goto firstswitch;
	}
}
break;
case 3:
{//TRAPEZOID
	cout << "TRAPEZOID" << endl << endl;
	cout << "Base A: "; cin >> number1;
	cout << "Base B: "; cin >> number2;
	cout << "Height: "; cin >> number3;
	cout << "Area: " << trapezoid(number1, number2, number3) << endl;
	result << "Trapezoid" << endl;
	result << "Area: " << trapezoid(number1, number2, number3) << endl << endl;
	system("PAUSE");
	system("CLS");
	cout << "Would you like to go to the main menu?" << endl;
	cout << "'y' = Main Menu | 'n' = Geometric Menu" << endl;
	cin >> answer;
	if (answer == 'y')
	{
		system("CLS");
		goto menu1;
	}

	else
	{
		system("CLS");
		goto firstswitch;
	}
}
break;
case 4:
{//CIRCLE
	cout << "CIRCLE" << endl << endl;
	cout << "Radius: "; cin >> number1;
	cout << "Area: " << circle(number1) << endl;
	result << "Circle:" << endl;
	result << "Area: " << circle(number1) << endl << endl;
	system("PAUSE");
	system("CLS");
	cout << "Would you like to go to the main menu?" << endl;
	cout << "'y' = Main Menu | 'n' = Geometric Menu" << endl;
	cin >> answer;
	if (answer == 'y')
	{
		system("CLS");
		goto menu1;
	}

	else
	{
		system("CLS");
		goto firstswitch;
	}
}
break;
case 0:
{//GO BACK
	system("CLS");
	goto LOOP;
}
break;
default:
{//DEFAULT ERROR
	cout << "Your choice did not match any of the given options. Please try again." << endl;
	system("PAUSE");
	system("CLS");
	goto firstswitch;
}
}




//VOLUME MENU
secondswitch: cout << "Select one of the following options: " << endl << endl;
cout << "1. Rectangular Prism" << endl;
cout << "2. Right Circular Cylinder" << endl;
cout << "3. Right Square Pyramid" << endl;
cout << "4. Right Circular Cone" << endl;
cout << "0. GO BACK" << endl << endl;
cin >> choice;

switch (choice)//VOLUME
{
case 1:
{//RECTANGULAR PRISM
	cout << "RECTANGULAR PRISM" << endl << endl;
	cout << "Length: "; cin >> number1;
	cout << "Width: "; cin >> number2;
	cout << "Height: "; cin >> number3;
	cout << "Volume: " << rectangular(number1, number2, number3) << endl;
	answer_v = rectangular(number1, number2, number3);
	result << "Rectangular Prism:" << endl;
	result << "Volume: " << rectangular(number1, number2, number3) << endl << endl;
	system("PAUSE");
	system("CLS");
	cout << "Would you like to go to the main menu?" << endl;
	arrayofshapes[0].volume[prism_v] = answer_v;
	prism_v++;
	cout << "'y' = Main Menu | 'n' = Geometric Menu" << endl;
	cin >> answer;
	if (answer == 'y')
	{
		system("CLS");
		goto menu1;
	}

	else
	{
		system("CLS");
		goto secondswitch;
	}
}
break;
case 2:
{//RIGHT CIRCULAR CYLINDER
	cout << "RIGHT CIRCULAR CYLINDER" << endl << endl;
	cout << "Radius: "; cin >> number1;
	cout << "Height: "; cin >> number2;
	cout << "Volume: " << cylinder(number1, number2) << endl;
	answer_v = cylinder(number1, number2);
	result << "Right Circular Cylinder:" << endl;
	result << "Volume: " << cylinder(number1, number2) << endl << endl;
	arrayofshapes[1].volume[cylinder_v] = answer_v;
	cylinder_v++;
	system("PAUSE");
	system("CLS");
	cout << "Would you like to go to the main menu?" << endl;
	cout << "'y' = Main Menu | 'n' = Geometric Menu" << endl;
	cin >> answer;
	if (answer == 'y')
	{
		system("CLS");
		goto menu1;
	}

	else
	{
		system("CLS");
		goto secondswitch;
	}
}
break;
case 3:
{//RIGHT SQUARE PYRAMID
	cout << "RIGHT SQUARE PYRAMID" << endl << endl;
	cout << "Base Edge: "; cin >> number1;
	cout << "Height: "; cin >> number2;
	cout << "Volume: " << pyramid(number1, number2) << endl;
	answer_v = pyramid(number1, number2);
	result << "Right Square Pyramid:" << endl;
	result << "Volume: " << pyramid(number1, number2) << endl << endl;
	arrayofshapes[2].volume[pyramid_v] = answer_v;
	pyramid_v++;
	system("PAUSE");
	system("CLS");
	cout << "Would you like to go to the main menu?" << endl;
	cout << "'y' = Main Menu | 'n' = Geometric Menu" << endl;
	cin >> answer;
	if (answer == 'y')
	{
		system("CLS");
		goto menu1;
	}

	else
	{
		system("CLS");
		goto secondswitch;
	}
}
break;
case 4:
{//RIGHT CIRCULAR CONE
	cout << "RIGHT CIRCULAR CONE" << endl << endl;
	cout << "Radius: "; cin >> number1;
	cout << "Height: "; cin >> number2;
	cout << "Volume: " << cone(number1, number2) << endl;
	answer_v = cone(number1, number2);
	result << "Right Circular Cone:" << endl;
	result << "Volume: " << cone(number1, number2) << endl << endl;
	arrayofshapes[3].volume[cone_v] = answer_v;
	cone_v++;
	system("PAUSE");
	system("CLS");
	cout << "Would you like to go to the main menu?" << endl;
	cout << "'y' = Main Menu | 'n' = Geometric Menu" << endl;
	cin >> answer;
	if (answer == 'y')
	{
		system("CLS");
		goto menu1;
	}

	else
	{
		system("CLS");
		goto secondswitch;
	}
}
break;
case 0:
{//GO BACK
	system("CLS");
	goto LOOP;
}
break;
default:
{//DEFAULT ERROR
	cout << "Your choice did not match any of the given options. Please try again." << endl;
	system("PAUSE");
	system("CLS");
	goto secondswitch;
}
}

system("PAUSE > NUL");
return 0;
}
}