# python

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [python](#python)
  - [Path](#path)
    - [exist](#exist)
  - [Format](#format)
  - [Numpy](#numpy)
    - [readtxt](#readtxt)
    - [array](#array)
    - [mask](#mask)
  - [Matplotlib](#matplotlib)
  - [string](#string)
    - [leading zeros](#leading-zeros)
  - [class](#class)
  - [def](#def)
    - [Mutable default parameter](#mutable-default-parameter)
  - [json](#json)
  - [subprocess](#subprocess)
  - [copy](#copy)
  - [File](#file)
    - [open](#open)
    - [read](#read)
  - [Font](#font)
  - [Misc](#misc)
    - [raise](#raise)
    - [delete file](#delete-file)
    - [import](#import)
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

## Path

### exist

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
numpy.genfromtxt('file', names=True, usecols=(1,2))
```

### array

```py
numpy.arange()
```

### mask

```py
list_tof = (numpy.array([1,2]) == 1)
```

## Matplotlib

```py
from matplotlib import pyplot
import numpy
import matplotlib

matplotlib.rcParams['font.size']=15
matplotlib.rcParams['font.family']='sans-serif'
matplotlib.rcParams['font.sans-serif']=["Arial"]

fig, ax = pyplot.subplots()

ax.plot( array_data[0], array_data[1], label = '', linewidth=2)

ax.legend()
ax.set_xlabel('')
ax.set_ylabel('')
#ax.set_xlim((0,600))
#ax.set_ylim((0,700))
fig.set_size_inches(7, 6)
fig.savefig('', bbox_inches='tight')
pyplot.show()

```

## string

### leading zeros

<https://stackoverflow.com/questions/134934/display-number-with-leading-zeros>

```py
number = 1
print("%02d" % (number,))
print("{:02d}".format(number))
print(f"{number:02d}")
```

## class

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

## def

### Mutable default parameter

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

## subprocess

```python
import subprocess
subprocess.run( ['python','test.py'] )
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

### open

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

### read

```py
file_open.readline()
file_open.next()
next( file_open )
```

Note: `.readline()` can't used with `.next()`.

## Font

```bash
rm -r ~/.cache/matplotlib/
```

## Misc

### raise

```python
raise [exceptionName [(reason)]]
```

### delete file

```py
import os
import shutil

os.remove('test.x')   ## file
shutil.rmtree('temp') ## folder
```

### import

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
