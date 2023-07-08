* ``print(.packages())`` # List loaded packages
* ``detach("package:<package_name>")`` # Unload packages
* load packages if not loaded already

```R
if(! "<package_name>" %in% (.packages())){
  library("<package_name>")
  (.packages())
}
```

* ``require`` The required package will load if not loaded already