# Nearest Permutation
This is a set of math/computer-science problems, not just 1.

## General statement of the problem
Given any function F and an arbitrary vector V, what's the optimal algorithm to permute the values in V, such that the [DFT](https://en.wikipedia.org/wiki/Discrete_Fourier_transform)s of F and V are as similar as possible?

Optionally, either of F or V can be set to a fixed value, thereby allowing specialized algorithms to be designed. If both were fixed values, then the algorithm would be trivial.

## Specific statement of the problem
Given an audio file `A` and a binary file `B`, what's the fastest program to rearrange non-overlapping `N`-bit chunks in `B`, such that playing `B` as a `N`-bit `T`Hz PCM sounds as similar as possible to `A`?

`N` & `T` can be either (or both):
- Chosen by the program, allowing greater similarity
- Chosen by the user, further constraining what the program can do

Just like the general problem, either (but not both) of `A` or `B` can be set to arbitrary data.

## Inspiration
- Audio-to-MIDI converters
- [Bytebeat](https://en.wikipedia.org/wiki/Low-complexity_art)

## Examples
If I asked you to rearrange the ASCII characters of the entire "Bee Movie" script, such that the bytes that represent those chars can be played as 8-bit ~40Khz PCM that sounds like N.G.G.Y.U. (Rick-Roll), how would you do it?

## etc
I bet some mathematician or computer-scientist can come up with an insane conjecture about this
