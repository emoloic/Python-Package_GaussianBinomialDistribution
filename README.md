# Python Package (Gaussian and Binomial Distributions)

This repository contains a simple python package that analyze **Gaussian distribution** and **Binomial distribution.**

We can use the package to:
* **Read in dataset**
* **Calculate mean**
* **Calculate standard deviation**
* **Plot histogram**
* **Plot probability density function**
* **Add two gaussian (or binomial) distributions**

If you would like to review the Gaussian (normal) distribution and binomial distribution, here are a few resources:
* [Gaussian distribution](https://en.wikipedia.org/wiki/Normal_distribution)
* [Binomial distribution](https://en.wikipedia.org/wiki/Binomial_distribution)

A Python package does not need to use object-oriented programming. We could simply have a Python module with a set of functions. However, most—if not all—of the popular Python packages take advantage of object-oriented programming for a few reasons:

1- Object-oriented programs are relatively easy to expand, especially because of inheritance.
2- Object-oriented programs obscure functionality from the user. Consider scipy packages. You don't need to know how the actual code works in order to use its classes and methods.


## What is pip?

**pip** is a Python package manager that helps with installing and uninstalling Python packages. You might have used pip to install packages using the command line: **pip install numpy**. When you execute a command like **pip install numpy**, pip downloads the package from a Python package repository called [PyPi](https://pypi.org/).


## Making a Package

A **package** is a collection of Python modules. A python package also need a **__init__.py** file. This file is telling Python that the folder contains a package. The code inside this file gets run whenever you import a package inside a python program. You can can have a look of our package called [Gaussian-Binomial-distributions](./Gaussian-Binomial-distributions)
We also need to create a file called **setup.py**. This file should be at the same level as our Python package [Gaussian-Binomial-distributions](./Gaussian-Binomial-distributions). It's necessary for **pip install** (pip will automatically look for this file). This file contains informations (or metadata) about the package.


## Putting code on PyPi

### PyPi vs test PyPi

Note that [pypi.org](https://pypi.org/) and [test.pypy.org](https://test.pypi.org/) are two different websites. You'll need to register separately at each website. If you only register at pypi.org, you will not be able to upload to the test.pypy.org repository.

Remember that your package name must be unique. If you use a package name that is already taken, you will get an error when trying to upload the package.

Inside our package folder, we need to add extra file.
* **license.txt** - where you put copyright information. Example: MIT License(https://opensource.org/licenses/MIT)
* **README.md** - where you document how your package works.
* **setup.cfg** - where you define your README.md file.

### Instructions

You first need to open a terminal in this folder and then enter the following commands:

1. Build our package
```bash
python setup.py sdist 
```
This command will create many files. Inside the directory dist, there is a file with .tar extension that you are going to end up uploading to the PyPi repository.

2. Install **twine** (library used to upload package to PyPi)
```bash
pip install twine
```

3. Upload to the PyPi test repository
```bash
twine upload --repository-url https://test.pypi.org/legacy/ dist/*
```
You are required to provide your username and password from PyPi test website.

To install your package from the PyPi test repository, run the following command:
```bash
pip install --index-url https://test.pypi.org/simple/ (package-name)
```
You need to provide the name of the package you defined.
Once you're satisfied (all tests passed), you can now upload the package in PyPi repository where the package will be publicly available.

4. Upload to the PyPi repository
```bash
twine upload dist/*
```
Once again, you need to provide your username and password from PyPi website.
To install the package from PyPi, run the folloowing command:
```bash
pip install (python-package)
```
As you might notice, you do not need to provide the flag (--index-url) since our package is now public. Everyone can download it.


## Example

**Adding two gaussians**

```bash
from gaussian-binomial-distributions import Gaussian

guassian_one = Gaussian(5, 2)
guassian_two = Gaussian(10, 1=)
guassian_sum = guassian_one + guassian_two
print(guassian_sum.mean)
print(guassian_sum.stdev)
```
**Results:**

```bash
15
2.23606797749979
```

**Note:** To install your package on your local computer, you can create a virtual environment. A virtual environment is a silo-ed Python installation apart from your main Python installation. That way you can install packages and delete the virtual environment without affecting your main Python installation.
You can either use **conda** or **venv**.
If you want to know more on how to create a virtual environment with venv. Please, visit the this [link](https://www.freecodecamp.org/news/how-to-setup-virtual-environments-in-python/)


**Useful resource:** - https://www.geeksforgeeks.org/how-to-publish-python-package-at-pypi-using-twine-module/