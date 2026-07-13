import math

# Define methods
def bisection_method(f, low, high, tol, max_iter):
    for _ in range(max_iter):
        mid = (low + high) / 2
        if f(mid) == 0 or abs(high - low) < tol:
            return mid
        elif f(low) * f(mid) < 0:
            high = mid
        else:
            low = mid
    return mid

def secant_method(f, x0, x1, tol, max_iter):
    for _ in range(max_iter):
        if abs(x1 - x0) < tol:
            return x1
        x_temp = x1 - f(x1) * (x1 - x0) / (f(x1) - f(x0))
        x0, x1 = x1, x_temp
    return x1

def false_position_method(f, low, high, tol, max_iter):
    for _ in range(max_iter):
        f_low, f_high = f(low), f(high)
        x_new = low - f_low * (high - low) / (f_high - f_low)
        if abs(f(x_new)) < tol or abs(high - low) < tol:
            return x_new
        elif f(low) * f(x_new) < 0:
            high = x_new
        else:
            low = x_new
    return x_new

def newton_raphson_method(f, f_prime, x0, tol, max_iter):
    x = x0
    for _ in range(max_iter):
        x_new = x - f(x) / f_prime(x)
        if abs(x_new - x) < tol:
            return x_new
        x = x_new
    return x

# Parse and compile function
def parse_function(equation):
    # Return a function that takes x and evaluates the equation
    return lambda x: eval(equation)

# Main program
method_choice = input("Choose a method:\n1. Bisection\n2. Secant\n3. False Position\n4. Newton-Raphson\nEnter number: ")
equation = input("Enter the equation in terms of x (e.g., x**2 - 4*x + 4): ")

stop_choice = input("Choose stopping criteria:\n1. Tolerance\n2. Max Iterations\nEnter number: ")
tol = max_iter = None
if stop_choice == '1':  # Tolerance-based stopping
    tol = float(input("Enter tolerance (e.g., 0.05): "))
    max_iter = 1000  # Set a default max iteration if only tolerance is chosen
elif stop_choice == '2':  # Max iterations-based stopping
    max_iter = int(input("Enter maximum iterations: "))
    tol = 1e-5  # Set a default tolerance if only max iterations are chosen
else:
    print("Invalid stopping criteria choice.")
    exit()

f = parse_function(equation)

result = None
if method_choice == '1':  # Bisection Method
    low = float(input("Enter start of interval (low): "))
    high = float(input("Enter end of interval (high): "))
    result = bisection_method(f, low, high, tol, max_iter)
elif method_choice == '2':  # Secant Method
    x0 = float(input("Enter first initial guess (x0): "))
    x1 = float(input("Enter second initial guess (x1): "))
    result = secant_method(f, x0, x1, tol, max_iter)
elif method_choice == '3':  # False Position Method
    low = float(input("Enter start of interval (low): "))
    high = float(input("Enter end of interval (high): "))
    result = false_position_method(f, low, high, tol, max_iter)
elif method_choice == '4':  # Newton-Raphson Method
    x0 = float(input("Enter initial guess (x0): "))
    
    # Derivative function for Newton-Raphson
    h = 1e-5  # Small step for numerical derivative
    f_prime = lambda x: (f(x + h) - f(x)) / h
    
    result = newton_raphson_method(f, f_prime, x0, tol, max_iter)
else:
    print("Invalid method choice.")
    exit()

print("Root found:", result)
