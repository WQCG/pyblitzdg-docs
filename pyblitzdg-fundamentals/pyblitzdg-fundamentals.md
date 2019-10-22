---
description: Instructions for how to install pyblitzdg on top of your python environment
---

# Installing the Latest Pyblitzdg

### Preliminaries

To install `pyblitzdg` , we first need a Python 3+ installation with pip installed. If you don't have Python 3 yet, and are on Windows, we recommend the Anaconda python distribution since it comes pre-loaded with a wide-array of useful numerical libraries.

Assuming you've gotten python3 installed on your own, you next need the package managing command-line utility `pip`to install `pyblitzdg`.

To achieve this first step, we suggest downloading the `get-pip.py` python script and running it with python3. It can be downloaded from [https://bootstrap.pypa.io/get-pip.py](https://bootstrap.pypa.io/get-pip.py).

Next, install the latest `pyblitzdg` package using pip.

```
$ pip3 install pyblitzdg
```

{% hint style="info" %}
 Depending on the type of python installation you have, the 'pip' command may be named either 'pip3' \(for example, on linux that has python 2 and 3 installed\) or just 'pip' \(for example, in an Anaconda environment\), to distinguish from the python 2 executable.
{% endhint %}

If you have a python 3 installation that does not already have `numpy` and `scipy` packages, we recommend you install those as well, e.g.,

```
$ pip3 install numpy
$ pip3 install scipy
```

Congratulations, you're now ready to develop new model code using the `pyblitzdg` platform.

