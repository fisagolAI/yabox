<img src='../master/docs/images/yabox.png?raw=true' width=250 align=right />

# Yabox

_Yet another black-box optimization library for Python_

## Description

Yabox is a very small library for black-box (derivative free) optimization of functions that only depends on `numpy` and `matplotlib` for visualization. The library includes different stochastic algorithms for minimizing a function `f(X)`  that does not need to have an analytical form, where `X = {x1, ..., xN}`.
The current version of the library includes the Differential Evolution algorithm and a modified version for parallel evaluation.

Example of minimization of the Ackley function (using Yabox and Differential Evolution):

![Ackley Function](../master/notebooks/img/ackley.gif?raw=true)

## Basic usage

### Pre-defined functions
Yabox includes some default benchmark functions used in black-box optimization, available in the package yabox.problems. These functions also include 2D and 3D plotting capabilities:

```python
>>> from yabox.problems import CrossInTray
>>> problem = CrossInTray()
>>> problem.plot3d()
```

![CrossInTray Function](../master/docs/images/crossintray.png?raw=true)

A problem is just a function that can be evaluated for a given X:
```python
>>> problem(np.array([1,1,1]))
-2.0342415830385301
```


### Optimization

Simple example minimizing a function of one variable `x` using Differential Evolution, searching between -10 <= x <= 10:

```python
>>> from yabox import DE
>>> DE(lambda x: sum(x**2), [(-10, 10)]).solve()
(array([ 0.]), 0.0)
```

Example using Differential Evolution and showing progress (requires tqdm)

![Optimization example](../master/docs/images/opt_example.gif?raw=true)

## About

This library is inspired in the scipy's differential evolution implementation. The main goal of Yabox is to include a larger set of stochastic black-box optimization algorithms plus many utilities, all in a small library with minimal dependencies.

