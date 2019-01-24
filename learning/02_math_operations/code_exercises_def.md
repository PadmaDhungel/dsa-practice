A collection of beginner-friendly Python programs to practice numerical operations and formulas. These are the same problems, rewritten to make it modular or by function, so we can reuse it elsewhere.  

>One thing may appear inconsistent, how return statements are written. Sometimes the return contains the full calculation directly, while other times it returns a variable holding the result computed earlier.

*In the beginning, it’s good practice to store calculations in variables and then return those variables when the logic involves multiple steps. For simple one-liner calculations that don’t span the width of the page, you can return the expression directly. Both ways are possible, but this approach helps build clearer and more manageable code early on.*
### ~ Km to miles conversion
You are given distance in km unit, and have to convert it in miles
```
def km_to_miles(km):
    return km * 0.621371
km = float(input("Enter distance in kilometers: "))
miles = km_to_miles(km)
print("Distance in miles:", miles)
```
### ~ Calculation of speed
You are given distance and time, and have to calculate its speed. The formuala is speed = distance/time
```
def speed(distance,time):
    return distance / time ## for time 0, raises zero division error

distance = float(input("Enter distance (in km): "))
time = float(input("Enter time (in hours): "))
speed = speed(distance,time)
print("Speed is", speed, "km/h")
```
### ~ Convert Celsius to Fahrenheit
You are given temperature value in celsius and are to convert into Fahrenheit. The formula is (celsius * 9/5) + 32
```
def celsius_to_fahrenheit(celsius):
    return (celsius * 9/5) + 32
celsius = float(input("Enter temperature in Celsius: "))
fahrenheit = celsius_to_fahrenheit(celsius)
print("Temperature in Fahrenheit:", fahrenheit)
```
### ~ Simple Interest Calculator
You are given principal(P) and rate (R) and time(T), and are to calculate the simple interest. The formula is (p*t*r)/100
Formula:
Simple Interest = (P × R × T) / 100
```
def simple_interest(principal,time,rate):
    return principal*time*rate/100
principal = float(input("Enter principal amount: "))
rate = float(input("Enter rate of interest: "))
time = float(input("Enter time in years: "))
simple_interest_value = simple_interest(principal,time,rate)
print("Simple Interest is:", simple_interest_value)
```
### ~ Area and perimeter calculation
You are given the length and breadth of a table, you are to calculate area and perimeter. Area of rectangle shape is length*breadth and perimeter is 2 * (length + breadth)
```
def area(length,breadth):
    return length * breadth
def perimeter(length, breadth):
    return 2 * (length + breadth)
length = float(input("Enter length: "))
width = float(input("Enter width: "))
area = area(length, width)
perimeter = perimeter(length, width)
print("Area:", area)
print("Perimeter:", perimeter)
```
### ~ Average of Three Numbers or mean
You are given three numbers a, b and c, the average is calculated using (a + b + c)/3
```
def average_of_three(a, b, c):
    return (a + b + c) / 3
first = float(input("Enter first number: "))
second = float(input("Enter second number: "))
third = float(input("Enter third number: "))
average = average_of_three(first, second, third)
print("Average is:", average)
```
### ~ Area of a Circle
You are given the radius and are to calculate the area. The formula is pi*radius^2 -> π × r²
```
import math
def area_of_circle(radius):
    return math.pi * radius ** 2
radius = float(input("Enter radius of the circle: "))
area = area_of_circle(radius)
print("Area of the circle:", area)
```
### ~ Volume of a Cube
You are given the length of one side of a cube and need to calculate its volume. The formula is side³
```
def volume_of_cube(side):
    return side ** 3
side = float(input("Enter the side length of the cube: "))
volume = volume_of_cube(side)
print("Volume of the cube:", volume)
```
### ~ Pythagorean Theorem (find hypotenuse)
You are given two sides (A and B) of a right-angled triangle. Use the Pythagorean Theorem to calculate the hypotenuse. The formula is √(a² + b²)
```
import math

def pythagorean_theorem(a, b):
    hypotenuse = math.sqrt(a ** 2 + b ** 2)
    return hypotenuse
a = float(input("Enter side A: "))
b = float(input("Enter side B: "))
c = pythagorean_theorem(a, b)
print("Hypotenuse is:", c)
```
### ~ BMI Calculator
You are given a person’s weight and height, and are to calculate their BMI (Body Mass Index). The formula is weight / height²
```
def bmi_calculator(weight, height):
    bmi = weight / (height ** 2)
    return bmi
weight = float(input("Enter your weight (in kg): "))
height = float(input("Enter your height (in meters): "))
bmi = bmi_calculator(weight, height)
print("Your BMI is:", bmi)
```

### ~ Convert Seconds to Hours, Minutes, and Seconds
You are given total seconds. Convert them to hours, minutes, and seconds using integer division and modulo
```
def convert_seconds(total_seconds):
    hours = total_seconds // 3600
    minutes = (total_seconds % 3600) // 60
    seconds = total_seconds % 60
    return hours, minutes, seconds

total_seconds = int(input("Enter total seconds: "))
result = convert_seconds(total_seconds)
#Unpack returned tuple into separate variables h, m, s
h,m,s = result
print("Time is:", h, "hrs", m, "min", s, "sec")

```

### ~ Swap Two Variables
You are given two values, a and b, and are to swap them using tuple unpacking
```
def swap_variables(a, b):
    a, b = b, a
    return a, b
a = float(input("Enter first number: "))
b = float(input("Enter second number: "))
a, b = swap_variables(a, b)
print("After swapping:")
print("First number:", a)
print("Second number:", b)
```
### ~ Sum of n terms of an Arithmetic Progression
You are given the first term a, common difference d, and number of terms n. Calculate the sum of the first n terms using the formula (2a+(n−1)d).
```
def sum_of_ap(a, d, n):
    sum_ap = (n / 2) * (2 * a + (n - 1) * d)
    return sum_ap
a = float(input("Enter the first term (a): "))
d = float(input("Enter the common difference (d): "))
n = int(input("Enter the number of terms (n): "))

sum_ap = sum_of_ap(a, d, n)
print("Sum of the arithmetic progression:", sum_ap)
```