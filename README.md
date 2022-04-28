# Project Johan
[_Johan_][1] in Indonesian mainly used for name and originated from Farsi [جهان][2] which means _world_.

## Background

The project is developed to explore options for simple grid-based location encoding systems beyond [QuadTree][3].
The goal is simple, split into k x k grid with alphanumeric sequence. Living in Southeast Asia, I am comfortable with simple planar solution compared to spherical solution such as [S2][5] or [H3][6] as the distortion is quite minimal.

I find [OpenLocationCode][4] quite excellent in shortening the index, yet too focused on avoiding easily confused characters and in return breaks the intuitiveness, as it excludes several characters.

## Mapping
So here I try to generate the grid in multiple k. Since k=2 equal to QuadTree, we begin from k=3.
* k=3, n=9. 123|456|789 (0 unused)
* k=4, n=16. 0123|4567|89AB|CDEF
* k=5, n=25. ABCDE|FGHIJ|KLMNO|PQRST|UVWXY (Z unused)
* k=6, n=36. 012345|6789AB|CDEFGH|IJKLMN|OPQRST|UVWXYZ

Implementation wise, it is possible to apply either 2-dimensional (pairwise index), 1-dimensional (combined index) ,or even a mix of both, but in this example I will focus on the latter to make this as basic and intuitive as possible.

I find k=3 is simple enough to be represented in numeric and also  fits for gamification. TicTacToe, colors (RGB) even sudoku are based on 3x3, not to mention phone dial sequence with missing 0. Extended to k=4 we can use hexadecimal sequence which fits perfectly. Going k=5 we can go alphabet mode excluding Z character. k=6 is another perfect fit by using complete alphanumeric. We could possibly go on beyond by using lower/upper case and all the ASCII symbols but I'd leave those imagination to the readers and tweakers.

## Recommendation
Personally I think initial k should be bigger as it likely get static at country level. The use of alphanumeric (k=4 or k=6) might not be a favorable option if we decide to mix the k. Of course using k=6 seems like the best deal for the encoding part, but intuitiveness is not just about the shortest sequence. Optionally k=6 may be an option for 2=dimensional but then its a matter of character confusion part.

Therefore I'm ended in favor of using a mix of k=3 and k=5. First 2-3 uses k=5, followed by 2-4 k=3, then it repeats as having a too long numeric sequence might also be easier to forget.


[1]: https://kbbi.kemdikbud.go.id/entri/johan
[2]: https://en.wiktionary.org/?curid=183930
[3]: https://docs.microsoft.com/en-us/bingmaps/articles/bing-maps-tile-system
[4]: https://github.com/google/open-location-code/wiki/Evaluation-of-Location-Encoding-Systems
[5]: https://docs.google.com/presentation/d/1Hl4KapfAENAOf4gv-pSngKwvS_jwNVHRPZTTDzXXn6Q/view
[6]: https://h3geo.org/docs/highlights/indexing/
