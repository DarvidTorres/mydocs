Conda keeps a history of all the changes made to your environment, so you can easily "roll back" to a previous version.

- To list the history of each change to the current environment: `conda list --revisions`.
- To restore environment to a previous revision:
```Conda
conda install --revision=<revision_numer>
conda install --rev <revision_number>
```

