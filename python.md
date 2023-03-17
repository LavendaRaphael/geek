# python

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [python](#python)
  - [Loop](#loop)
  - [Tar](#tar)
  - [Path](#path)
  - [Format](#format)
  - [Numpy](#numpy)
    - [readtxt](#readtxt)
    - [array](#array)
    - [mask](#mask)
  - [Matplotlib](#matplotlib)
    - [colorbar](#colorbar)
    - [font](#font)
    - [Constrained layout](#constrained-layout)
    - [Tight layout](#tight-layout)
    - [dpi](#dpi)
    - [figsize](#figsize)
      - [legend](#legend)
    - [unicode](#unicode)
    - [mathtex](#mathtex)
  - [Class](#class)
  - [Def](#def)
  - [json](#json)
  - [Subprocess](#subprocess)
  - [copy](#copy)
  - [File](#file)
  - [Font](#font-1)
  - [Raise](#raise)
    - [Delete file](#delete-file)
  - [Import](#import)
  - [Pip](#pip)
    - [换源](#换源)
    - [config](#config)
    - [install](#install)
    - [update](#update)
    - [offline](#offline)
  - [ase](#ase)
    - [gif](#gif)
    - [render](#render)

<!-- /code_chunk_output -->

## Loop

```py
for id, element in enumerate([1,2,3]):
for i1, i2 in zip([1,2,3],[4,5,6]):
```

## Tar

```py
import tarfile
with tarfile.open('file.tar','w') as tar:
    tar.add('file')

tarfile.open('file.tar').extractall(path='./')
```

## Path

exist

```py
import os.path
os.path.exists(file_path/dir_path)
os.path.isfile(file_path)
```

## Format

<https://www.runoob.com/python/att-string-format.html>

```py
print(f'{math.pi:.3f}')
```

## Numpy

### readtxt

```py
numpy.loadtxt('file')
numpy.genfromtxt('file', names=True, usecols=(1,2))
```

### array

```py
numpy.arange()
```

### mask

```py
np_array = np.array([
    [1, 1, 1],
    [0, 1, 2],
    [1, 0, 3],
])
list_tof = (np_array[:,0]== 1) & (np_array[:,1]== 1)
np_array[ list_tof ]
```

## Matplotlib

```py
import matplotlib.pyplot as plt
import matplotlib as mpl

mpl.rcParams['font.size']=12
mpl.rcParams['pdf.fonttype'] = 42
mpl.rcParams['ps.fonttype'] = 42
mpl.rcParams['font.family'] = 'Arial'

fig, ax = plt.subplots()

ax.plot( array_data[0], array_data[1], label = '', linewidth=2)

ax.set_xlabel('')
ax.set_ylabel('')
ax.set_xlim((None,None))
ax.set_ylim((None,None))
ax.legend(
    loc = 'upper center',
    frameon = False,
    title = 'title',
    handlelength = 1.0,
    labelspacing = 0.1,
)

fig.set_tight_layout(True)
cm = 1/2.54
fig.set_size_inches(8.9*cm,7.5*cm)
fig.savefig('', dpi=450)

plt.show()
```

### colorbar

```py
norm = plt.Normalize(0, 1)
cmap = 'coolwarm'
ax.scatter( , c=0.5, cmap=cmap, norm=norm, alpha=0.5)
smap = plt.cm.ScalarMappable(cmap=cmap, norm=norm)
fig.colorbar(smap)
```

### font

必须放在 fig 实例化之前

```py
from matplotlib import rc
rc('font',**{'size':12, 'family':'sans-serif','sans-serif':['Arial']})
```

```py
import matplotlib as mpl
mpl.rcParams['font.size']=12

mpl.rcParams['pdf.fonttype'] = 42
mpl.rcParams['ps.fonttype'] = 42

mpl.rcParams['font.family'] = 'Arial'

mpl.rcParams['font.family']='sans-serif'
mpl.rcParams['font.sans-serif']=["Arial"]
```

### Constrained layout

```py
mpl.rcParams['figure.constrained_layout.use'] = True
```

### Tight layout

```py
fig.set_tight_layout(True)
plt.tight_layout()
mpl.rcParams["figure.autolayout"] = True

fig.set_tight_layout(False)
fig.subplots_adjust(
    left = ,
    right = ,
    bottom = ,
    top = ,
    wspace = ,
    hspace = ,
)
```

### dpi

```py
mpl.rcParams['figure.dpi'] = 450
fig.savefig(str_save, dpi=450)
```

### figsize

```py
cm = 1/2.54
fig.set_size_inches(8.9*cm,7.5*cm)
fig, ax = plt.subplots(figsize=(8.9*cm,7.5*cm))
```

#### legend

```py
ax.legend(
    loc = 'upper center',
    frameon = False,
    title = 'title',
    handlelength = 1.0
)
```

### unicode

```py
'\N{Asterisk}'
```

### mathtex

```py
r'$a_1$'
```

## Class

```py
class class_test():
    class_viariable = 1
    def __init__(self):
        self.instance_viaralbe = 2
```

```py
class class_():
    @property
    def (self):
        return self._
    @.setter
    def (self, value):
        self._ = value
```

colormaps

<https://towardsdatascience.com/creating-colormaps-in-matplotlib-4d4de78a04b8>

Colors

```py
import matplotlib.colors as mcolors
print(mcolors.TABLEAU_COLORS)
```

```py
{
    'tab:blue': '#1f77b4', 
    'tab:orange': '#ff7f0e', 
    'tab:green': '#2ca02c', 
    'tab:red': '#d62728', 
    'tab:purple': '#9467bd', 
    'tab:brown': '#8c564b', 
    'tab:pink': '#e377c2', 
    'tab:gray': '#7f7f7f', 
    'tab:olive': '#bcbd22', 
    'tab:cyan': '#17becf'
}
```

## Def

<https://www.liaoxuefeng.com/wiki/1016959663602400/1017261630425888>

默认参数必须指向不变对象！

```py
def def_x(a=None):
    if a is None:
        a = []
```

## json

```py
import json
json.load( fp )
json.dump( obj, fp, indent=None )
```

## Subprocess

<https://stackoverflow.com/questions/4256107/running-bash-commands-in-python>

```python
import subprocess
subprocess_results = subprocess.run( 'echo hello', shell=True, check=True, text=True, executable='/bin/bash')
print(subprocess_results.stdout)
```

## copy

```python
import copy
a=[]
b=list(a)
c=copy.copy(a)
print( id(a), id(b), id(c) )
```

## File

<https://docs.python.org/3/library/functions.html#open>

```py
with open('file', 'r') as file_open:
```

|mode   |file exist |No file|r or w 
|:---:  |:-:        |:-:    |:---:  
|`'r'`  |open       |error  |r
|`'w'`  |clear      |create |w
|`'a'`  |open       |create |w
|`'r+'` |open       |error  |rw
|`'w+'` |clear      |create |rw
|`'a+'` |open       |create |rw

```py
file_open.readline()
```

Note: `.readline()` can't used with `.next()`.

## Font

```bash
rm -r ~/.cache/matplotlib/
```

## Raise

```python
raise [exceptionName [(reason)]]
```

### Delete file

```py
import os
import shutil

os.remove('test.x')   ## file
shutil.rmtree('temp') ## folder
```

## Import

a.py

```py
class A:
 aaa=10
```

b.py

```py
import sys
sys.path.append(r'./')
from a import A

b=A.aaa
```

## Pip

<https://pip.pypa.io/en/stable/user_guide/>

### 换源

```bash
python -m pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```

### config

<https://pip.pypa.io/en/stable/topics/configuration/>

```bash
python -m pip config edit
```

pip.conf

```conf
[global]
index-url = 'https://pypi.tuna.tsinghua.edu.cn/simple'
```

### install

```sh
python -m pip install --user ase
```

### update

```sh
python -m pip list --outdated
python -m pip install --user --upgrade pip
python -m pip install --user robotframework==2.8.7
python -m pip uninstall [options] <package>
```

### offline

<https://imshuai.com/python-pip-install-package-offline-tensorflow>

## ase

### gif

```python
from ase.io import read, write
a=read('POSCAR')
b=read('CONTCAR')
write('movie.gif', [a,b], interval=500)
```

### render

```py
from ase.io import read,write
import sys
import os

filename='render'

cont=read(str(sys.argv[1]))
cell=cont.cell
cont=cont*(1,1,1)
cont.cell=cell

r = [{'O': 0.74, 'Pt': 1.39}[at.symbol] for at in cont]

generic_projection_settings = {
    'bbox':(render_in.x1, render_in.y1, render_in.x2, render_in.y2),
##   'rotation': rot,  ## text string with rotation (default='' )
##   'rotation': '90y',
    'rotation': '90x,90z',
##   'rotation': '10x,-10y',
##   'rotation': '-72x',
    'radii': .85,  ## float, or a list with one float per atom
    'radii': r,
    'colors': None,  ## List: one (r, g, b) tuple per atom
    'show_unit_cell': 0,   ## 0, 1, or 2 to not show, show, and show all of cell
}

## ase2, ase3, glass, simple, pale, intermediate, vmd, jmol
tex = ['jmol', ] * 288 + ['glass', ] * 288 + ['ase3', ] * 288 + ['vmd', ] * 288
povray_settings={
##   'display': False,  ## Display while rendering
##   'pause': True,  ## Pause when done rendering (only if display)
##   'transparent': False,  ## Transparent background
##   'canvas_width': None,  ## Width of canvas in pixels
    'canvas_height': 500,  ## Height of canvas in pixels
##   'camera_dist': 50.,  ## Distance from camera to front atom
##   'image_plane': None,  ## Distance from front atom to image plane
    'camera_type': 'perspective',  ## orthographic, perspective, ultra_wide_angle
    'point_lights': [],             ## [[loc1, color1], [loc2, color2],...]
    'area_light': [(2., 3., 40.),  ## location
                   'White',       ## color
                   .7, .7, 3, 3],  ## width, height, Nlamps_x, Nlamps_y
##   'background': 'White',        ## color
    'textures': ['jmol',]*1000,  ## ase2, ase3, glass, simple, pale, intermediate, vmd, jmol
    'textures': tex,
##   'celllinewidth': 0.1,  ## Radius of the cylinders representing the cell
}

renderer=write(filename+'.pov',cont,
    **generic_projection_settings,
    povray_settings=povray_settings)
renderer.render()

os.remove(filename+'.ini')
os.remove(filename+'.pov')
```
