*A collection of beginner-friendly Python programs to practice numerical operations and formulas without using conditionals or loops.*
### ~ Km to miles conversion
You are given distance in km unit, and have to convert it in miles
```
km = float(input("Enter distance in kilometers: "))
miles = km * 0.621371
print("Distance in miles:", miles)
```
### ~ Calculation of speed
You are given distance and time, and have to calculate its speed. The formuala is speed = distance/time
```
distance = float(input("Enter distance (in km): "))
time = float(input("Enter time (in hours): "))
speed = distance / time ## for time 0, raises zero division error
print("Speed is", speed, "km/h")
```
### ~ Convert Celsius to Fahrenheit
You are given temperature value in celsius and are to convert into Fahrenheit. The formula is (celsius * 9/5) + 32
```
celsius = float(input("Enter temperature in Celsius: "))
fahrenheit = (celsius * 9/5) + 32
print("Temperature in Fahrenheit:", fahrenheit)
```
### ~ Simple Interest Calculator
You are given principal(P) and rate (R) and time(T), and are to calculate the simple interest. The formula is (p*t*r)/100
Formula:
Simple Interest = (P × R × T) / 100
```
principal = float(input("Enter principal amount: "))
rate = float(input("Enter rate of interest: "))
time = float(input("Enter time in years: "))
simple_interest = (principal * rate * time) / 100
print("Simple Interest is:", simple_interest)
```
### ~ Area and perimeter calculation
You are given the length and breadth of a table, you are to calculate area and perimeter. Area of rectangle shape is length*breadth and perimeter is 2 * (length + breadth)
```
length = float(input("Enter length: "))
width = float(input("Enter width: "))
area = length * width
perimeter = 2 * (length + width)
print("Area:", area)
print("Perimeter:", perimeter)
```
### ~ Average of Three Numbers or mean
You are given three numbers a, b and c, the average is calculated using (a + b + c)/3
```
a = float(input("Enter first number: "))
b = float(input("Enter second number: "))
c = float(input("Enter third number: "))
average = (a + b + c) / 3
print("Average is:", average)
```
### ~ Area of a Circle
You are given the radius and are to calculate the area. The formula is pi*radius^2 -> π × r²
```
import math
radius = float(input("Enter radius of the circle: "))
area = math.pi * radius ** 2
print("Area of the circle:", area)
```
### ~ Volume of a Cube
You are given the length of one side of a cube and need to calculate its volume. The formula is side³
```
side = float(input("Enter the side length of the cube: "))
volume = side ** 3
print("Volume of the cube:", volume)
```
### ~ Pythagorean Theorem (find hypotenuse)
You are given two sides (A and B) of a right-angled triangle. Use the Pythagorean Theorem to calculate the hypotenuse. The formula is √(a² + b²)
```
import math
a = float(input("Enter side A: "))
b = float(input("Enter side B: "))
c = math.sqrt(a**2 + b**2)
print("Hypotenuse is:", c)
```
### ~ BMI Calculator
You are given a person’s weight and height, and are to calculate their BMI (Body Mass Index). The formula is weight / height²
```
weight = float(input("Enter your weight (in kg): "))
height = float(input("Enter your height (in meters): "))
bmi = weight / height**2
print("Your BMI is:", bmi)
```

### ~ Convert Seconds to Hours, Minutes, and Seconds
You are given total seconds. Convert them to hours, minutes, and seconds using integer division and modulo
```
total_seconds = int(input("Enter total seconds: "))
hours = total_seconds // 3600
minutes = (total_seconds % 3600) // 60
seconds = total_seconds % 60
print("Time is:", hours, "hrs", minutes, "min", seconds, "sec")
```

### ~ Swap Two Variables
You are given two values, a and b, and are to swap them using tuple unpacking
```
a = float(input("Enter first number: "))
b = float(input("Enter second number: "))
a, b = b, a
print("After swapping:")
print("First number:", a)
print("Second number:", b)
```
### ~ Sum of n terms of an Arithmetic Progression
You are given the first term a, common difference d, and number of terms n. Calculate the sum of the first n terms using the formula (2a+(n−1)d).
```
a = float(input("Enter the first term (a): "))
d = float(input("Enter the common difference (d): "))
n = int(input("Enter the number of terms (n): "))

sum_ap = (n / 2) * (2 * a + (n - 1) * d)
print("Sum of the arithmetic progression:", sum_ap)
```