NOTE: this repo is no more updated, dev now occurs on gitlab <https://gitlab.com/deleuzec/mfig2dev>

# mfig2dev

## Export multiple related pictures from a single fig file

This is a simple wrapper around `fig2dev` that uses the main comment
in the fig file to export objects at specific depths to a specific
output file.  This is usefull to create several variants of a figure,
eg in different languages, or a sequence of pictures for an animation.

### Variants of a figure

Here's a simple example, circle.fig

	#FIG 3.2  Produced by xfig version 3.2.8
	Landscape
	Center
	Metric
	A4
	100.00
	Single
	-2
	# layer comments for mfig2dev
	# $$ -en 50,51
	# $$ -fr 50,52
	# $$ -eo 50,53
	1200 2
	# a simple circle, at depth 50
	1 3 0 1 0 7 50 -1 -1 0.000 1 0.0000 3870 3960 860 860 3870 3960 4725 4050
	# an english text, at depth 51
	4 1 0 51 -1 0 12 0.0000 4 135 630 3870 3960 A circle\001
	# a french text, at depth 52
	4 1 0 52 -1 0 12 0.0000 4 135 765 3870 3960 Un cercle\001
	# an esperanto text, at depth 53
	4 1 0 53 -1 0 12 0.0000 4 135 480 3870 3960 Cirklo\001

`mfig2dev pdf circle.fig` will generate three files:

  - circle-en.pdf with objects at depth 50 and 51: the circle and english text
  - circle-fr.pdf with objects at depth 50 and 52: the circle and french text
  - circle-eo.pdf with objects at depth 50 and 53: the circle and esperanto text
  
![circle-en](https://gitlab.com/deleuzec/mfig2dev/wikis/circle-en.png)
![circle-fr](https://gitlab.com/deleuzec/mfig2dev/wikis/circle-fr.png)
![circle-eo](https://gitlab.com/deleuzec/mfig2dev/wikis/circle-eo.png)

### Sequence of figures for an animation

The edns.fig file has the following layer comments

	# $$ 1 50,51
	# $$ 2 50:52
	# $$ 3 50:53
	# $$ 4 50:54

so that `mfig2dev png edns.fig` will generate files `edns1.png`, `edns2.png`, `edns3.png` and `edns4.png`:

![edns1](https://gitlab.com/deleuzec/mfig2dev/wikis/edns1.png)
![edns2](https://gitlab.com/deleuzec/mfig2dev/wikis/edns2.png)
![edns3](https://gitlab.com/deleuzec/mfig2dev/wikis/edns3.png)
![edns4](https://gitlab.com/deleuzec/mfig2dev/wikis/edns4.png)
