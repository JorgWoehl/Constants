# Frequently Asked Questions


* [What is the difference between `id` and `name`?](#what-is-the-difference-between-id-and-name)
* [Why are certain constants included but others are not?](#why-are-certain-constants-included-but-others-are-not)
* [Why are certain entries empty?](#why-are-certain-entries-empty)
* [Do I need the Symbolic Math Toolbox to use `Constants`?](#do-i-need-the-symbolic-math-toolbox-to-use-constants)


## What is the difference between `id` and `name`?


The `id` is the constant's current name, while `name` provides its historical name. The `id` remains fixed, but the `name` of a given constant may change between datasets.

```matlab
const = Constants('all', 'all');

% get the current name
const.epsilonzero.id

% get historical names from 1998-2014 datasets
const.epsilonzero.name(1:5)
```
Output:

```console
'vacuum electric permittivity'
"electric constant"    "electric constant"    "electric constant"    "electric constant"    "electric constant"
```


## Why are certain constants included but others are not?


The `Constants` object contains constants with **dedicated symbols** specified by CODATA but excludes derived or assembled constants without unique symbols.

For example, the electron mass (_m_<sub>e</sub>) and elementary charge (_e_) have dedicated symbols and are included in `Constants`, but the electron charge to mass quotient, -_e_ / _m_<sub>e</sub>, is not included since it does not have a unique symbol.


## Why are certain entries empty?


Entries are empty in individually loaded datasets if the constant does not exist in the dataset.

For example, the value of the Faraday constant for conventional electric current (_F_<sup>*</sup>) is not listed in the [2018 dataset](https://physics.nist.gov/cuu/Constants/Table/allascii.txt), so it will be empty when loading that specific dataset:

```matlab
const = Constants('all', '2018');
const.Fstar
```

Output:

```console
[]
```


## Do I need the Symbolic Math Toolbox to use `Constants`?


No. `Constants` will work just fine without the Symbolic Math Toolbox. However, the `symvalue`, `symunit`, and `sym` options will only be available if the Symbolic Math Toolbox is present.