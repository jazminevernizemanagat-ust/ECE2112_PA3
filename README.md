# ECE2112_PA3
# Experiment 3: Python Data Analysis (Pandas)

**Name:** MANAGAT, JAZMINE VERNIZE S.  
**Section:** 2ECE-A  

---

## Intended Learning Outcomes

* Load a CSV dataset into a Pandas DataFrame.
* Select rows and columns using positional and label-based indexing.
* Filter records using conditions on a DataFrame column.
* Extract a well-defined subset of data without changing the source data.

```python 
cars = pd.read_csv(r"C:\Users\Jaz\Downloads\cars.csv") 
```

---

## Detailed Discussion of Problems and Solutions

### A. Positional and Label-Based Slicing

* **Problem Statement:** Display the shape and complete list of column names of `cars`. Create `cars_6_to_10` containing rows 6 through 10 of the dataset using positional slicing (`iloc`), where the first data row is row 1. Display only the columns `Model`, `mpg`, `cyl`, `hp`, and `gear` in that order using column labels.
* **Implementation:**

```python
import pandas as pd

print("Shape of cars: ", cars.shape)
print("Column names: ", cars.columns.tolist())

cars_6_to_10 = cars.iloc[5:10]

selected_columns = cars_6_to_10[['Model', 'mpg', 'cyl', 'hp', 'gear']]
print(selected_columns)
```

### B. Model Lookup

* **Problem Statement:** Use Boolean indexing on the Model column to display the complete row for Toyota Corolla (stored in toyota) and display only `Model`, `mpg`, `hp`, and `wt` for `Pontiac Firebird` (stored in pontiac). Do not use hard-coded row numbers.
* **Implementation:**

```python
toyota = cars[cars['Model'] == 'Toyota Corolla']
print("Toyota Corolla: ")
print(toyota)

pontiac = cars[cars['Model'] == 'Pontiac Firebird'][['Model', 'mpg', 'hp', 'wt']]
print("\n", "Pontiac Firebird: ")
print(pontiac)
```

### C. Multi-Model Subsetting

* **Problem Statement:** Create a DataFrame named selected_cars containing only the records for `Datsun 710`, `Lotus Europa`, and `Ferrari Dino`. Retain only the columns `Model`, `mpg`, `cyl`, `hp`, and `gear` using model values rather than row numbers. Display `selected_cars` and its shape.
* **Implementation:**

```python
target_models = ["Datsun 710", "Lotus Europa", "Ferrari Dino"]
target_columns = ["Model", "mpg", "cyl", "hp", "gear"]

selected_cars = cars[cars["Model"].isin(target_models)][target_columns]

print("Selected Cars: ")
print(selected_cars)
print("\n", "Shape of Selected_cars: ", selected_cars.shape)
```


