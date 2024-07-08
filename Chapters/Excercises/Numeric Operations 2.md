### Exercise 1.1 - Square Properties
Create a function to calculate each each of the following properties of a square given its other measurements:
- diagonal from side
- side from diagonal
- perimeter from side
- side from perimeter
- area from side
- side from area

Then test each of them for multiple values

### Exercise 1.2 - Circle Properties
Create a function to calculate each of the following properties of a circle given its other measurements:
- diameter from radius
- radius from diameter
- perimeter from radius
- radius from perimeter
- area from radius
- radius from area

Then test each of them for multiple values

> [!tip] The value of Pi
> You can use an approximation of `pi = 3.14` or use `from math import pi`

### Exercise 2 - Chaining Functions

Using only the functions you defined above, create a function to calculate the perimeter of a square [inscribed](https://en.wikipedia.org/wiki/Inscribed_figure) within a circle given that circle's radius.

> [!tip]+
> Image to help visualize the problem (the blue square is inscribed within the green circle, and the green line connecting to the center of the image is the circle's radius)
> ![[Excalidraw/Numeric Operations 2 2024-05-20 01.55.36.excalidraw]]

%%TODO LOOK UP HOW TO INSERT ALT TEXT
Image showing a Blue Square inscribed inside of a Green Circle
%%

> [!caution]- Solution
> The diagonal of the square is the same as the diameter of the circle.
> A correct answer should give you `perimeter = {TODO CALCULATE AND INSERT EXPECTED ANSWER}` for `radius = 10`.
> > [!error]- Show code
> > First, you have to calculate the circle's diameter:
> > `diameter = diameter_from_radius(radius)`
> > Then, you have to calculate the side of the squared based on that:
> > `side = side_from_diagonal(diameter)`
> > At least, you can calculate the square's perimeter:
> > `perimeter = perimeter_from_side(side)`
> > You can call your functions `x_from_y` or `y_to_x` or even something else, as long as they're doing the right operations

