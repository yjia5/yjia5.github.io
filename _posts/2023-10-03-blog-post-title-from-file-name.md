Error when install devtool to conda

cran does not compile with conda very well. So there is error when install devtool with install.packages().
Instead, if using conda, try to keep use conda install.

Another way is use remotes instead of devtool. Remotes can be installed easily from cran.
install.packages("remotes")
Then use remotes to instlal packages from github.
remotes::install_github("genecell/COSGR") 
