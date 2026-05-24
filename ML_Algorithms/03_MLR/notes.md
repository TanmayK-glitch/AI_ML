### Multiple Linear Regression ###

# Intuition
- The intuition behind Multiple Linear Regression is a direct expansion of Simple Linear Regression, but adapted for real-world scenarios where you have more than one input column (independent variable) to predict an output.
- However, if you have two inputs (e.g., predicting LPA based on both CGPA and IQ), the data becomes 3D. Instead of drawing a line, your model now draws a 2D Plane that cuts through the scattered data points floating in 3D space

# Basic maths behind MLR
- The mathematics of Multiple Linear Regression shifts from the simple line equation to a broader equation that accounts for multiple features.
- For n-dimentional dataset the equation will be:
    ycap = w1x1 + w2x2 + w3x3 +.... wnxn + w0
    Here: ycap -> is the output given by the model.
          w -> weight of each feature 
          x -> feature (input column)
          w0 -> bias(shifts the plan to get the best fit line)

- 
