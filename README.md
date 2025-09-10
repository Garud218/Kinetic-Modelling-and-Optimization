# Kinetic-Modelling-and-Optimization
## Kinetic Modelling and Optimization of Series Reactions

This repository contains the MATLAB and Python code for a course project on kinetic modeling and optimization of a chemical reaction system. This project focuses on solving the system of ordinary differential equations (ODEs) that govern a complex series-parallel reaction network.

The primary goal is to implement and compare various numerical methods to simulate the concentration profiles of chemical species over time, providing insights for process optimization and chemical reactor design.

---

## 🧪 Problem Statement

The project aims to determine the solution for the following kinetic system:

A series reaction with a parallel step:
$$ A \xrightarrow{k_1} B \xrightarrow{k_2} C $$
$$ B \xrightarrow{k_3} D $$

This system is described by a set of four first-order ordinary differential equations:
* $dA/dt = -k_{1}A$
* $dB/dt = k_{1}A - k_{2}B - k_{3}B$
* $dC/dt = k_{2}B$
* $dD/dt = k_{3}B$

The simulation was run with the following initial conditions and parameters:
* **Initial Concentrations**: $A(0)=1$; $B(0)=0$; $C(0)=0$; $D(0)=0$
* **Rate Constants**: $k_1 = 2$, $k_2 = 0.5$, $k_3 = 0.3$
* **Time Span**: $t = 0$ to $t = 10$

---

## 💻 Methodology & Implementation

Kinetic models were built using **MATLAB and Python** to solve the system of ODEs. Three different numerical methods were implemented and analyzed:

* **Explicit Euler's Method**: The simplest numerical method, which approximates the solution by taking a small step in the direction of the derivative at the current point. It has a local truncation error of $O(h^2)$.

* **Implicit Euler's Method**: Approximates the derivative using a backward finite difference, requiring an iterative solver. In this project, the **Newton-Raphson method** was applied at each time step, which involves calculating the Jacobian matrix of the system. This method also has a local truncation error of $O(h^2)$.

* **4th Order Runge-Kutta (RK-4) Method**: A higher-order method that provides improved accuracy by using four intermediate slope calculations within each time step. It has a much smaller local truncation error of $O(h^5)$.

The solutions from these methods were compared against the results from MATLAB's built-in `ode45` solver to verify their accuracy.

---

## 📊 Key Findings & Conclusion

The project successfully modeled the kinetic system and offered several key insights:

* **Accuracy Comparison**: The **RK-4 method** was determined to be significantly more accurate than both the Explicit and Implicit Euler methods, which is expected due to its higher order and more complex algorithm.

* **Impact of Step Size (h)**: For all methods, the accuracy of the numerical solution was found to be inversely proportional to the step size; a smaller `h` yields a more accurate result.

* **Method Stability**: The **Implicit Euler method is unconditionally stable**, making it robust for stiff ODE systems. In contrast, the Explicit Euler and RK-4 methods are conditionally stable, meaning they can become unstable if the step size is too large.

Overall, this work demonstrates how kinetic modeling is a fundamental tool in chemical engineering for analyzing reaction mechanisms, optimizing operating conditions for maximum yield, and ensuring the efficient and safe design of chemical processes.
