---
title: "Thoughts on Deno"
date: 2024-11-13T20:22:00+02:00
draft: false
tags:
  ["typescript", "deno", "deno deploy"]
---

I originally asked chatGPT to write this article. Just to test chatGPT out.
I forgot to mention that I wrote it with chatGPT and it was absolutely an
embarrasing piece of writing. It looked like a machine wrote it.

The topic of article is still very interesting. Now maybe more than ever.
Because Deno 2.0 has been released. JSR exists. After about two years (?)
of using Deno what can I say about it that hasn't been said. Nothing.
But I want to give my input.

Compared to Node.js. The runtime is simply better. It can run TypeScript
natively, without `tsc` and `tsconfig.json`. It has top-level `async-await`.
No more need for awkwardly doing this:
```javascript
(async ()=>{
  await myFunc()
})()
```

One of the big arguments against Node.js ecosystem is that the scripts
have access to EVERYTHING. The runtime does nothing to keep you safe.
With Deno you have to explicitly allow the script to access the filesystem
or the network or your environmental variables. But if you are running
a script you wrote yourself (or which you know is a hundred percent safe
you can just run `deno run -A script.ts`

Deno makes web development fun again. With their official framework `Deno Fresh`.
Deno Fresh is just a fancy way to say `Preact + Server Side Rendering & functions +Islands (as seen on Astro)`.
Why should we care? Because it is Preact, it is small while giving you a good
developer experience and supporting all modern browsers. Server side rendering
makes SEO easier and makes you ship a website instead of a webapp. You might think
this is the old and slow way to do things. Deno is so fast. The websites seem blazing
fast. Going from page to page still loads the page with the blink of an eye.
Server side functions make it so that you can connect to a private api without creating
some hodge-podge public API to accomodate (aka backend for frontend).
If you need interactive javascript, we have you covered. They're called islands.

Deno now has good native API, it has npm compatibility, but also a thriving package repository (JSR).
It lets you run TypeScript without transpiling to js with `tsc`.

Deno is what Node should have been. Deno is created by Ryan Dahl. Node was created by Ryan Dahl.

Thanks, Ryan.
