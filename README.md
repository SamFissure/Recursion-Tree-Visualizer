# Recursion Visualiser  
Recursion visualiser is a python tool that visualizes recursion tree with animation and draws recursion tree for recursive function.
It works with almost any type of recursive function.
Just add the recursion-visualiser decorator to your function and let it do the rest of the work.

  
  ## Installation  
The only dependency for recursion visualiser is Graphviz which you can download from [here](https://www.graphviz.org/download/)  
  
- Download  [graphviz binary](https://www.graphviz.org/download/)  
- Add graphviz bin to path manually or by adding the following line on your script. Change the installation directory according to your installation path  
  
```  
# Set it to bin folder of graphviz  
os.environ["PATH"] += os.pathsep +  'C:/Program Files (x86)/Graphviz2.38/bin/'  
```  

  
The easiest way to  install ```recursion-visualiser``` package is from [pypi](https://pypi.org/project/recursion-visualiser/)
```
pip install recursion-visualiser
```
The preferred way to import the class from the package is as:
```python
from visualiser.visualiser import Visualiser as vs
```
## Example  
### 1.  Fibonacci  
Let's draw the recursion tree for fibonacci number.  
Here is how the simple code looks like  
```python  
def fib(n):  
    if n <= 1: 
        return n 
    return fib(n - 1) + fib(n - 2)  

print(fib(6))  
```  
  
Now we want to draw the recursion tree for this function. It is as simple as adding a decorator  
```python  
# Author: Bishal Sarang

# Import Visualiser class from module visualiser
from visualiser.visualiser import Visualiser as vs

# Add decorator
# Decorator accepts arguments: ignore_args and show_argument_name
@vs()
def fib(n):
    if n <= 1:
        return n
    return fib(n=n - 1) + fib(n=n - 2)


def main():
    # Call function
    print(fib(n=6))
    # Save recursion tree to a file
    vs.make_animation("fibonacci.gif", delay=2)


if __name__ == "__main__":
    main()
```  
Here are the changes required:  
 
 - Add decorator Visualiser which accepts optional arguments `ignore_args`, `show_argument_name`  and 'show_return_value'   
 - Change every function calls to pass as keyword arguments.  
 - Make_animation
  
 The output image are saved as "fibonacci.gif" and "fibonacci.png"
 
Here is how the recursion tree looks like:  
Animation:
![enter image description here](https://github.com/sarangbishal/Recursion-Visualizer/blob/master/examples/fibonacci.gif)  
  
![enter image description here](https://github.com/sarangbishal/Recursion-Visualizer/blob/master/examples/fibonacci.png)  

## 2. Make sum  
This is taken from one of my answers on quora where I had to manually  draw recursion tree. Using Visualiser with very less changes I was able to draw the following tree. You can compare the tree [here](https://qr.ae/TltTCV)  
![enter image description here](https://github.com/sarangbishal/Recursion-Visualizer/blob/master/examples/make_sum.png)  
  
  
  
## TODO:  
 - [x] Minimal working version  
 - [x] Upload package to pypi  
 - [x] Support animation
 - [ ] Support aliasing for function name
 - [ ] Show repeated states
 - [ ] Support node_color, backgroundcolor etc
 - [ ] Refactor  
 - [ ] Handle base cases  
 - [ ] Make more beautiful trees