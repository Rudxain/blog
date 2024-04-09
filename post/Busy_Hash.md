# Busy-Beaver Hash
> If [Busy Beavers](https://en.wikipedia.org/wiki/Busy_beaver) are so slow, why not use them for [password hashing](https://en.wikipedia.org/wiki/Password_Hashing_Competition)?

There's only 1 problem: **BBs are stuck at a local maximum**. This is because they are [tuned to win if the tape is all zeros](https://en.wikipedia.org/wiki/Overfitting), not an arbitrary sequence of 1s and 0s.

Why is this a problem? 2 reasons:

- [timing](https://en.wikipedia.org/wiki/Timing_attack)
- unreliability

A BB may stop processing a tape, even before it has touched all the bits between the ends of the input data. So we might have to run the BB multiple times at different "tape addresses" to get "full" [diffusion](https://en.wikipedia.org/wiki/Confusion_and_diffusion).

Most cryptographic algorithms have some subroutine that's ["recursively" iterated](https://en.wikipedia.org/wiki/Round_(cryptography)) over the data, so this isn't a bad thing per-se. The problem is that it **leaks timing information** that could be used to infer some bits of the password. This is **very bad.**

However, in practice, BBs such as the current 5-state winner are so unpredictable, that timing-info will be near-useless.

But there's also [HP](https://en.wikipedia.org/wiki/Halting_problem), which is the opposite problem of halting prematurely. Even just a single BB-round may enter an **infinite loop**, which is totally undesirable and undecidable (pun intended)

This means we also have to set a runtime limit to guard against it:
- Setting a timeout will make the digest non-deterministic. This is a no-go.
- Forcing a halt after the whole password has been processed, is not enough. It may enter an infinite loop that never digests the full password.
- Setting a *shift* limit is a reliable alternative.

For a standard BB, the number of shifts is directly proportional to the number of (cumulative) times any bit has been processed, which is sometimes proportional to the number of *unique* bits processed.

This has the advantage that different shift limits will yield different hashes, deterministically.

Now, how do we ensure the resulting tape has a fixed size? If we model the BB as an [LBA](https://en.wikipedia.org/wiki/Linear_bounded_automaton), the tape would have the same length as the password, which is not very helpful. We could truncate the hash by using an [XOR-hasher](https://github.com/Rudxain/xorsum), which preserves (and sometimes increases) _entropy-density_ (not the same as absolute entropy).

I just realized that LBAs don't have a halting-problem, so we can simply use more memory to detect when an infinite loop happens. This has the added advantage of increasing resource-usage for crackers, as the loop-detection algorithm is hard to optimize and affects the resulting hash
