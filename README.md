A minimal package to help reproduce the following cryptic warning and error
produced by `R CMD check`:

    * checking Rd contents ... OK
    * checking for unstated dependencies in examples ... ERROR
    Warning: parse error in file 'lines':
    37:12)
    ** will not attempt to run examples
    * checking examples ... SKIPPED

The name of the file where the parse error happens (`lines`) and the
line:col numbers are meaningless, so the developer of the package are
on their own!

FWIW the issue can be debugged interactively by running:

    library(tools)
    debug(tools:::.check_packages_used_in_examples)
    tools:::.check_packages_used_in_examples("crypticcheckerr")

after installing **crypticcheckerr**.

