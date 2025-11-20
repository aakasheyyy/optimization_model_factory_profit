COMPANY:CODTECH IT SOLUTIONS

NAME:AAKASH R

INTERN ID:CT04DR985

DOMAIN:DATA SCIENCE

DURATION:4 WEEKS

MENTOR:NEELA SANTHOSH


# optimization_model_factory_profit
A Linear Programming project using Python PuLP to maximize factory profit under labor and material constraints.
# Optimization Model: Maximizing Factory Profit

## Project Overview
This project demonstrates the application of **Linear Programming (LP)** to solve a **business optimization problem** using Python's `PuLP` library.  
The objective is to **maximize total profit** for a factory producing two products under limited resources such as labor hours and raw materials.  

By using optimization techniques, businesses can **efficiently allocate resources** to achieve the highest possible profit.

---

## Problem Description
A factory produces **Product A** and **Product B**. Each product requires **labor hours** and **raw materials**, and each has a **profit per unit**. The goal is to determine the **optimal number of units of each product** to produce to maximize total profit without exceeding the available resources.

**Product Details and Resource Requirements:**

| Product | Profit per unit ($) | Labor hours/unit | Material/unit |
|---------|------------------|-----------------|---------------|
| A       | 20               | 2               | 3             |
| B       | 30               | 4               | 2             |

**Available Resources:**  
- Labor hours = 100  
- Material = 90

---

## Linear Programming Formulation

**Decision Variables:**  
- `x` = number of units of Product A to produce  
- `y` = number of units of Product B to produce  

**Objective Function:**  
\[
\text{Maximize Profit } Z = 20x + 30y
\]

**Constraints:**  
1. Labor: \(2x + 4y \leq 100\)  
2. Material: \(3x + 2y \leq 90\)  
3. Non-negativity: \(x \geq 0, y \geq 0\)

This formulation ensures that production stays within resource limits while achieving maximum profit.

---

## Python Implementation (PuLP)

The project is implemented in **Google Colab** using Python's `PuLP` library.  

**Code Snippet:**

```python
import pulp

# Define the Linear Programming Problem
prob = pulp.LpProblem("Maximize_Profit", pulp.LpMaximize)

# Decision Variables
x = pulp.LpVariable('Product_A', lowBound=0, cat='Continuous')
y = pulp.LpVariable('Product_B', lowBound=0, cat='Continuous')

# Objective Function
prob += 20*x + 30*y, "Total Profit"

# Constraints
prob += 2*x + 4*y <= 100, "Labor Constraint"
prob += 3*x + 2*y <= 90, "Material Constraint"

# Solve the problem
prob.solve()

# Display Results
print("Status:", pulp.LpStatus[prob.status])
print("Produce {} units of Product A".format(x.varValue))
print("Produce {} units of Product B".format(y.varValue))
print("Maximum Profit = $", pulp.value(prob.objective))
How to Run

Open the notebook in Google Colab or Jupyter Notebook.

Install PuLP if not already installed:

!pip install pulp


Run all cells to see the optimal production plan, maximum profit, and visualization.

Repository Structure
optimization_model_factory_profit/
│
├── optimization_model_factory_profit.ipynb   # Main Colab notebook
├── README.md                                 # Project description (this file)
├── profit_chart.png (optional)               # Screenshot of the chart for README
