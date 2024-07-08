### Introduction

Unlike the previous Challenge, this gives you a direct list of requirements, which may seem like more guidance than the average exercise, but is fairly more complicated and lengthy than most exercises.

> [!tip] Alternative Challenge
> If you don't like this kind of exercise, feel free to skip it.
> You can try to create a short text based game instead.

### Challenge: Pizza orders

Create a fixed list of pizza flavors, then use `input()` to ask users to specify their order, followed by conditional statements to validate if their answers are valid.

The program must ask the following questions:

- Which shape the Pizza should be, out of `{"square", "circle"}`
	- Some later steps will depend on this choice, including the questions prompted to the user.
- Which Pizza flavor the user wants.
	- Remember to display the list of offered flavors.
- What should be the size of the Pizza
	- If the shape is a circle, it should ask the diameter of the pizza
	- If the shape is a square, it should ask the side of the pizza

And it has to validate if:
- The shape is valid (either square or circle)
- The flavor is within the list of offered flavors
- The **area** of the pizza is between a minimum and a maximum value determined by you

If it passes all conditions, print the final order.
The valid flavors and output format is up to you, but some examples that would be considered passing:
```
Confirming Order: A square peperoni pizza with side 10cm and area 100cm2
```
```
Confirming Order: A circular Calabresa Pizza with diameter 10in and area 78in2
```

Remember to test your program against multiple inputs, both passing and failure cases.

> [!tip] Behavior on Failure
> The simplest way to reject input is calling `print()` to show an error message, then call `exit()` to close the program.
> Alternatively, you can use exceptions such as `raise Exception("Invalid Shape")`, but we'll only cover them later.
> You can also opt not exit the program, but rather continue asking until the user provides a valid input. We'll see that in the next chapter, but feel free to use a `while` loop if you already know how to use them.

