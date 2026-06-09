# 11424114陳玟臻 工程數學第二次作業

This document contains the solutions for the specific math problems requested from the assignment: Problem 4 (Laplace Transform) and Problem 6 (Fourier Transform).

---

## Problem 4: Laplace Transform

### Problem Statement
Solve the following second-order linear homogeneous ordinary differential equation using the Laplace transform:
$$2\frac{d^2x}{dt^2} + 7\frac{dx}{dt} + 3x = 0$$

**Initial Conditions:**
$x(0) = 0$, $x'(0) = 1$

### Solution

**Step 1: Apply the Laplace transform to both sides of the equation.**
Let $X(s)$ be the Laplace transform of $x(t)$.
$$2[s^2X(s) - s x(0) - x'(0)] + 7[sX(s) - x(0)] + 3X(s) = 0$$

**Step 2: Substitute the initial conditions.**
Plug in $x(0) = 0$ and $x'(0) = 1$.
$$2[s^2X(s) - s(0) - 1] + 7[sX(s) - 0] + 3X(s) = 0$$
$$2[s^2X(s) - 1] + 7sX(s) + 3X(s) = 0$$

**Step 3: Solve for $X(s)$.**
Expand the terms:
$$2s^2X(s) - 2 + 7sX(s) + 3X(s) = 0$$
Group the $X(s)$ terms together:
$$X(s)(2s^2 + 7s + 3) = 2$$
Isolate $X(s)$:
$$X(s) = \frac{2}{2s^2 + 7s + 3}$$

**Step 4: Factor the denominator and use partial fractions.**
Factor the bottom part: $2s^2 + 7s + 3 = (2s + 1)(s + 3)$
$$X(s) = \frac{2}{(2s + 1)(s + 3)} = \frac{A}{2s + 1} + \frac{B}{s + 3}$$
Find $A$ and $B$:
$$2 = A(s + 3) + B(2s + 1)$$
* If $s = -3$: $2 = B(-5) \implies B = -0.4$
* If $s = -0.5$: $2 = A(2.5) \implies A = 0.8$

So, the equation becomes:
$$X(s) = \frac{0.8}{2s + 1} - \frac{0.4}{s + 3}$$
To match standard Laplace tables, divide the top and bottom of the first fraction by $2$:
$$X(s) = \frac{0.4}{s + 0.5} - \frac{0.4}{s + 3}$$

**Step 5: Apply the Inverse Laplace transform.**
Using the standard formula $\mathcal{L}^{-1}\{\frac{1}{s - a}\} = e^{at}$:
$$x(t) = 0.4e^{-0.5t} - 0.4e^{-3t}$$

**Final Answer:**
$$x(t) = 0.4(e^{-0.5t} - e^{-3t}) \quad \text{for } t \ge 0$$

---

## Problem 6: Fourier Transform

### Problem Statement
Given the function $f(t) = te^{-5t}$.
Find the Fourier representation of the function $f$. 

*(Note: The original text asks for a "Fourier series", but because the function is not periodic and has no given interval, this is solved as a standard continuous **Fourier Transform** problem assuming $t \ge 0$, which is common in engineering exams.)*

### Solution

**Step 1: Define the function properly.**
Assume $f(t) = te^{-5t}u(t)$, where $u(t)$ is the unit step function (meaning the function is only active for $t \ge 0$).

**Step 2: Use standard Fourier Transform formulas.**
We know the basic Fourier Transform pair for an exponential decay function:
$$\mathcal{F}\{e^{-at}u(t)\} = \frac{1}{a + j\omega}$$

We also know the "Multiplication by $t$" property of the Fourier Transform:
$$\mathcal{F}\{t \cdot g(t)\} = j \frac{d}{d\omega} G(\omega)$$

**Step 3: Apply the property to our function.**
Let $g(t) = e^{-5t}u(t)$. Therefore, $G(\omega) = \frac{1}{5 + j\omega}$.
Now, apply the derivative property to find the transform of $t \cdot e^{-5t}$:
$$\mathcal{F}\{t \cdot e^{-5t}\} = j \frac{d}{d\omega} \left( \frac{1}{5 + j\omega} \right)$$

Use the chain rule for the derivative:
$$\frac{d}{d\omega} (5 + j\omega)^{-1} = -1 \cdot (5 + j\omega)^{-2} \cdot j = \frac{-j}{(5 + j\omega)^2}$$

**Step 4: Multiply by $j$.**
$$\mathcal{F}\{f(t)\} = j \cdot \left( \frac{-j}{(5 + j\omega)^2} \right)$$
Since $j \cdot -j = -j^2 = -(-1) = 1$:
$$F(\omega) = \frac{1}{(5 + j\omega)^2}$$

**Final Answer:**
The Fourier Transform is:
$$F(\omega) = \frac{1}{(5 + j\omega)^2}$$
