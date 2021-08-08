<h1>How to use MEF1D framewrok</h1>

<p align="justify">This function performs structural analysis of frame elements with 2 nodes (1 at each end). After installation you can use framework. To use the library function it is necessary to import it.</p>


<h3>Call framework</h3>

Example:
```python
# Install process
!pip install -i https://test.pypi.org/simple/ FINITO-FEM-TOOLBOX

# Import MEF 1D Algorithm
from FINITO_FEM_TOOLBOX import MEF1D
```

<h3>Input data</h3>

<p align="justify">Data entry can be done by a text file (.txt extension) or a Python dictionary. 
The entry must contain the following information:</p>

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-mim8{border-color:#000000;font-size:12px;text-align:left;vertical-align:top}
.tg .tg-0f7m{background-color:#efefef;border-color:#000000;font-size:12px;text-align:left;vertical-align:top}
.tg .tg-j50o{background-color:#c0c0c0;border-color:#000000;font-size:12px;text-align:center;vertical-align:top}
</style>
<table class="tg" style="undefined;table-layout: fixed; width: 816px">
<colgroup>
<col style="width: 234px">
<col style="width: 330px">
<col style="width: 252px">
</colgroup>
<thead>
  <tr>
    <th class="tg-j50o"><span style="font-weight:bold">Variable</span></th>
    <th class="tg-j50o"><span style="font-weight:bold">Description</span></th>
    <th class="tg-j50o"><span style="font-weight:bold">Observation</span></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-mim8">TYPE_ELEMENT</td>
    <td class="tg-mim8">Type element in Finito algorithm</td>
    <td class="tg-mim8"><span style="font-style:italic">0 = Frame bar element</span></td>
  </tr>
  <tr>
    <td class="tg-0f7m">TYPE_SOLUTION</td>
    <td class="tg-0f7m">Solution of the system of equations</td>
    <td class="tg-0f7m"><span style="font-style:italic">0 = Condense procedure</span><br><span style="font-style:italic">1 = Zero and One algorithm</span></td>
  </tr>
  <tr>
    <td class="tg-mim8">N_NODES</td>
    <td class="tg-mim8">Number of nodes</td>
    <td class="tg-mim8"></td>
  </tr>
  <tr>
    <td class="tg-0f7m">N_MATERIALS</td>
    <td class="tg-0f7m">Number of materials</td>
    <td class="tg-0f7m"></td>
  </tr>
  <tr>
    <td class="tg-mim8">N_SECTIONS</td>
    <td class="tg-mim8">Number of sections</td>
    <td class="tg-mim8"></td>
  </tr>
  <tr>
    <td class="tg-0f7m">N_ELEMENTS</td>
    <td class="tg-0f7m">Number of frame elements</td>
    <td class="tg-0f7m"></td>
  </tr>
  <tr>
    <td class="tg-mim8">N_DOFPRESCRIPTIONS</td>
    <td class="tg-mim8">Number of DOF displacement control</td>
    <td class="tg-mim8"></td>
  </tr>
  <tr>
    <td class="tg-0f7m">N_DOFLOADED</td>
    <td class="tg-0f7m">Number of DOF forces</td>
    <td class="tg-0f7m"></td>
  </tr>
  <tr>
    <td class="tg-mim8">N_DOFSPRINGS</td>
    <td class="tg-mim8">Number of DOF spring elements</td>
    <td class="tg-mim8"></td>
  </tr>
  <tr>
    <td class="tg-0f7m">COORDINATES</td>
    <td class="tg-0f7m">Coordinates properties</td>
    <td class="tg-0f7m"><span style="font-style:italic">Node, x, y</span></td>
  </tr>
  <tr>
    <td class="tg-mim8">ELEMENTS</td>
    <td class="tg-mim8">Elements properties</td>
    <td class="tg-mim8"><span style="font-style:italic">Node 0 ... Node (</span><span style="font-weight:bold;font-style:italic">N_NODES</span><span style="font-style:italic"> - 1), Material ID, Geometry ID, Hinge ID node 0, Hinge ID node 1</span></td>
  </tr>
  <tr>
    <td class="tg-0f7m">MATERIALS</td>
    <td class="tg-0f7m">Materials properties</td>
    <td class="tg-0f7m"><span style="font-style:italic">Young, Poisson, Density, Thermal coefficient</span></td>
  </tr>
  <tr>
    <td class="tg-mim8">SECTIONS</td>
    <td class="tg-mim8">Sections properties</td>
    <td class="tg-mim8"><span style="font-style:italic">Area, Inertia 1, Inertia Frame bar, X GC, Y GC</span></td>
  </tr>
  <tr>
    <td class="tg-0f7m">PRESCRIBED DISPLACEMENTS</td>
    <td class="tg-0f7m">Prescribed DOF displacement properties</td>
    <td class="tg-0f7m"><span style="font-style:italic">Node, Direction (X = 0, Y = 1, Z = 2), Value</span></td>
  </tr>
  <tr>
    <td class="tg-mim8">NODAL LOADS</td>
    <td class="tg-mim8">Nodal DOF force properties</td>
    <td class="tg-mim8"><span style="font-style:italic">Node, Direction (X = 0, Y = 1, Z = 2), Value</span></td>
  </tr>
  <tr>
    <td class="tg-0f7m">SPRINGS</td>
    <td class="tg-0f7m">Nodal DOF spring properties</td>
    <td class="tg-0f7m"><span style="font-style:italic">Node, Direction (X = 0, Y = 1, Z = 2), Value</span><br><span style="font-weight:bold;font-style:italic">N_DOFSPRINGS</span><span style="font-style:italic"> = 0</span><br><span style="font-style:italic">a) </span><span style="font-weight:bold;font-style:italic">NULL</span><span style="font-style:italic"> .txt extension</span><br><span style="font-style:italic">b) </span><span style="font-weight:bold;font-style:italic">None</span><span style="font-style:italic"> Py dictionary</span></td>
  </tr>
</tbody>
</table>

<h3>Input Examples</h3>

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-m5y2{background-color:#c0c0c0;border-color:#000000;font-size:13px;font-weight:bold;text-align:center;vertical-align:top}
.tg .tg-ml71{border-color:#000000;font-size:13px;text-align:center;vertical-align:top}
.tg .tg-317x{background-color:#efefef;border-color:#000000;font-size:13px;text-align:center;vertical-align:top}
</style>
<table class="tg" style="undefined;table-layout: fixed; width: 431px">
<colgroup>
<col style="width: 95px">
<col style="width: 82px">
<col style="width: 120px">
<col style="width: 134px">
</colgroup>
<thead>
  <tr>
    <th class="tg-m5y2">Name</th>
    <th class="tg-m5y2">Structure</th>
    <th class="tg-m5y2">Input File</th>
    <th class="tg-m5y2">Notebook Jupyter</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-ml71">TRUSS_00</td>
    <td class="tg-ml71">Figure</td>
    <td class="tg-ml71"><a href="https://github.com/wmpjrufg/FINITO_TOOLBOX/blob/gh-pages/MEF1D/TRUSS_00/TRUSS_00.txt" target="_blank" rel="noopener noreferrer">.txt</a>, <a href="https://github.com/wmpjrufg/FINITO_TOOLBOX/blob/gh-pages/MEF1D/TRUSS_00/TRUSS_00.py" target="_blank" rel="noopener noreferrer">dictionary</a></td>
    <td class="tg-ml71"><a href="https://github.com/wmpjrufg/FINITO_TOOLBOX/blob/gh-pages/MEF1D/TRUSS_00/TRUSS_00_EXAMPLE_TXT.ipynb" target="_blank" rel="noopener noreferrer">.txt</a>, <a href="https://github.com/wmpjrufg/FINITO_TOOLBOX/blob/gh-pages/MEF1D/TRUSS_00/TRUSS_00_EXAMPLE_DICTIONARY.ipynb" target="_blank" rel="noopener noreferrer">dictionary</a></td>
  </tr>
  <tr>
    <td class="tg-317x">TRUSS_01</td>
    <td class="tg-317x">Figure</td>
    <td class="tg-317x"><a href="https://github.com/wmpjrufg/FINITO_TOOLBOX/blob/gh-pages/MEF1D/TRUSS_01/TRUSS_01.txt" target="_blank" rel="noopener noreferrer">.txt</a>, <a href="https://github.com/wmpjrufg/FINITO_TOOLBOX/blob/gh-pages/MEF1D/TRUSS_01/TRUSS_01.py" target="_blank" rel="noopener noreferrer">dictionary</a></td>
    <td class="tg-317x"><a href="https://github.com/wmpjrufg/FINITO_TOOLBOX/blob/gh-pages/MEF1D/TRUSS_01/TRUSS_01_EXAMPLE_TXT.ipynb" target="_blank" rel="noopener noreferrer">.txt</a>, <a href="https://github.com/wmpjrufg/FINITO_TOOLBOX/blob/gh-pages/MEF1D/TRUSS_01/TRUSS_01_EXAMPLE_DICTIONARY.ipynb" target="_blank" rel="noopener noreferrer">dictionary</a></td>
  </tr>
  <tr>
    <td class="tg-ml71">FRAME_00</td>
    <td class="tg-ml71">Figure</td>
    <td class="tg-ml71"><a href="https://github.com/wmpjrufg/FINITO_TOOLBOX/blob/gh-pages/MEF1D/FRAME_00/FRAME_00.txt" target="_blank" rel="noopener noreferrer">.txt</a>, <a href="https://github.com/wmpjrufg/FINITO_TOOLBOX/blob/gh-pages/MEF1D/FRAME_00/FRAME_00.py" target="_blank" rel="noopener noreferrer">dictionary</a></td>
    <td class="tg-ml71"><a href="https://github.com/wmpjrufg/FINITO_TOOLBOX/blob/gh-pages/MEF1D/FRAME_00/FRAME_00_EXAMPLE_TXT.ipynb" target="_blank" rel="noopener noreferrer">.txt</a>, <a href="https://github.com/wmpjrufg/FINITO_TOOLBOX/blob/gh-pages/MEF1D/FRAME_00/FRAME_00_EXAMPLE_DICTIONARY.ipynb" target="_blank" rel="noopener noreferrer">dictionary</a></td>
  </tr>
  <tr>
    <td class="tg-317x">FRAME_01</td>
    <td class="tg-317x">Figure</td>
    <td class="tg-317x"><a href="https://github.com/wmpjrufg/FINITO_TOOLBOX/blob/gh-pages/MEF1D/FRAME_01/FRAME_01.txt" target="_blank" rel="noopener noreferrer">.txt</a>, <a href="https://github.com/wmpjrufg/FINITO_TOOLBOX/blob/gh-pages/MEF1D/FRAME_01/FRAME_01.py" target="_blank" rel="noopener noreferrer">dictionary</a></td>
    <td class="tg-317x"><a href="https://github.com/wmpjrufg/FINITO_TOOLBOX/blob/gh-pages/MEF1D/FRAME_01/FRAME_01_EXAMPLE_TXT.ipynb" target="_blank" rel="noopener noreferrer">.txt</a>, <a href="https://github.com/wmpjrufg/FINITO_TOOLBOX/blob/gh-pages/MEF1D/FRAME_01/FRAME_01_EXAMPLE_DICTIONARY.ipynb" target="_blank" rel="noopener noreferrer">dictionary</a></td>
  </tr>
</tbody>
</table>


<h3>View results</h3>

<p align="justify">The results are divided by elements in a Python dictionary. The algorithm divides each element into 10 parts, that is, 11 internal nodes. Therefore the results are presented in 11 nodes, including the beginning and end nodes of the element.<br>
<br>
We note here that the values of the element's internal nodes have not yet been implemented. So to identify this pattern we leave the value **-1989** which has no physical meaning.
</p>

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-mim8{border-color:#000000;font-size:12px;text-align:left;vertical-align:top}
.tg .tg-0f7m{background-color:#efefef;border-color:#000000;font-size:12px;text-align:left;vertical-align:top}
.tg .tg-6v09{background-color:#c0c0c0;border-color:#000000;font-size:12px;font-weight:bold;text-align:center;vertical-align:top}
.tg .tg-uiz2{border-color:#000000;font-size:12px;text-align:center;vertical-align:top}
.tg .tg-nqa4{background-color:#efefef;border-color:#000000;font-size:12px;text-align:center;vertical-align:top}
</style>
<table class="tg" style="undefined;table-layout: fixed; width: 341px">
<colgroup>
<col style="width: 148px">
<col style="width: 193px">
</colgroup>
<thead>
  <tr>
    <th class="tg-6v09">Result dictionary</th>
    <th class="tg-6v09">Description</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-uiz2">'X'</td>
    <td class="tg-mim8"><span style="font-style:italic">x</span> coordinate in local axis</td>
  </tr>
  <tr>
    <td class="tg-nqa4">'UX'</td>
    <td class="tg-0f7m"><span style="font-style:italic">u </span>displacement in <span style="font-style:italic">x</span> coordinate</td>
  </tr>
  <tr>
    <td class="tg-uiz2">'UY'</td>
    <td class="tg-mim8"><span style="font-style:italic">v</span> displacement in <span style="font-style:italic">x</span> coordinate</td>
  </tr>
  <tr>
    <td class="tg-nqa4">'UZ'</td>
    <td class="tg-0f7m"><span style="font-style:italic">θ</span> displacement in <span style="font-style:italic">x</span> coordinate</td>
  </tr>
  <tr>
    <td class="tg-uiz2">'N'</td>
    <td class="tg-mim8">Internal load - Axial force</td>
  </tr>
  <tr>
    <td class="tg-nqa4">'V'</td>
    <td class="tg-0f7m">Internal Load - Shear force</td>
  </tr>
  <tr>
    <td class="tg-uiz2">'M'</td>
    <td class="tg-mim8">Internal load - Bending Moment</td>
  </tr>
  <tr>
    <td class="tg-nqa4">'ID_ELEMENT'</td>
    <td class="tg-0f7m">ID element</td>
  </tr>
</tbody>
</table>

<p align="justify">To view the results there are two possibilities:</p>

a) ```print()``` in command line:

View results about **0** element.

```python
# Output print
TRUSS_00_BAR_0 = TRUSS_00_RESULTS[0] 
print(TRUSS_00_BAR_0)
```

View just **axial force**
```python
print(TRUSS_00_BAR_0['N'])
```

- ```TRUSS_00_BAR_0['N'][0]```  - First DIV or 0 internal node in **0** Element;
- ```TRUSS_00_BAR_0['N'][10]``` - Last DIV or 1 internal node in **0** Element.

b) Interesting view using ```pandas``` framework:

View results about **0** element using notebook Jupyter.

```python
# Output print
import pandas as pd
TRUSS_00_BAR_0 = pd.DataFrame(data = TRUSS_00_BAR_0)
TRUSS_00_BAR_0.head(50)
```

Observation: Always use the value 50 in the ```.head()``` method.