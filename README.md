# Specifying an R environment with a runtime.txt file

Binder supports using R and RStudio, with libraries pinned to a specific
snapshot on [packagemanager.rstudio.com](https://packagemanager.rstudio.com/client/#/).

### Requirements and suggestions
#### Create/Edit `runtime.txt` 
You need to create or edit [`runtime.txt`](binder/runtime.txt) file that is located in the `binder` folder and formatted like:

```
r-<r-version>-<YYYY>-<MM>-<DD>
```

where `<r-version>` is a version of R (like 4.1, 4.0, etc) you want to use,
and `<YYYY>-<MM>-<DD>` is the date for [a snapshot](https://packagemanager.rstudio.com/client/#/repos/1/overview)
from [packagemanager.rstudio.com](https://packagemanager.rstudio.com) that will
be used for installing your R packages.

Try using a date newer than `2022-01-01`, as you'll get faster
package installs thanks to [binary packages](https://www.rstudio.com/blog/package-manager-v1-1-no-interruptions/)
from rstudio.packagemanager.com!

#### (Pre-)Install packages

To install R libraries, add `install.package("<package-name>")` calls to
[`install.R`](binder/install.R) located in the `binder` folder. If you want to pin to a specific version of the library, you
can also do `devtools::install_version("<package-name>", "<version>")`.

For some R packages, you might need to install system packages via apt - you can
do so by writing out a list of apt package names in `apt.txt`. You can find
the list of such packages in the page for your package at
[packagemanager.rstudio.com](https://packagemanager.rstudio.com/client/#/). Make sure
to select "Ubuntu 18.04 (Bionic)" in the dropdown on the top right.