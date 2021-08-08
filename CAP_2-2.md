<h2><b>MEF 1D</b></h2>

Function: _**MEF1D**_

About: This function performs structural analysis of bars with 2 nodes (1 at each end). 

<h3><b>How to use</b></h3>

<p align="justify">The MEF 1D function has the following input variables. All inputs kwargs python arguments type.</p>

- ```FILENAME```: structural dataset (.txt extension);
- ```DICTIONARY```: Structural dataset (Python dictionary);

<p align="justify">The MEF 1D function has the following output variables.</p>
- ```RESULTS```: Structural analysis results by element (Python dictionary)

<h4><b>Optional setup:</b></h4>

> Dictionary
- ```TYPE_ELEMENT```: 0 = Frame element, 1 = CST
- ```TYPE_SOLUTION```: 0 = Condense procedure, 1 = Zero and One procedure
- ```COORDINATES```: X, Y
- ```ELEMENTS```: Node 1, Node 2, Material id, Section id, Hinge id node 1, Hinge id node 2 (0 = No, 1 = Yes) 
- ```MATERIALS```: Young's Modulus, Poisson, Density, Thermal coefficient
- ```SECTIONS```: Area, Inertia 1, Inertia 2, X cg, Y cg
- ```PRESCRIBED DISPLACEMENTS```: Node id, Direction (u = 0, v = 1, θ = 2), Displacement value
- ```ELEMENT LOADS```: Under construction (Fill only ```"None"```)
- ```NODAL LOADS```: Node id, Direction (u = 0, v = 1, θ = 2), Displacement value
- ```SPRINGS```: Node id, Direction (u = 0, v = 1, θ = 2), Stiffness value

Obs.: If you do not want to fill in a value for ```SPRINGS``` or ```NODAL LOADS```, use the ```"None"``` tag. In .txt extension to use ```NULL``` tag.

Truss Example in dictionary:

```python
import numpy as np                  # It's necessary to put an internal array in dictionary
from FINITO_TOOLBOX import MEF1D    # Import MEF1D algorithm (See section 2-1)

# Structure data
# Truss structure
STRUCTURE = {
              "TYPE_ELEMENT": 0,        
              "TYPE_SOLUTION": 0,       
              "N_NODES": 3,
              "N_MATERIALS": 3,
              "N_SECTIONS": 3,
              "N_ELEMENTS": 3,
              "N_DISPLACEMENTS": 3,
              "N_ELEMENTSLOADED": 0,
              "N_NODESLOADED": 1,
              "N_SPRINGS": 0,
              "COORDINATES":            
              np.array([[0.0, 0.0],      
                [2.0, 0.0],
                [0.0, 2.0]]),
              "ELEMENTS": 
              np.array([[0, 1, 0, 0, 1, 1],
                [1, 2, 1, 1, 1, 1],
                [0, 2, 2, 2, 1, 1]]),
              "MATERIALS": 
              np.array([[2.050E8, 0.3, 78600, 0.000012],
                [2.050E8, 0.3, 78600, 0.000012],
                [2.050E8, 0.3, 78600, 0.000012]]),
              "SECTIONS": 
              np.array([[0.0079, 0.000005, 0.000005, 0.05, 0.05],
                [0.0079, 0.000005, 0.000005, 0.05, 0.05],
                [0.0079, 0.000005, 0.000005, 0.05, 0.05]]),
              "PRESCRIBED DISPLACEMENTS": 
              np.array([[0, 0, 0],
                [0, 1, 0],
                [2, 0, 0]]),
              "ELEMENT LOADS": None,
              "NODAL LOADS": 
              np.array([[1, 1, -100]]),
              "SPRINGS": None}

# Call MEF1D Algorithm
TRUSS_01_RESULTS = MEF1D(DICTIONARY = STRUCTURE)
```

Truss Example in external file:

```python
import numpy as np                  # It's necessary to put an internal array in dictionary
from FINITO_TOOLBOX import MEF1D    # Import MEF1D algorithm (See section 2-1)

# Structure data
# Truss structure (See file: https://github.com/wmpjrufg/FINITO_TOOLBOX/blob/gh-pages/truss_01.txt)
TRUSS_01_RESULTS = MEF1D(FILENAME = truss_01)
```

<h4><b>View results:</b></h4>

i Element results  
i = 0  

> Dictionary tags  
ID_ELEMENT  - Input element id    
M           - Bending moment    
N           - Axial force  
V           - Shear force   
UX          - u displacement  
UY          - v displacement  
UZ          - θ rotation  
X           - Lenght  
  
Obs.: The algorithm divides the element into 11 pieces.  

```python
...
...
TRUSS_01_RESULTS_0 = TRUSS_01_RESULTS[0]                    # 0 Element results
```
  
Using Pandas library  
```python
...
...
import pandas as pd
TRUSS_01_RESULTS_0 = pd.DataFrame(data = RESULTS[0])        # 0 Element results
RESULTS_BAR_0.head(50)
```
  
Obs.: Always use the value 50 in the ```.head()``` method.  
