# This is where we document our the package works.

In other to use this package, please make sure matplotlib library is already installed in your python environment.

You can install it by enter the following command:
```
bash
pip install matplotlib
```

Once the libary is installed, run the following command to install the package:
```
bash
pip install gaussian-binomial-distributions
```

## Example

**Adding two gaussians**

```
bash

from gaussian-binomial-distributions import Gaussian

guassian_one = Gaussian(5, 2)
guassian_two = Gaussian(10, 1=)
guassian_sum = guassian_one + guassian_two
print(guassian_sum.mean)
print(guassian_sum.stdev)
```
**Results:**

```
bash
15
2.23606797749979
```