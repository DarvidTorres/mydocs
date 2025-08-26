Now the last part, making it work. For that, the R extension for VSCode has really good documentation, there is also R Debugger you must have. The main points that are needed for installation are as follows

- languageserver: Installed from the R console with `install.packages("languageserver")`
    
- httpgd: Also from the R console with `install.packages("httpgd")`
    

Now, I also work a bit with Markdown, so I have installed that package as well using `install.packages("rmarkdown”)` in the R console, and the dependency Pandoc

To finish the setup there are a couple of paths that are very useful to know, to paste in the config file settings.json. I’ll list those below.

- Radian path: Found typing in the terminal `where radian`
    
- R path: Found typing in terminal `where R`
    
- R library paths: Found going into the R console (type `R` in the terminal) and inside type `.libPaths()`
    

Those paths need to be entered into the settings.json file in the following configuration options. If you are on windows, the settings would be.

"r.rterm.windows": Radian path,
"r.rpath.windows": R Path, 
R path: Found typing in the terminal  separated by ","\]

Additionally, after following the configuration recommendation from the extension, these are the settings I ended up with.

 "r.bracketedPaste": true,
 "files.associations": {
     "*.Rmd": "rmd"
 },
 "r.plot.useHttpgd": true,
 "r.rterm.option": [
     "--no-restore"
 ],

And with this, the setup is finished.