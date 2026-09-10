# PA3_2ECEC_TIU

#### 1) **POSITIONAL AND LABEL-BASED SLICING** - 

```python
import pandas as pd
cars = pd.read_csv('cars.csv') # Load CSV data into a DataFrame
cars # Display full table

# Return shape
cars.shape

# inspect column names
cars.columns

cars_6_to_10 = cars.iloc[5:10] # Slice rows 5 to 9 by integer position
cars_6_to_10

cars_6_to_10.loc[5:9, ['Model', 'mpg', 'cyl', 'hp', 'gear']] # Select specific features by label
```

##### Step-by-step procedure
- `cars = pd.read_csv('cars.csv')` → Reads the CSV file and names it cars
- `cars.shape` → Returns a tuple showing the total number of rows and columns
- `cars.columns` → Lists all column header names present in the dataset
- `cars_6_to_10 = cars.iloc[5:10]` → Extracts rows 5 to 9 using integer-position slicing and assigns them to a new DataFrame
- `cars_6_to_10.loc[5:9, ['Model', 'mpg', 'cyl', 'hp', 'gear']]` → Filters rows with index labels 5 through 9 and retrieves only the specified list of columns

#### 2) **MODEL LOOKUP**

```python
toyota = cars.loc[cars['Model']=='Toyota Corolla', :] # Get full row for Toyota Corolla
Toyota

pontiac = cars.loc[(cars['Model']=='Pontiac Firebird'), ['Model', 'mpg', 'hp', 'wt']] # Get Pontiac Firebird with subset of specs
Pontiac
```

##### Step-by-step procedure
- `toyota = cars.loc[cars['Model']=='Toyota Corolla', :]` → Filters the row where Model matches 'Toyota Corolla' and selects all columns
- `pontiac = cars.loc[(cars['Model']=='Pontiac Firebird'), ['Model', 'mpg', 'hp', 'wt']]` → Filters the row where Model matches 'Pontiac Firebird' and retrieves only the specified columns

#### 3) **MULTI-MODEL SUBSETTING**

```python
# Filter rows matching any of the 3 models and restrict to target columns
selected_cars = pd.DataFrame(cars[
                             (cars['Model'] == 'Datsun 710') |
                             (cars['Model'] == 'Lotus Europa') |
                             (cars['Model'] == 'Ferrari Dino')],
                             columns=['Model', 'mpg', 'cyl', 'hp', 'gear'])

# Return shape
selected_cars.shape
```

##### Step-by-step procedure
- `selected_cars = pd.DataFrame(...)` → Filters rows matching any of the three models ('Datsun 710', 'Lotus Europa', or 'Ferrari Dino') using bitwise OR (|) and constructs a new DataFrame containing only the columns 'Model', 'mpg', 'cyl', 'hp', and 'gear'
- `selected_cars.shape` → Returns the dimensions (rows, columns) of the newly created DataFrame selected_cars
