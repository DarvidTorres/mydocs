- A module is related code.
- A package is a collection of modules.
- A library is a combination of modules and packages
	- package and library terms are used interchangeable


To find a package you have already installed, first [[Environment creation#^f69a0a|activate]] the environment you want to search.
```Conda
conda search <package_name>
```

To install package:
```Conda
conda install <package_name>
```

List packages:
```Conda
conda list
```

```
conda config --append channels conda-forge
```