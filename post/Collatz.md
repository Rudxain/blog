# My experience and questions about [CC](https://en.wikipedia.org/wiki/Collatz_conjecture)
This page is about all of the things I learned about the CC, and some unanswered questions I had along the way

## Relation with Mersenne
If `n` is a Natural that when tripled and incremented becomes a power of 2 then it's of the form `3n + 1 = 2^m`, thus equivalent to `n = M(m) / 3`, implying `M(m) mod 3 = 0`.

Therefore `m = 2k` for some int k, because `bitlen(3) = 2` (where `bitlen(x) := ilb(x) + 1`), so `n = (2^(2k) - 1) / 3`. There is a generalized theorem that explains why `M(2k) mod M(2) = 0`, and I don't remember where's the proof. However, [there is proof](https://math.stackexchange.com/questions/7473/prove-that-gcdan-1-am-1-a-gcdn-m-1) for the following theorem: `gcd(M(n), M(m)) = M(gcd(n, m))`

This means that `3n+1` is a **perfect square power of 2**, because it has an even count of trailing zeros in binary.

`n` would look like `...10101` in binary. Remember that `3x = 2x+x` for all Real `x`. Here's a "visual proof" of the previous paragraphs:
1. 10 × 10101 = `10101 << 1` = 101010
10. 101010 + 10101 = `101010 ^ 10101` = `101010 | 10101` = 111111 = M(110)
11. 111111 + 1 = 1000000 = 10^(10 × 11) = `1 << 110`
100. QED

## Counter-example searching optimization
According to [this](https://math.stackexchange.com/a/2285699), (if I understood correctly) an int of the form `2^a + n`, where `n` is a number already checked and `2^a >= n`, could be discarded if the length of the hailstone sequence of `n` is short enough to preserve at least 1 of the zeros of the most significant slice (the zeros that were added by the power of 2).

So a numeral like `0b10000000000000011` can be immediately discarded (not a counter-example candidate) because the hailstone length of 3 (`0b11`) is small, however a numeral like `0b10111` must be checked because the hailstone length of 7 (`0b111`) is too long to preserve the only `0` available.

## Unconditional fn limit
Let `f` be the "shortcut" Collatz function. Does the following limit converge for some unknown x?
```
lim n->∞ f^(n+1)(x) / f^n(x)
```
Is it irrational? If so, is it transcendental?

## What if we pretend CC is false?
For all practical purposes, it's guaranteed to be true, but that's boring because nothing has changed. So what's so interesting about it being false? There are 2 types of counter-examples:

### Unknown cycle
If there are 2 ints n>4 & k>1, such that C^k(n) = n (where C^k is the Collatz function repeatedly applied k times), then there's a cycle that hasn't been discovered yet. Keep in mind, **every number in the cycle would satisfy that equation**, so we usually imply to find the smallest n that satisfies it.

The interesting thing is that, since cycles can't diverge, there may be **more than 1 of such cycles**, and we may never know.

### Divergence
If there's a n such that C^k(n) < C^(k+1)(n) **for all k**, then n diverges to +♾️. Again, just like the cycle, finding the minimal n is implied, as there would be **infinite solutions**.

This case is interesting because, unlike the cycle, we (maybe just me?) can infer more information about the properties of this value:
- it must be odd, as all evens would be reduced until it hits an odd number
- it would **persist to be odd** when using the "shortcut" fn, thereby explaining the unbounded growth, as ×3 factor dominates ÷2 (the +1 doesn't contribute significantly to growth)

If we take a heuristic/statistical POV, **this is impossible**. But let's assume it is.

Thanks to the power of algebra™, we can pretend to do arithmetic with such a value. Let's call it ç, for short:
- 3ç + 1 = 0 mod 2
- (3ç + 1) ÷ 2 = 1 mod 2
- ?

That's about it 🤷‍♂. I couldn't think of more examples. And even if there were more examples, it wouldn't be a very useful number anyways, at least in the context of arithmetic.

Perhaps it could find practical use with respect to _primes_?
Maybe it's the key to proving _[RH](https://en.wikipedia.org/wiki/Riemann_hypothesis)?_

## See also
- [Numberphile](https://youtu.be/5mFpVDpKX70)
- [Veritasium](https://youtu.be/094y1Z2wpJg)
- [@makessenseright](https://youtu.be/i4OTNm7bRP8) (underrated)
- [Mem optimization](https://math.stackexchange.com/questions/3330085/computational-verification-of-collatz-problem)
- [Group of ints `mod n`](https://math.stackexchange.com/questions/3940237/collatz-problem-on-integers-modulo-n)
- [`÷ -2` instead of `2`](https://math.stackexchange.com/questions/2161249/collatz-divide-by-2-instead)
- [Benford's law applies](https://www.johndcook.com/blog/2017/05/03/the-3n1-problem-and-benfords-law)
