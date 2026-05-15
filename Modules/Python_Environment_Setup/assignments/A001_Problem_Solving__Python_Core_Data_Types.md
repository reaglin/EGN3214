# Python Core Data Types & Operators: Engineering Problem-Solving Exercise

**Module:** Python Environment Setup
**Assignment Type:** Problem-Solving Exercise
**Estimated Time:** 2–4 Hours
**Submission Format:** Shared Google Colab Notebook Link (viewable as a webpage)

---

## Purpose — Why This Assignment Matters

Engineering analysis depends on precise numerical reasoning and clear communication of results. Python has become one of the most widely used tools in engineering practice precisely because it combines readable code with powerful numeric computation. In this assignment, you will use Python's core data types and operators inside a Google Colab notebook to solve a realistic structural-load engineering problem.

By completing this exercise, you will practice the same workflow used by practicing engineers who write Python scripts to automate calculations, document assumptions, and communicate results to colleagues — all in a single shareable document. This assignment directly supports the module's learning goals of applying Python's built-in types and operators to solve and document real computational problems.

---

## Learning Outcomes

By the end of this assignment, you will be able to:

1. **Declare** correctly typed Python variables (`int`, `float`, `str`, `bool`, and `None`) to represent engineering quantities and metadata.
2. **Apply** Python arithmetic, comparison, and logical operators to compute structural load calculations across a multi-step engineering problem.
3. **Verify** intermediate and final results using the `type()` and `isinstance()` functions to confirm that computed values carry the expected data types.
4. **Construct** a fully documented Google Colab notebook that communicates problem setup, calculations, and engineering conclusions to a technical audience using Markdown text cells and well-commented code cells.

---

## Background — The Engineering Scenario

You are a junior engineer at a structural consulting firm. A client is building a **single-story rectangular warehouse** and needs you to calculate the **total load acting on the building's roof**, then determine whether the roof structure can safely support that load.

The roof must carry three types of loads:

| Load Type | Symbol | Description |
|---|---|---|
| Dead load | `D` | Weight of the roof structure itself (permanent) |
| Live load | `L` | Temporary loads (people, equipment during maintenance) |
| Snow load | `S` | Accumulated snow on the roof surface |

The **total factored load** on the roof is calculated using a standard load combination formula from structural engineering practice:

```
factored_load = 1.2 × D + 1.6 × L + 0.5 × S
```

> **What "factored" means:** Load factors (1.2, 1.6, 0.5) are safety multipliers required by building codes. They account for uncertainty and variability in each load type. You do not need to derive these factors; use them exactly as shown.

The **total force on the entire roof** is:

```
total_force = factored_load × roof_area
```

The roof has a **design capacity** — the maximum load per unit area it was engineered to withstand. You must determine whether the calculated factored load **exceeds** the design capacity and produce a clear, documented conclusion.

---

## Given Values

Use **exactly** the values in the table below. Do not change them.

| Variable Name | Value | Unit | Python Type to Use |
|---|---|---|---|
| `D` | 1.20 | kPa (kiloPascals) | `float` |
| `L` | 0.96 | kPa | `float` |
| `S` | 1.44 | kPa | `float` |
| `roof_length` | 45 | meters | `int` |
| `roof_width` | 30 | meters | `int` |
| `design_capacity` | 6.50 | kPa | `float` |
| `project_name` | `"Warehouse Roof Load Analysis"` | — | `str` |
| `engineer_name` | Your full name | — | `str` |
| `analysis_complete` | `False` (update to `True` after final calculation) | — | `bool` |
| `notes` | `None` (update with a string conclusion at the end) | — | `None` → `str` |

---

## Task — Step-by-Step Instructions

> **How to read these instructions:** Each numbered step maps to one or more cells in your Colab notebook. Steps marked **[Text Cell]** require a Markdown text cell. Steps marked **[Code Cell]** require a Python code cell. Every code cell must include inline comments (lines beginning with `#`) explaining what each line does.

---

### Step 1 — Create and Set Up Your Colab Notebook [Text Cell + Code Cell]

**1a.** Open [Google Colab](https://colab.research.google.com) and create a new notebook. Rename it:
```
LastName_FirstName_RoofLoadAnalysis.ipynb
```

**1b.** In the **first cell**, insert a **Text (Markdown) cell** that includes all of the following, each as its own labeled section:

- A top-level heading (`#`) with the project name: *Warehouse Roof Load Analysis*
- **Engineer:** Your full name
- **Date:** The date you completed the notebook
- **Problem Description:** Write 3–5 sentences in your own words explaining the engineering problem — what is being calculated, why it matters, and what the outcome of the analysis will tell the client. Do not copy the background section verbatim; paraphrase it.
- **Variable Dictionary:** A table listing every variable from the Given Values table above, including its name, value, unit, Python type, and a plain-English description of what it represents physically.

> **Defining "Variable Dictionary":** A variable dictionary is a reference table that explains every variable used in your code so that any reader — even one who cannot read Python — understands what each piece of data represents.

---

### Step 2 — Declare All Variables [Code Cell]

**2a.** Create a **Code Cell** titled with a comment: `# Step 2: Variable Declarations`

**2b.** Declare every variable from the Given Values table using correct Python syntax. Requirements:

- Numeric variables must use the exact Python type specified (`int` or `float`). For example, `roof_length = 45` stores an integer; `D = 1.20` stores a float.
- `project_name` and `engineer_name` must be assigned as string literals.
- `analysis_complete` must be assigned the boolean value `False`.
- `notes` must be assigned the value `None`.
- Every variable declaration must have an inline comment explaining the variable and its unit.

**2c.** Immediately after all declarations, use the `type()` function to **print the data type of every variable**. Format each print statement so the output clearly labels which variable is being reported. Example format:

```python
print("Type of D:", type(D))
```

> **Why type-checking here?** Verifying types immediately after declaration is a professional habit. A variable declared as `45` (int) and one declared as `45.0` (float) will behave differently in some calculations. Catching type mismatches early prevents subtle bugs.

---

### Step 3 — Calculate the Roof Area [Code Cell + Text Cell]

**3a.** Create a **Code Cell** titled: `# Step 3: Roof Area Calculation`

**3b.** Calculate the roof area using the multiplication operator:
```python
roof_area = roof_length * roof_width
```

**3c.** Print the result with a descriptive label and its unit (m²).

**3d.** Use `isinstance()` to check whether `roof_area` is an `int`. Print a statement that reports the result of this check.

> **Defining `isinstance()`:** `isinstance(variable, type)` returns `True` if the variable is of the specified type, and `False` otherwise. Unlike `type()`, it correctly handles type inheritance, making it the preferred method when using types in conditional logic.

**3e.** Below the code cell, add a **Text (Markdown) cell** that explains in 1–2 sentences what the calculated area represents and why it is needed for the next step.

---

### Step 4 — Calculate the Factored Load Per Unit Area [Code Cell + Text Cell]

**4a.** Create a **Code Cell** titled: `# Step 4: Factored Load Calculation (per unit area)`

**4b.** Calculate the factored load using the exact formula given in the scenario. Break the calculation into clearly commented sub-steps:

```python
# Dead load component (factored)
dead_component = 1.2 * D

# Live load component (factored)
live_component = 1.6 * L

# Snow load component (factored)
snow_component = 0.5 * S

# Total factored load per unit area
factored_load = dead_component + live_component + snow_component
```

**4c.** Print each component and the final `factored_load` with descriptive labels and units (kPa).

**4d.** Verify that `factored_load` is a `float` using `isinstance()`. Print the result of this check.

**4e.** Add a **Text (Markdown) cell** below the code that explains what each load factor (1.2, 1.6, 0.5) represents conceptually and what the total factored load value means for the roof design.

---

### Step 5 — Calculate the Total Force on the Roof [Code Cell + Text Cell]

**5a.** Create a **Code Cell** titled: `# Step 5: Total Force on Roof`

**5b.** Calculate the total force:

```python
total_force = factored_load * roof_area
```

**5c.** Print the result with a descriptive label and units (kN, kilonewtons).

> **Unit note:** kPa × m² = kN (kilonewtons). You do not need to convert units; the math handles it automatically.

**5d.** Use an **f-string** to print a formatted summary sentence. The sentence must embed at least three variables. Example format:

```
"The total factored force acting on the 1350 m² roof of the warehouse is 8788.50 kN."
```

> **Defining f-strings:** An f-string is a string prefixed with `f` that allows you to embed Python expressions directly inside curly braces `{}` within the string. Example: `f"Result: {total_force:.2f} kN"`. The `:.2f` format specifier rounds the displayed value to two decimal places.

**5e.** Add a **Text (Markdown) cell** that interprets the total force in plain language — what does this number represent physically, and why does a structural engineer need to know it?

---

### Step 6 — Safety Check Using Comparison and Logical Operators [Code Cell + Text Cell]

**6a.** Create a **Code Cell** titled: `# Step 6: Safety Check`

**6b.** Use a **comparison operator** to determine whether the factored load exceeds the design capacity:

```python
is_over_capacity = factored_load > design_capacity
```

**6c.** Print the result of `is_over_capacity` with a descriptive label. Verify its type using `isinstance()` and confirm it is a `bool`.

**6d.** Use a **logical operator** to create a compound safety check. The roof is considered **safe** only if:
- The factored load does **not** exceed the design capacity, **and**
- The `analysis_complete` variable is `True` (you will update this in Step 7)

Write this check as:

```python
roof_is_safe = (not is_over_capacity) and analysis_complete
```

Print the result with a label. Explain in an inline comment why `roof_is_safe` may show an unexpected value at this point in the notebook.

**6e.** Use an augmented assignment operator to update a `safety_margin` variable. Calculate it as:

```python
safety_margin = design_capacity   # initialize
safety_margin -= factored_load    # augmented subtraction: margin = capacity - factored_load
```

Print `safety_margin` with its unit (kPa) and a label.

> **Defining augmented assignment:** An augmented assignment operator like `-=` updates a variable's value in place. `x -= 5` is exactly equivalent to `x = x - 5`. It makes code more concise, especially in iterative calculations.

**6f.** Add a **Text (Markdown) cell** that explains what the safety margin means physically. A positive margin means the load is within capacity; a negative margin means the design is inadequate. Discuss what the calculated margin value implies for this warehouse project.

---

### Step 7 — Final Summary and Conclusion [Code Cell + Text Cell]

**7a.** Create a **Code Cell** titled: `# Step 7: Final Summary`

**7b.** Update the status variables now that the analysis is complete:

```python
analysis_complete = True
notes = "Your conclusion here — replace this placeholder with your actual conclusion."
```

Replace the placeholder string in `notes` with a real engineering conclusion (written by you) that directly answers the question: *Can this roof safely support the calculated factored load? What should the client be told?*

**7c.** Recalculate `roof_is_safe` now that `analysis_complete` is `True` (copy the line from Step 6 and re-run it here):

```python
roof_is_safe = (not is_over_capacity) and analysis_complete
```

**7d.** Print a complete formatted summary using f-strings. Your summary must include:

- Project name
- Engineer name
- Roof dimensions and area
- Factored load per unit area (kPa)
- Design capacity (kPa)
- Safety margin (kPa)
- Total force on the roof (kN)
- Whether the roof is over capacity (`is_over_capacity`)
- Whether the roof is safe (`roof_is_safe`)
- The `notes` conclusion

**7e.** Verify the final type of `notes` using `type()` and confirm it has changed from `NoneType` to `str`.

**7f.** Add a **Text (Markdown) cell** that serves as the formal engineering conclusion section. It must include:

- A restatement of the problem
- The key numeric results (factored load, safety margin, total force)
- A plain-English recommendation to the client
- A reflection sentence: In 2–3 sentences, explain what Python data types and operators made this calculation possible, and why using Python for this type of analysis is advantageous compared to a basic calculator.

---

### Step 8 — Operator Precedence Verification [Code Cell + Text Cell]

**8a.** Create a **Code Cell** titled: `# Step 8: Operator Precedence Check`

**8b.** Demonstrate that Python's operator precedence affects the result of the factored load formula. Write the formula **without parentheses** first, then **with explicit parentheses**, and compare the results:

```python
# Without grouping parentheses (relies on Python's default precedence)
result_no_parens = 1.2 * D + 1.6 * L + 0.5 * S

# With explicit grouping parentheses (same mathematical intent, made explicit)
result_with_parens = (1.2 * D) + (1.6 * L) + (0.5 * S)

# Are the results equal?
results_match = result_no_parens == result_with_parens
```

Print all three variables with labels.

**8c.** Now write a **deliberately incorrect** version of the formula that would result from misapplying precedence (for example, adding before multiplying by accident). Show what the wrong result would be and how it differs from the correct value.

```python
# Incorrect version (demonstrates what happens without understanding precedence)
result_incorrect = 1.2 * (D + 1.6) * (L + 0.5) * S
difference = factored_load - result_incorrect
```

Print `result_incorrect` and `difference` with labels.

**8d.** Add a **Text (Markdown) cell** that explains:

- What Python's operator precedence rules are (highest to lowest, as covered in the module)
- Why the correct and parenthesized versions produce the same result in 8b
- Why the incorrect version in 8c produces a different result, and what engineering consequence a calculation error like this could have in a real project

---

## Notebook Structure Checklist

Before submitting, confirm your notebook contains the following cells in order:

| # | Cell Type | Content |
|---|---|---|
| 1 | Text | Title, engineer info, problem description, variable dictionary |
| 2 | Code | All variable declarations + `type()` checks |