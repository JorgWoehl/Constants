# Frequently Asked Questions


* [What is the difference between `id` and `name`?]()
* [Why is variable _X_ included in `Constants` but _Y_ is not?]()
* [Why are certain entries empty?]()

## What is the difference between `id` and `name`?


The `name` and other properties of a constant may change over the years, but its `id` is fixed. By definition, the `id` is the name of the constant in the latest dataset.

```matlab
const = Constants('all', 'all');
const.epsilonzero.id         % current name
const.epsilonzero.name(1:5)  % name in 1998-2014 datasets
```
Output:

```console
'vacuum electric permittivity'
"electric constant"    "electric constant"    "electric constant"    "electric constant"    "electric constant"
```


## Why is variable _X_ included in `Constants` but _Y_ is not?


`Constants` only contains constants with a **dedicated symbol**, but derived or assembled constants are not included.

For example, the electron mass (symbol $m_\textnormal{e}$) and elementary charge (symbol $e$) have dedicated symbols and are therefore included in `Constants`. However, the electron charge to mass quotient, $-e / m_\textnormal{e}$, does not have a dedicated symbol, and -- although it appears in the 2018 dataset -- is therefore not included in `Constants`.


## Why are certain entries empty?


Constants that are not included in an individually loaded dataset appear empty. 

For example, the value of the Faraday constant for conventional electric current ($F^*$) is not listed in the 2018 dataset and is therefore empty:

```matlab
const = Constants('all', '2018');
const.Fstar
```

Output:

```console
[]
```