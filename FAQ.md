# Frequently Asked Questions


* [What is the difference between `id` and `name`?](#what-is-the-difference-between-id-and-name)
* [Why are certain constants included but others are not?](#why-are-certain-constants-included-but-others-are-not)
* [Why are certain entries empty?](#why-are-certain-entries-empty)
* [Do I need the Symbolic Math Toolbox to use `Constants`?](#do-i-need-the-symbolic-math-toolbox-to-use-constants)


## What is the difference between `id` and `name`?


The `id` is the constant's current name, while `name` shows its historical names. The `id` remains fixed, but the `name` of a given constant may change between datasets.

```matlab
const = Constants('all', 'all');
const.epsilonzero.id         % current name
const.epsilonzero.name(1:5)  % historical name in the 1998-2014 datasets
```
Output:

```console
'vacuum electric permittivity'
"electric constant"    "electric constant"    "electric constant"    "electric constant"    "electric constant"
```


## Why are certain constants included but others are not?


`Constants` contains constants with **dedicated symbols** specified by CODATA, but excludes derived or assembled constants without unique symbols.

For example, the electron mass ($m_\textnormal{e}$) and elementary charge ($e$) have dedicated symbols and are included in `Constants`, but the electron charge to mass quotient, $-e / m_\textnormal{e}$, is not.


## Why are certain entries empty?


Entries are empty in individually loaded datasets if the constant does not exist in the dataset.

For example, the value of the Faraday constant for conventional electric current ($F^*$) is not listed in the [2018 dataset](https://physics.nist.gov/cuu/Constants/Table/allascii.txt) and is therefore empty:

```matlab
const = Constants('all', '2018');
const.Fstar
```

Output:

```console
[]
```


## Do I need the Symbolic Math Toolbox to use `Constants`?


No. `Constants` will run fine even without the Symbolic Math Toolbox present. In this case, `symvalue`, `symunit`, and `sym` will not be available as options for the first argument and will not be listed as part of the data structure.