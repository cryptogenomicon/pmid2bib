# pmid2bib: format a BibTeX entry, given a pubmed id

Usage: `pmid2bib <PMID>`  
Example: `pmid2bib 13882203`

```
@Article{CITEKEY,
  author     = {F. H. Crick and L. Barnett and S. Brenner and R. J. Watts-Tobin},
  title      = {General Nature of the Genetic Code for Proteins},
  journal    = {Nature},
  year       = 1961,
  volume     = 192,
  pages      = {1227--1232},
  pmid       = 13882203,
  reprinturl = {https://doi.org/10.1038/1921227a0},
}
```

`pmid2bib` produces a nighly-formatted BibTeX entry given a PubMed
identifier (a PMID).  You have to add the CITEKEY yourself
(e.g. Crick61). You may need to do some light editing of things that
the script isn't smart enough to do. For example, check for accented
characters on authornames, capitalization and italics (species names)
in titles, and your preferences for journal abbreviation.

The `pmid` and `reprinturl` fields in the entry are noncanonical
custom fields that I use in my own `.bib` files.

The script is rudimentary, with rudimentary rules. The goal is to get
something close enough to save a lot of typing time, not to get every
detail.

The script uses `urllib.request` to obtain an XML entry from PubMed,
and `xml.etree.ElementTree` to parse that XML. The script also doed
some light rule-based stuff to format the author names as
initials/surname (as "X. Y. Foo and A. B. Bar and Z. Baz"),
standardize capitalization in titles (including recognizing some
common species names to leave them uncapitalized - but you'll need to
add the `\emph{}` italics yourself), and switch in some of our most
commonly used journal abbreviations.

See the source code of the script itself (which is brief) for more
detail on what and how it's formatting.












