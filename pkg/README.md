# An example to understand Python's import bahavior

## Directory Structure
```
pkg/
| sub_pkg1/
| | __init__.py
| | module2.py
| sub_pkg2/
| | __init__.py
| | module3.py
| __init__.py
| main.py
| module1.py
```

## Key Take Aways

* Parent package must be in `sys.path`, in order for the the package to be installed.
* Relative import is only possible up to the parent module specified in the import(, therefore not in `main.py`!)
