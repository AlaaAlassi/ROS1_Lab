# ROS1_Lab
a workspace for ros 1

# How to structure a Python-based ROS package 
[How to structure a Python-based ROS package](http://www.artificialhumancompanions.com/structure-python-based-ros-package/)

How does a node or script file actually import our main code?

Python looks for modules or Python packages in the current directory or on the path specified by the environment variable PYTHONPATH. We shouldn’t manipulate PYTHONPATH ourselves, but get Catkin to do it for us. To do that, we need to configure a file called setup.py in <base dir>.

setup.py is a standard Python file used for creating a distributable, installable chunks of code (I refuse to use the word “package” with yet another meaning). This process is handled by a Python tool suite called distutils which is documented here, for those that are interested. For our purposes, we simply need to use setup.py to tell Catkin the name of our Python package (“mypackage”) and where it is located (in the directory “src”). Here is an example of setup.py:
```python
#!/usr/bin/env python

from distutils.core import setup
from catkin_pkg.python_setup import generate_distutils_setup

setup_args = generate_distutils_setup(
     packages=['mypackage'],
     package_dir={'': 'src'}
)

setup(**setup_args)
```
