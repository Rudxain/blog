# Reusable Terms and conditions
Here I'll lay-out my proposal for making human-friendly contracts, without sacrificing basic nuance.

This is a [WIP](https://en.wikipedia.org/wiki/Work_in_process), so please don't assume a finished state. Suggestions are welcome! (**warning:** I haven't chosen an open license, yet).

## Intro
You know what the following have in common:
- Licenses
- Terms and Conditions
- Terms of Service
- Privacy Policy
- Literally any sort of contract

But I'll outline them anyways, for emphasis:
- They're long and verbose
- They're filled with [legalese](https://en.wikipedia.org/wiki/Legal_writing#Legalese)
- If they aren't verbose/legalese, they tend to be ambiguous
- They have similar glossaries, sentences, and even full paragraphs, in common with other legal documents of the same kind (sometimes even identical replicas!)
- It's hard to properly write one, so you either copy-paste a template or hire lawyer
- Multi-service organizations tend to avoid declaring accurate terms for individual services. Rather, they treat all services as a unit (easier for them), taking away more user rights. Example: Google-Keep doesn't need location data, but G-Maps certainly does, so they [CTA](https://en.wikipedia.org/wiki/Cover_your_ass) by saying "We may collect location data at any time, without notice." (not verbatim quote) rather than "Here's an exhaustive list of services that collect location data..."

The year is almost **2025 and humanity hasn't fixed this simple issue** for decades (**millennia**, if we're being unfair).

## Inspiration
The following is a list of resources to which I feel grateful:
- [Hyper-media](https://en.wikipedia.org/wiki/Hypermedia) has already solved this for arbitrary content (information, misinformation 🤡, raw data, graphics, audio, text, executables, etc...)
- [Nicky Case's "Nutshell"](https://ncase.me/nutshell) extends the concept of hyper-media to be more interactive. But this isn't a [Web Standard](https://en.wikipedia.org/wiki/Web_standards) or a [Web Browser API](https://developer.mozilla.org/en-US/docs/Web/API), yet...
- [SPDX](https://en.wikipedia.org/wiki/Software_Package_Data_Exchange) has _mostly_ solved this for [OSS](https://en.wikipedia.org/wiki/Open-source_software) licenses. If you want a modified version of a license, you must [inline](https://en.wikipedia.org/wiki/Inline_expansion) the full text anyways... ([square 1](https://en.wiktionary.org/wiki/back_to_square_one)).
- The [OpenPD](https://openpd.org/) aims to solve this for privacy-policies.
- There's [this paper about "Machine-Readable Privacy Notices"](https://ieeexplore.ieee.org/document/10386763). I haven't read it yet, I'm just referencing it.
- [This tool](https://rejectconvenience.com/privacy-visualizer) helps users "digest" privacy-policies, but doesn't solve the underlying problem.

## Why?
As a "layperson", you might wonder:
> why can't [orgs](https://en.wikipedia.org/wiki/Organization) and [corps](https://en.wikipedia.org/wiki/Corporation) simply say
> "BTW, our terms are the same as Google's, except for this part"

The whole point of "legally-valid" contracts is that there should be no ambiguity (this is why legalese looks like a programming language), as any omitted detail could become a [loop-hole](https://en.wikipedia.org/wiki/Loophole), which is equivalent to a [software vulnerability](https://en.wikipedia.org/wiki/Vulnerability_(computer_security)). That's the reason why there's so much legalese, because lawyers need to cover **everything** (every possible scenario in the past, present, and future), to protect the org from "abusive users" exploiting the holes.

This goes both ways: A "legal [bug](https://en.wikipedia.org/wiki/Software_bug)" could be so unintentionally strict, that [100% of the target demographic would be forbidden from using the service](https://web.archive.org/web/20241008105526/https://github.com/WinampDesktop/winamp/issues/2656).

Even if they could refer to an existing contract in a "rigorous" way, there's still the problem of **stability**: What happens if your TOS links to Firefox TOS, and then Mozilla **updates** it? The update will [effect](æfect.md) the meaning of your TOS, because it could change arbitrary sentences in a way that you may or may not intend.

> Well, then what about versioning? Why not slap a [sem-ver](https://semver.org/) number and [CIAD](https://en.wiktionary.org/wiki/call_it_a_day)?

Because you're still referring to the contract using whatever identifier the author invented. This is prone to fragmentation (see [Linux distros](https://itsfoss.com/desktop-linux-torvalds/) and [this XKCD](https://xkcd.com/927/)) as every contract author may use different naming conventions and versioning schemes, heck they can even be inconsistent with themselves! (see [USB3](https://news.ycombinator.com/item?id=31069128))

## Solution
Here comes my proposed solution...

A standard international registry of (unique) contract identifiers. Each identifier maps (associated) to a complete, clear, unambiguous, legally-sound, document that could be used as-is or as a template for customized docs. Every major (semantically breaking) update must have a different version number, and the previous version must still be available for reference.

To allow custom contracts to specify modifications ([`diff`s](https://en.wikipedia.org/wiki/File_comparison)), a standard diff description format (like Git's) should be used for machine-readable text. For human consumers, something like `Section 3, paragraph 5, sentence 4, is to be replaced with "blah bleh..."` could be used instead, but each one of those "part-numbers" must be rigorously defined by the specification (How exactly do we split sentences?), not the author of the custom-contract.

## Outro
I guess that's it! It really is ["quite simple"](https://youtu.be/7iHGoBVLtyY).

It's worth noting that this won't magically solve the problem of ill-intentioned data-hoarders, which are happily willing to abuse [dark patterns](https://www.deceptive.design/) such as opaque privacy-policies to deter users from protecting their data
