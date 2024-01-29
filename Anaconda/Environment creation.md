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

- To activate environment: ^0d9fbb
```Conda
conda activate <env-name>
```

^f69a0a

- Deactivate environment:
```Conda
conda deactivate <env-name>
conda deactivate # Deactivates active environment
```
Note: Deactivate environments when not being used is a best practice.

Verify which version of Python is in your current environment:

```Conda
python --version
```

- Remove an environment
```Conda
conda remove --name <env_name> --all
conda env remove --name myenv # Same as above
```