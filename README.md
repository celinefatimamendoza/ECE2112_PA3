<kbd>ECE2112<kbd>
# ECE 2112 - Programming Assignment #03  

**Celine Fatima C. Mendoza | 2ECE-C**  
# EXPERIMENT 3:  PYTHON DATA ANALYSIS (PANDAS)  

This repository contains programming assignment 2 for the **ADVANCED COMPUTER PROGRAMMING AND ALGORITHMS** ```[ECE2112]``` course. It consists of three programming problems covering **Module 3 - Pandas**.  


  ## I. Intended Learning Outcomes  
  At the end of this laboratory activity, the student should be able to:  

  1. load a CSV dataset into a Pandas DataFrame;  
  2. select rows and columns using positional and label-based indexing;  
  3. filter records using conditions on a DataFrame column; and  
  4. extract a well-defined subset of data without changing the source data.  

   ## II. Programming Problems  

### A.  POSITIONAL AND LABEL-BASED SLICING  
After loading `cars`, complete the following operations.  
a. Display the shape and complete list of column names of `cars`.  
b. Using positional slicing, create `cars_6_to_10` containing rows **6** through **10** of the dataset, where the first data row is row 1.  
c. From `cars_6_to_10`, display only the columns `Model`, `mpg`, `cyl`, `hp`, and `gear`, in that order.  

### Function:  
  ~ **.read_csv()** -  

  *Example:*  
  ```pd.read_csv('cars.csv')``` -  

  ~ **.columns.tolist()** -  

  *Example:*
    ```cars.columns.tolist()``` -  

  ~ **.iloc[]** -  

  *Example:*  
  ```cars.iloc[5:10]``` -  

  ~ **.loc[]** -  

  *Example:*  
  ```cars_6_to_10.loc[:, ['Model', 'mpg', 'cyl', 'hp', 'gear']]``` -  

```python
import pandas as pd

cars = pd.read_csv('cars.csv')

columnname_list = cars.columns.tolist()

cars_6_to_10 = cars.iloc[5:10]

selected_columns = cars_6_to_10.loc[:, ['Model', 'mpg', 'cyl', 'hp', 'gear']]

print ("Shape of cars =", cars.shape)
print("List of column names: ", columnname_list)
print("\ncars 6 to 10: ")
display(cars_6_to_10)
print("Selected columns for cars 6 to 10: ")
display(selected_columns)
```


### B. MODEL LOOKUP  
Use Boolean indexing on the `Model` column to answer both requests.  
a. Display the complete row for `Toyota Corolla`.  
b. For `Pontiac Firebird`, display only `Model`, `mpg`, `hp`, and `wt`.  
Store the two results in `toyota` and `pontiac`, respectively. Do not use a hard-coded row number to locate either model.  

  ### Function:  

```python
toyota = cars.loc[(cars['Model'] == 'Toyota Corolla')]
pontiac = cars.loc[(cars['Model'] == 'Pontiac Firebird'), ['Model', 'mpg', 'hp', 'wt']]

print("Toyota Corolla")
display(toyota)
print("Pontiac Firebird")
display(pontiac)
```


### C. MULTI-MODEL SUBSETTING  
Create a DataFrame named `selected_cars` containing only the records for three models: `Datsun 710`, `Lotus Europa`, and `Ferrari Dino`.  
For these records, retain only `Model`, `mpg`, `cyl`, `hp`, and `gear`. Select the rows by their model values rather than by row numbers. Display `selected_cars` and its shape.  

  ### Function:  

```python
selected_cars = cars.loc[(cars['Model'] == 'Datsun 710') | (cars['Model'] == 'Lotus Europa') | (cars['Model'] == 'Ferrari Dino'), ['Model', 'mpg', 'cyl', 'hp', 'gear']]

display(selected_cars)
print("Selected cars shape = ", selected_cars.shape)
```


  

