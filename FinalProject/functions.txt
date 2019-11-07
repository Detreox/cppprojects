//GEOMETRIC
//AREA
#define PI 3.141592653589793238462
//PARALLELOGRAM
double parallelogram(double number1, double number2)
{
	return number1 * number2;
}
//TRIANGLE
double triangle(double number1, double number2)
{
	return (number1 * number2) / 2;
}
//TRAPEZOID
double trapezoid(double number1, double number2, double number3)
{
	return ((number1 + number2) / 2) * number3;
}
//CIRCLE
double circle(double number1)
{
	return (number1 * number1) * PI;
}
//VOLUME

//RECTANGULAR PRISM
double rectangular(double number1, double number2, double number3)
{
	return number1 * number2 * number3;
}
//RIGHT CIRCULAR CYLINDER
double cylinder(double number1, double number2)
{
	return (number1 * number1) * number2 * PI;
}
//RIGHT SQUARE PYRAMID
double pyramid(double number1, double number2)
{
	return (number1 * number1) * (number2 / 3);
}
//RIGHT CIRCULAR CONE
double cone(double number1, double number2)
{
	return (number1 * number1) * (number2 / 3) * PI;
}

//ALGEBRAIC
//ADDITION
double add(double number1, double number2)
{
	return number1 + number2;
}
//SUBTRACTION
double subt(double number1, double number2)
{
	return number1 - number2;
}
//MULTIPLY
double mult(double number1, double number2)
{
	return number1 * number2;
}
//DIVISION
double divi(double number1, double number2)
{
	if (number2 == 0)
		return -1;

	return number1 / number2;
}
//SQUARE
double sqr(double number1)
{
	return number1 * number1;
}
//FACTORIAL
long long int fact(long long int factorial)
{
	if (factorial == 0)
	{
		return 1;
	}
	return factorial * fact(factorial - 1);
}