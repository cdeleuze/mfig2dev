# mfig2dev

## Export multiple related pictures from a single fig file.

This is a simple wrapper around `fig2dev` that uses the main comment
in the fig file to export objects at specific depths to a specific
output file.  This is usefull to create several variants of a figure,
eg in different languages, or a sequence of pictures for an animation.

Suppose file `main.fig` has following lines in the main comment:

    $$ -a 50,51,60
    $$ -b 50:52
    $$ -c 50,52:58,60:62

Then `mfig2dev pdf main.fig` will generate three files:

  - main-a.pdf with objects at depth 50, 51 and 60
  - main-b.pdf with objects at depth 50,51,52
  - main-c.pdf with objects at depths 50, 52 to 58 and 60 to 62
