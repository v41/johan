# Project Johan
[_Johan_][1] is Indonesian word mainly used for name originated from Farsi [جهان][2] which means _world_.

## Background

The project is developed to explore options for simple grid-based location encoding systems beyond [QuadTree][3].
The goal is simple, split into n by n grid with sequence. Living in Southeast Asia, I am comfortable with simple planar solution compared to spherical solution such as [S2][5] or [H3][6] does.

I find [OpenLocationCode][4] quite excellent in shortening the index, yet too focused on avoiding easily confused characters and in return breaks the idea of sequencing, to compare or look two different codes and tell whether it is close together, as it excludes several characters which then requires another lookup to know which one is.

## Mapping
So here I try to generate the grid in multiple n. Since n=2 equal to QuadTree, we begin from n=3.
* n=3. 123456789 (0 unused)
* n=4. 0123456789ABCDEF
* n=5. ABCDEFGHIJKLMNOPQRSTUVWXY (Z unused)
* n=6. 0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ

Implementation wise, it is possible to apply either 2-dimensional (pairwise index) or 1-dimensional (combined index), but in this example I will focus on the latter.

## Recommendation
I find n=3 is simple enough to be represented in numeric and also more easy to go into gamification. TicTacToe, colors (RGB) even sudoku are based on 3x3, not to mention phone dial sequence with missing 0. Extended to n=4 we can use hexadecimal sequence which fits perfectly. Going n=5 we can go alphabet mode excluding Z character. n=6 is another perfect fit by using complete alphanumeric. We could possibly go on beyond by using lower/upper case and all the ASCII symbols but I'd leave those imagination to the readers and tweakers.


[1]: https://kbbi.kemdikbud.go.id/entri/johan
[2]: https://en.wiktionary.org/?curid=183930
[3]: https://docs.microsoft.com/en-us/bingmaps/articles/bing-maps-tile-system
[4]: https://github.com/google/open-location-code/wiki/Evaluation-of-Location-Encoding-Systems
[5]: https://docs.google.com/presentation/d/1Hl4KapfAENAOf4gv-pSngKwvS_jwNVHRPZTTDzXXn6Q/view
[6]: https://h3geo.org/docs/highlights/indexing/
