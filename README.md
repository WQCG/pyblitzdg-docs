# Introduction

### What is pyblitzdg?

`pyblitzdg` is an open-source physical modelling platform built on C++. The end-user writes their computational model in python 3+ with `numpy`, and leaves the sophisticated \(often, boilerplate\) details to the behind-the-scenes C++ implementations provided by pyblitzdg.

The `pyblitzdg` platform began as a pet project by Derek Steinmoeller, and later evolved into one of the Waterloo Quantitative Consulting Group's core free open-source software initiatives. 

### Why use pyblitzdg?

The back-end of `pyblitzdg` focuses on robust and efficient C++ implementation details for Galerkin finite element methods with support for Discontinuous and Continuous Galerkin approaches in the python front-end. 

From a historical point-of-view, most scientific physical modelling programs were written by researchers using low-level languages such as C or Fortran for speed and memory efficiency. Since most numerical libraries only implement very low-level details not specific to finite element methods, this left a gap for most physical model developers to fill in on their own. As a result, it could take one or more years to complete model code development and establish via test-cases that the output is correct.

`pyblitzdg`alleviates these headaches by providing finite element implementations that are agnostic to their end use-case in a model. These implementations are backed by unit-tests asserting the correctness of each independent piece of the bigger puzzle, with a high percentage of code-path coverage and validating numerical assertions, `pyblitzdg` offers a base-line of openness and quality that you can count on for your model development work.

## License

<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Creative Commons Licence" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" href="http://purl.org/dc/dcmitype/InteractiveResource" property="dct:title" rel="dct:type">Pyblitzdg official docs</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="https://wqcg.ca" property="cc:attributionName" rel="cc:attributionURL">Waterloo Quantitative Consulting Group (WQCG, a not-for-profit corporation)</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License</a>.<br />Based on a work at <a xmlns:dct="http://purl.org/dc/terms/" href="https://dsteinmo.gitbook.io/pyblitzdg-official-docs/" rel="dct:source">https://dsteinmo.gitbook.io/pyblitzdg-official-docs/</a>.<br />Permissions beyond the scope of this license may be available at <a xmlns:cc="http://creativecommons.org/ns#" href="https://github.com/WQCG/pyblitzdg-docs" rel="cc:morePermissions">https://github.com/WQCG/pyblitzdg-docs</a>.
