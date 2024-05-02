# [Re:](https://en.wikipedia.org/wiki/List_of_email_subject_abbreviations#Standard_prefixes) [The WWWorst App Store](https://www.gnu.org/philosophy/wwworst-app-store.html)
> Work In Progress, because I don't have time for this

## Prelude
Whenever you see quote-blocks, assume "[...]" is inserted before and after its contents. This is because most quotes will be reduced to their key substrings.

For further context about the quotes, read the GNU article linked in the heading

## Content
> run on your own computer

This seems like a contradiction to the following statements in that article, where they talk about server-side code taking control of users. Besides, shouldn't Unix/GNU utilities be able to run entirely locally? (unless the program fundamentally requires network connections, such as `wget`).

> be online to run them

From this point onwards (which is **very early** in the article) they start doing unfair generalizations. In this case, they didn't acknowledge that [PWAs](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps) can be installed for offline use.

I get that it's just rhetoric, but it seems somewhat fallacious to not even put a disclaimer at some point in the article.

> you start them, they contact the app store

It's totally reasonable for privacy-advocates to hate that! I agree.

> updated version

I disagree. I love when an app only gets updated if I actually use it, not regularly poll the server in the background.

Background updates are only private if the device is always connected to the internet, as the servers never get any useful data about the state of the device. But we all know this isn't going to be the case, as network connections can fail (trivial example: no signal).

BG updates do have some advantages, such as pre-downloading (and optionally pre-installing) the app in advance, which (occasionally) saves time for the user.

However, auto-updates of any kind (regular, irregular, poll, event-driven, etc..) can be inopportune, that's why I sometimes prefer to only update when I give explicit consent.

> no longer welcome
>
> [...]
>
> servers are offline

That's a valid point! But it mostly affects apps that "require" (or force users to require) internet connection. (See how they did another generalization?)

I absolutely despise apps that should work totally fine offline, but devs use crappy frameworks that make the server more indispensable than it should. I don't blame them (mostly), those FWs can be attractive, and sometimes they have no choice but to maintain a codebase that made poor design decisions.

Don't get me wrong, server-side rendering is fine, in **(actually) reasonable** situations.

> hold your data in the app store's servers

Ever heard of the [Storage API](https://developer.mozilla.org/en-US/docs/Web/API/Storage)? Cookies? (3 generalizations!)

I get the point. They're talking about those apps that require user-accounts for seemingly no reason. I hate when apps force me to register/login/sign-in just to do something trivial (looking at you: Samsung, Twitter and Pinterest). Corps come with the excuse "bot protection", but that's what CAPTCHAs are for!

> backups of your data, but you'd have to figure out how to decode

That's just a blatant fallacy, and the 4th generalization. That statement literally applies to **anything** that uses proprietary formats! One of the reasons why [this guy hates PSD](https://github.com/gco/xee/blob/4fa3a6d609dd72b8493e52a68f316f7a02903276/XeePhotoshopLoader.m#L108-L136)

> business-driven perversion

This seems like they're not generalizing, but I'm hesitating to give them the benefit of the doubt.

> encouraged to adopt “web apps”

It's actually the opposite! Most corps force us to install native apps, while neglecting (or even worsening) their web-clients. Besides, what's wrong about web-apps? They're "inherently" cross-platform.

> often distributed as JavaScript

At least they seem to acknowledge some apps are server-side-rendered HTML+CSS

> don't have control over what the program does

Ironically, JS is much more ductile than machine-code and byte-code. That's why [bookmarklets](https://en.wikipedia.org/wiki/Bookmarklet) and scriptlets are so easy to develop and inject, if compared to modding and disassembling of binaries.

Were they talking about server-side code?

> don't have control over when you can run it

Tangent-topic: it would be really nice if browsers could pause/resume JS/Wasm. Oh wait, they do! but it's "hidden" behind the debugger, which is unavailable for Android/iOS users (unless they do some inconvenient stuff).

As of now, the alternative is to reload the app everytime we [toggle scripting in uBO](https://github.com/gorhill/uBlock/wiki/Per-site-switches#no-scripting)

> don't have control over your own data

Again, that isn't specific to web apps. But I agree with the sentiment.

> lose when the JavaScript code is nonfree

Propaganda. And license is irrelevant.

> lose when it is (nominally) free software!

[Fallacy](https://techdirt.com/2012/12/20/stop-saying-if-youre-not-paying-youre-product)
