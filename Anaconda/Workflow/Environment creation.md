```Conda
conda --version
conda env list # List of conda environments
conda info --envs # Same as above
```
Note: The active environment is the one with an asterisk (`*`). Don't work in `base`.

- To create an environment:
```Conda
conda create -n <env-name> [python[=<version>]] [<package_name>[=<version>]...]
```

Example:
```Conda
conda create -n my_env python=3.9 scipy=0.17.3 pandas
```



- Reproducible environments are created using YAML.