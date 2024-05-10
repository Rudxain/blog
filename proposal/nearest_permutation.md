# General statement of the problem
Given a function F and a vector V, what's the optimal algorithm to permute the values in V, such that the [DFT](https://en.wikipedia.org/wiki/Discrete_Fourier_transform)s of F and V are as similar as possible?

# Specific statement of the problem
Given an audio file `A` and a binary file `B`, what's the fastest program to rearrange non-overlapping `N`-bit chunks in `B`, such that playing `B` as a `N`-bit `T`Hz PCM sounds as similar as possible to `A`?

`T` can be either:
- Chosen by the program, allowing greater similarity
- Chosen by the user, further constraining what the program can do
