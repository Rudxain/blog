# JavaScript abuse

> [!note]
> This blog-post is WIP/unfinished.

I'm not here to tell you "JS bad", because many people have already done that:
- [`/denysdovhan/WTFJS/`](https://github.com/denysdovhan/wtfjs)
- [`/brianleroux/WTFJS/`](https://github.com/brianleroux/wtfjs)
- [YLS](https://wiki.theory.org/YourLanguageSucks#JavaScript_sucks_because)

I'm writing this for other reasons:
- spreading awareness of the crap that `noscript` users have to deal with, and how this effects "[normies](https://en.wiktionary.org/wiki/normie)" as well
- venting, because I'm **fucking sick of this shit**
- propose alternatives, for people with _good intentions™_
- shame and mock entities that are incompetent, don't care, or willfully do this shit
- a cry for help, coming from a developer who was forced to deal with piles of abstractions (React + Redux + MaterialUI + ReactRouter = **NIGHTMARE**)
- the accessibility challenges of dynamic content
- how this connects to [enshittification](https://consumerrights.wiki/w/Enshittification) and [bloat](https://consumerrights.wiki/w/Bloatware)

Keep in mind, **I ain't a luddite**. And I don't hate JS in particular. I love when JS is used right! such as:
- [Demoscene](https://github.com/Rudxain/RGB-digital-rain)
- [Competitive stuff](https://gist.github.com/Rudxain/c06a6800807233fe6e74f179dda750a8)
- Make [an abomination](https://github.com/Rudxain/ideas/blob/aa9a80252a4b7c9c51f32eda5c716e96220ed96e/software/evar/with_bf.js) for fun, and to [prove a point](https://github.com/Rudxain/ideas/blob/aa9a80252a4b7c9c51f32eda5c716e96220ed96e/software/evar/README.md#why)!
- Even [coding as a form of art](https://gist.github.com/Rudxain/f4d2dd9b1c3e44a2eb4fb46ddf2a76f6#file-minimum-bit-length-js-L58-L77) ✨

Notice how the "competitive" one abuses ES/JS behavior to optimize the size of the program. That's called _code-golfing_, and it's totally acceptable to break best-practices to reach your goal, simply because the result pushes the boundaries of what was believed to be possible, and that's _cool_, not _disgusting_.

## Sources
- [LibRedirect explaining why it exists, and how MV3 limits it](https://libredirect.github.io/faq.html)
- [gluegle has beef with Firefox users](https://github.com/uBlockOrigin/uBlock-issues/discussions/3240)
- ["meta" inc, spitting in your face](https://github.com/Rudxain/uBO-rules/pull/9)
- [`noscript` treated like 2nd-class citizen](https://github.com/Rudxain/uBO-rules/blob/42220bd4f80052ee15136dff7269df19529c43ec/rx.abp#L69-L76)
- [websites being obnoxious to `noscript` users](https://github.com/iam-py-test/my_filters_001/blob/fc5f61eff0b0d821cb426bea76b18937072bc390/no-js-warnings.txt)
- [disbloat](https://github.com/Rudxain/uBO-rules/blob/42220bd4f80052ee15136dff7269df19529c43ec/rx.ubo#L3-L19)
- ["Enough with the JavaScript already!"](https://www.slideshare.net/slideshow/enough-withthejavascriptalready/23262138)
- ["Maybe we could tone down the JavaScript"](https://eev.ee/blog/2016/03/06/maybe-we-could-tone-down-the-javascript)
- ["You don't need JavaScript for that"](https://www.htmhell.dev/adventcalendar/2023/2/)
- ["You really don't need all that JavaScript, I promise"](https://www.kryogenix.org/code/dont-need-that-js)
- https://jakearchibald.com/2013/progressive-enhancement-still-important
- [Unobtrusive JS](https://www.w3.org/wiki/The_principles_of_unobtrusive_JavaScript)
- ["Everyone has JS, right?"](https://www.kryogenix.org/code/browser/everyonehasjs.html)
- [The humble "grug-brain" developer](https://grugbrain.dev) (this is for the "cry for help" part)
- [Web Obesity Crisis](https://idlewords.com/talks/website_obesity.htm)
- [JS bloat (2024)](https://tonsky.me/blog/js-bloat)
- [Software disenchantment](https://tonsky.me/blog/disenchantment)
- https://www.gnu.org/philosophy/javascript-trap.html
- https://www.gnu.org/philosophy/wwworst-app-store.html : [I don't agree with this](re_twwwas.md), but I love the ending!
> if you wish your site to give its users a taste of how the WWWorst app store feels to us, add to web pages you control the following JavaScriptlet:
> ```js
> document.body.textContent = 'Please disable JavaScript to view this site.'
> ```
- [🖱️Click ×4](https://clickclickclick.click): this is about tracking/privacy-invasion

## to-do
[These exception-filters](https://github.com/uBlockOrigin/uAssets/blob/30c5cbc78a4625ab02a1a1a52d898102da7eb58a/filters/filters-2021.txt#L4128-L4132) prove that enshittification effects everyone. I had to rewrite [one of my filters](https://github.com/Rudxain/uBO-rules/blob/42220bd4f80052ee15136dff7269df19529c43ec/rx.abp#L112) because I never allow JS on windowscentral, so I never need to prevent uBO from being detected. The uBO team is forced to design filters for the lowest-common-denominator, leading to sad stuff like that.

If you visit any [Discourse](https://discourse.org) forum, you'll notice they have [graceful degradation (not PE)](https://www.w3.org/wiki/Graceful_degradation_versus_progressive_enhancement). However, if you visit it using a phone, you'll be greeted by this ✨ _wonderful_ ✨ message:

> "HTML content omitted because you are logged in or using a modern mobile device"

```rust
for _ in 0..=u16::MAX {
	println!("WHY?");
}
```

I'll ~steal~ borrow [a quote](https://blog.vaxry.net/articles/2025-dbusSucks):
> Honestly, I am at a loss of words as to how to describe this without being extremely rude.

## Unreliable color-scheme
We need to talk about dark and light modes. Yes, this is **so bad that it needs its own section**.

Let me preface by asserting that your page **only needs [1 line of HTML](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/meta/name/color-scheme)** to support both preferences:
```html
<meta name=color-scheme content="light dark">
```
That's it! Just add that inside the `<head>` and your pages now can **automatically** ("dynamic" if you will) switch between both themes in *real-time*, adapting to user preference!

This is not new, it has existed for many years. No need to worry about "compatibility"!

I can already hear you complaining:
> But the default browser stylesheet is ugly!

or:
> But I **NEED** my pages to look the same in all browsers!

or:
> But I have a _Brand™!_ I have my own stylesheets to theme my site!

Fine, [here you go](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-color-scheme):
```css
/* default light */
html {
	background: #ccc;
	color: #111;
	/* etc... */
}
/* conditional override */
@media (prefers-color-scheme: dark) {
	html {
		background: #111;
		color: #ccc;
	}
	/* etc... */
}
```
No excuses!

> But I **NEED** it to be configurable!

...why would you want that? It already is?

> No! We want an obvious UI that allows users to choose a theme that doesn't match the browser!

Again, _why_ would you want that? Are your users complaining about "lack of choice"?

> No...?

Then shut up.

> But-

**OK FINE!!!** If you insist, just use a [`<form>` element](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/form) to take input and send it to the server, then the server response should [set a cookie](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Cookies) on the client, to remember the preference. Are you happy now?

> but-

Now that the preface is done, [let me tell you how much I despise](https://youtu.be/EddX9hnhDS4) youtube!

### youtube
YT theme requires JS to detect preference:

This is bad, but it's "forgivable" since YT needs JS for many things. However, it's worth noting that **YT remembers the last preference**. I know because the server returns a page colored like my last visit. This is better than other sites, which fallback to a hard-coded stylesheet (_\[cough\]_ disbloat _\[cough]_)

YT theme **needs a full-page reload** to apply...

wait, **WHAT?!**

![](https://deltarune.wiki/images/Noelle_overworld_Berdly_shake.gif?cb=b5hyde&h=thumb.php&f=Noelle_overworld_Berdly_shake.gif)

what 👏 is 👏 the 👏 point 👏 of 👏 a 👏 "dynamic" 👏 language? 👏

seriously, **WHAT IS THE DAMN FUCKING POINT OF JS IF YOU NEED TO RELOAD ANYWAYS‽‽‽**

**WHAT HAPPENED TO** _"[single-page application](https://en.wikipedia.org/wiki/Single-page_application)™"_**‽‽‽**

**AND THEY HAVEN'T FIXED THIS FOR YEARS!!!**

And you know what's worse? That "Device theme" option (the one that "adapts" to your preference) **requires you to manually reload the damn page** just so that YT notices the change.

Have they heard of [`matchMedia`](https://developer.mozilla.org/en-US/docs/Web/API/Window/matchMedia)?:
```js
const light_query = matchMedia("(prefers-color-scheme: light)");
// sync
let is_light = light_query.matches;
// async
light_query.addEventListener("change", (e) => {
	is_light = e.matches;
});
```

What kind of incompetence YT has??? No sane human should think that is "acceptable"!

But nooo, [they're too busy fighting ad-blockers](https://consumerrights.wiki/index.php?title=YouTube&oldid=31465#Crackdown_against_ad-blockers), so they end up being ["resource constrained"](https://idlewords.com/talks/website_obesity.htm#:~:text=Google%20was%20%22resource%20constrained%22) to actually improve [UX](https://en.wikipedia.org/wiki/User_experience)

Let's take a moment of silence to pray for our beloved YT...

After a word from our sponsor! **RAID SHA-** 🔫💥

### Wikipedia
I respect WP, [I even like it](https://en.wikipedia.org/wiki/User:Rudxain), but I'm sorry, nobody can convince me that WP is "struggling" to implement auto-color-scheme for more than 6 years, that's plain bullshit.

The [CRW](https://consumerrights.wiki/) is powered by MediaWiki as well, and its theme is **fully adaptive** without JS. So why does WP still consider "Auto" an "experimental feature"? and why does it require JS?

WP has **much** more money and contributors/volunteers than CRW, and they still fail to provide such a simple feature?

I'm sorry, again, if anyone gets offended, but this implies that WP doesn't care about its users. And if they do care, they're lazy and incompetent. There is no other explanation.

### Me?
Roasting others is unfair, so here I'll roast myself, for the sake of "redemption".

If you've visited my GH-Pages site, you'll quickly notice that I'm a hypocrite! All of my pages (except for RGB-DR) are either `light` or `dark`, even with JS enabled.

I'd like to [blame Jekyll themes](https://github.com/Rudxain/Rudxain.github.io/issues/9) for this, but this is my mistake, and I have to deal with it.

Don't worry, [I'm working on fixing it](https://github.com/Rudxain/Rudxain.github.io/pull/15)!

## Not all is bad
I don't want you, dear reader, to feel like a [doomer](https://www.urbandictionary.com/define.php?term=doomer)/[gloomer](https://www.urbandictionary.com/define.php?term=gloomer) after reading this. So here are some good news to give you hope!

- There's [many people in favor of simpler web development](https://github.com/lyoshenka/awesome-motherfucking-website)!
- There's [a big community pushing back against sloppy and/or corporate software](https://handmade.network/manifesto)!
- Someone made [this parody (not satire) site](http://vanilla-js.com), lol
- People do amazing things with only HTML and CSS:
	- [vereis theme](https://github.com/vereis/blog/issues/2)
	- [YDNJS](https://github.com/you-dont-need/You-Dont-Need-JavaScript)
	- [1HTML challenge](https://github.com/Metroxe/one-html-page-challenge)
	- [CSS Zen Garden](https://csszengarden.com)
- SoundCloud (yes, [that one](https://consumerrights.wiki/w/SoundCloud)!): A few weeks ago, their pages now show _more_ content than before! (in `noscript`). Previously, it was just a generic page telling you to enable JS. I wish I could say they care about `noscript` users, but they don't care about their users in general. I guess they're experimenting with [SSR](https://en.wikipedia.org/wiki/Server-side_rendering) or [pre-rendering](https://vite.dev/guide/ssr#pre-rendering-ssg)
- [Deno making dark-mode work in `noscript`](https://github.com/denoland/docs/pull/2709)
- [ESlint team concerned about accessibility and productivity](https://github.com/eslint/eslint/issues/20279)
