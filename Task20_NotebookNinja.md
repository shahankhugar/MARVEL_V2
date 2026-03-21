# Task 20 — Notebook Ninja: Getting Started with Jupyter

**Name:** Shashank Hugar
**Program:** UVCE MARVEL AI/ML — Level 1
**Status:** ✅ Completed

---

## What is Jupyter Notebook?

Jupyter Notebook is an open-source, browser-based tool that allows you to write and run code, see its output, and document your thought process — all in the same file. Unlike a regular Python script which is just code, a Jupyter notebook is an interactive document that combines code cells, output, and formatted text in one place.

This makes it the standard tool in data science and machine learning. A notebook tells a complete story — the problem, the approach, the code, the results, and the conclusion — in a single readable document that anyone can open and follow without running anything.

---

## Two Types of Cells

A Jupyter notebook is made of cells. Every cell is either one of two types:

**Code cell** — contains Python code. When you run it, the output appears directly below the cell. This could be printed text, a number, a table, or a graph.

**Markdown cell** — contains formatted text written in Markdown. When you run it, it renders as a clean, formatted document — headings, bullet points, bold text, images, code snippets. No code executes here, it is purely for documentation and presentation.

Mixing these two types correctly is what makes a notebook professional and readable.

---

## Quest 1 — Markdown and Presentation

The notebook was structured using Markdown cells to demonstrate formatting skills:

A title and section headers were added using `#` and `##` syntax. Headers create visual hierarchy and make the notebook easy to navigate.

A bullet list of three learning goals was added using `-` syntax — how to build machine learning models, how to analyze real-world datasets, and how to visualize data using Python.

Text was formatted using `**bold**` and `*italics*`. A horizontal divider was added using `---`.

An image was embedded using the Markdown image syntax. A code snippet was displayed inside triple backticks — demonstrating how to show code as documentation without actually running it.

---

## Quest 2 — Python Coding and Visualization

**Variables and Calculation**

Three variables were declared — name, age, and GPA. A calculation was performed multiplying age by GPA, and the results were printed using f-strings:

```python
name = "Shashank"
age = 20
gpa = 8.5
result = age * gpa
print(f"Age x GPA = {result}")
```

Output: `Age x GPA = 170.0`

This demonstrates basic Python variable declaration, arithmetic operations, and formatted string output.

**Matplotlib Line Plot**

A line graph was plotted showing learning progress over 6 months using Matplotlib:

```python
months = ["Jan", "Feb", "Mar", "Apr", "May", "Jun"]
scores = [55, 62, 70, 75, 85, 92]

plt.plot(months, scores, marker="o", color="purple", linewidth=2)
plt.title("My Learning Progress Over 6 Months")
plt.xlabel("Month")
plt.ylabel("Score")
plt.grid(True)
plt.show()
```

The graph shows a steady upward trend in scores from January to June. `plt.plot()` draws the line, `marker="o"` adds dots at each data point, and `plt.grid()` adds the background grid for readability.

---

## Why Jupyter is Important for AI/ML

In machine learning workflows, notebooks are used at every stage — loading and exploring data, cleaning it, training models, evaluating results, and presenting findings. The ability to run one cell at a time and see intermediate results makes debugging and experimentation much faster than running full scripts.

The habit of documenting each step with Markdown — explaining what you are doing and why — is what separates a readable notebook from a messy collection of code. This task built that habit from the beginning.

---

## Key Takeaways

Jupyter Notebook combines code, output, and documentation in a single interactive document. Markdown cells handle formatting and explanation while code cells handle execution. A well-structured notebook should be understandable to someone reading it without running any code. This is the standard workflow for data science, machine learning, and research in Python.

---

## Notebook

https://github.com/shahankhugar/UVCE-MARVEL-AI-ML-001/blob/main/Notebook_ninja_.ipynb
