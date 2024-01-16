```Conda
conda --version
conda env list # List of conda environments
conda info --envs # Same as above
```
Note: The active environment is the one with an asterisk (`*`). Don't work in `base`.

- To create an environment:
```Conda
conda create --name <env-name> [python[=<version>]] [<package_name>[=<version>]...]
```

Example:
```Conda
conda create -n my_env python=3.9 pandas=2.1.4 numpy
```

- To activate environment:
```Conda
conda activate <env-name>
```

- Deactivate environment:
```Conda
conda deactivate <env-name>
conda deactivate # Deactivates active environment
```

- Reproducible environments are created using YAML.