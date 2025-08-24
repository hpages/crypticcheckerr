A minimal package to help reproduce the following cryptic warning and error
produced by `R CMD check`:

    * checking Rd contents ... OK
    * checking for unstated dependencies in examples ... ERROR
    Warning: parse error in file 'lines':
    37:12)
    ** will not attempt to run examples
    * checking examples ... SKIPPED

The name of the file where the parse error happens (`lines`) is meaningless
(the package does not have such file). Also the line:col numbers are incorrect.

The correct location of the parse error is position 12 of line 11 in
file `man/manpage2.Rd`.

FWIW the issue can be debugged interactively by running:

    library(tools)
    debug(tools:::.check_packages_used_in_examples)
    tools:::.check_packages_used_in_examples("crypticcheckerr")

after installing **crypticcheckerr**.

This issue is being tracked here: https://bugs.r-project.org/show_bug.cgi?id=18907

