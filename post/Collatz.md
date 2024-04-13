# My experience and questions about [CC](https://en.wikipedia.org/wiki/Collatz_conjecture)
This page is about all of the things I learned about the CC, and some unanswered questions I had along the way

## What if we pretend CC is false?
For all practical purposes, it's guaranteed to be true, but that's boring because nothing has changed. So what's so interesting about it being false? There are 2 types of counter-examples:

### Unknown cycle
If there are 2 ints n>4 & k>1, such that C^k(n) = n (where C^k is the Collatz function repeatedly applied k times), then there's a cycle that hasn't been discovered yet. Keep in mind, **every number in the cycle would satisfy that equation**, so we usually imply to find the smallest n that satisfies it.

The interesting thing is that, since cycles can't diverge, there may be **more than 1 of such cycles**, and we may never know.

### Divergence
If there's a n such that C^k(n) < C^(k+1)(n) **for all k**, then n diverges to +♾️. Again, just like the cycle, finding the minimal n is implied, as there would be **infinite solutions**.

This case is interesting because, unlike the cycle, we (maybe just me?) can infer more information about the properties of this value:
- it must be odd, as all evens would be reduced until it hits an odd number
- it would **persist to be odd** when using the "shortcut" fn, thereby explaining the unbound growth, as ×3 factor dominates ÷2 (the +1 doesn't contribute significantly to growth)

Thanks to the power of algebra™, we can pretend to do arithmetic with such a value. Let's call it ç, for short:
- 3ç + 1 = 0 mod 2
- (3ç + 1) ÷ 2 = 1 mod 2
- ?

That's about it 🤷‍♂. I couldn't think of more examples. And even if there were more examples, it wouldn't be a very useful number anyways, at least in the context of arithmetic.

Perhaps it could find practical use with respect to primes?

## See also
- [Numberphile](https://youtu.be/5mFpVDpKX70)
- [Veritasium](https://youtu.be/094y1Z2wpJg)
- [underrated video](https://youtu.be/i4OTNm7bRP8)
