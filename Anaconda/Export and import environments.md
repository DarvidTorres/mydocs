# Export

When creating an environment and installing packages, Conda will download and install numerous additional packages to solve for dependencies, which may introduce packages incompatible across platforms (causing conflicts).

If you want to make your environment file work across platforms, you can use the `conda env export --from-history` flag. This will only include packages that you’ve explicitly asked for, as opposed to including every package in your environment.

If you use `conda env export`, it will export all of other packages.

Use `>` to pipe the output of command to a `.yml` file:
```Conda
conda env export > my_env.yml
```

# Import

Create the environment from a YAML file:
```Conda
conda env create --file <file_name>.yml
```

