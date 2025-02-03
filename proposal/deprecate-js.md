## Intro
This started [here](https://es.discourse.group/t/ecmascript-proposal-hash-comments-replacement-for-type-annotations/2287/16), but I've been considering writing this for a long time:

- ["evar"](https://github.com/Rudxain/ideas/blob/a0d27af11dee9bacdb6e14a4024c765084e98573/software/evar/README.md?plain=1#L28-L31)
- [Wasm is still in its infancy](https://github.com/rust-lang/arewewebyet/issues/442)
- [YT comment](https://youtube.com/watch?v=onCHSujPlfg&lc=UgxBTDoMyVj2AUFZPQN4AaABAg.A9waZIJwHKLAA6stKkYwbR)
- [YT comment](https://youtube.com/watch?v=onCHSujPlfg&lc=UgzsApR__1Gwz-2OYRB4AaABAg.A9wdEwcTs_OAA6vPFbjOZK)
- [YT comment](https://youtube.com/watch?v=onCHSujPlfg&lc=UgynYG7y8-tuIRYUXC14AaABAg.A9wr06kTXfJAA6x7KdfnLj)

If you've seen [discussions about the "JS0/JS-Sugar" proposal](https://caolan.uk/notes/2024-10-14_js0_jssugar.cm), you're probably going to disagree with the proposal itself, at least in one way or another.
But I'd like to point out that there really are some good intentions behind it.

> The road to hell is paved with good intentions

Yes, that's sometimes true, but hear me out for a second. I have another proposal that might be better, or worse, or just as bad. You'll be the judge.

## Body
IMO, **JS should be deprecated**, at least as a web-standard, not deprecated as a language spec (ECMAScript should live for a while).

Don't get me wrong, I feel "comfortable" writing JS, and I like the fact that having a browser installed implies access to a cross-platform general-purpose Turing-complete programming-lang (nice!).

But **Wasm has a textual representation**, and Python is much better suited as a cross-platform scripting/programming lang, so why are we forcing browsers to implement JS? Because of _"legacy"_.

But who cares about legacy if there will be old browser versions (both in binary and source form) available for download?. Additionally, anyone can implement a non-optimized JS engine, to avoid the maintenance burden of Chromium, WebKit, Blink, Gecko, SpiderMonkey, etc...

**Anyone who actually cares enough will eventually do that**, and if there's enough people they can create a "Legacy Browsing Foundation".

Please excuse my ignorance if what I'm saying is "bogus". But it's objectively true that web standards (such as HTML) have cruft that has been accumulating since the 90s. I respect the commitment to compatibility, but I'm afraid we have gone too far down this hole.

### Wasm
I've seen [people in the comments](https://youtu.be/onCHSujPlfg) saying stuff like "WebAssembly requires JS", "Wasm is slow when using the DOM API", etc...

They got it backwards: If Wasm got enough attention, eventually the standards-body and browser-vendors will make it **independent from JS**. Unfortunately, this is a catch-22 situation.

If it happens, it would be huge (hype alert?). Imagine a world where you could do
```html
<script type=wasm src=main.wasm>
</script>
```
Beautiful, isn't it?
- No more generated JS initialization code
- Direct DOM access and integration
- Better performance on ~all~ most tasks

But then again, HTML is meant to be a "human readable" text format, not a compact binary format, but that's a topic for another day.

## Outro
I hope all of this happens one day. In the meantime, I'm ok with JS runtimes (Node, Deno, Bun, etc...) existing, but eventually more servers should become native executables

See also:
- [The 30M line problem, by "Molly Rocket"](https://youtu.be/kZRE7HIO3vk)

