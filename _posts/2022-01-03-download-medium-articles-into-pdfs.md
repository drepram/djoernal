---
layout: post
title: "Download Medium Article(s) into PDFs"
tags: software
image:
    src: "assets/posts/2022/medium-pdf/cover.png"
    alt: "One output file from the tools discussed in this post regarding medium content retrieval into local disk"
---

To save time for the reader:

1. My task was to download articles from medium into PDFs
1. My solution was to use [percollate](https://github.com/danburzo/percollate) and [scribe](https://scribe.rip/)

> How-To
> To view a Medium post simply replace medium.com with scribe.rip
> 
> If the URL is: medium.com/@user/my-post-09a6af907a2 change it to scribe.rip/@user/my-post-09a6af907a2

Assuming you would want to download 2 PDFs, this is the command you could use:

- Given the two URLs ([https://scribe.rip/@astro-hmdfui/inpherence-3-the-little-useful-device-gyroscope-d1fedd4e17e](https://scribe.rip/@astro-hmdfui/inpherence-3-the-little-useful-device-gyroscope-d1fedd4e17e), and [https://scribe.rip/@astro-hmdfui/photrait-4-marie-curie-4883c40e9f09](https://scribe.rip/@astro-hmdfui/photrait-4-marie-curie-4883c40e9f09]))
- Because more than two articles are wanted, we use the `--individual` flag so that `percollate`'s output is not combined into 1 single file.

**The command that would work for us**:

```
percollate pdf --individual https://scribe.rip/@astro-hmdfui/inpherence-3-the-little-useful-device-gyroscope-d1fedd4e17e https://scribe.rip/@astro-hmdfui/photrait-4-marie-curie-4883c40e9f09
```

<br>

The `percollate` command format that we have written above follows the following format: `percollate pdf --individual http://example.com/page1 http://example.com/page2`. If it is only 1 article, omit the  `--individual` flag.

---

Moving on, here is the article:

What I used for this task:

- https://github.com/danburzo/percollate + https://scribe.rip/

Repositories that I tried and **didn't work** for me:

- https://github.com/sparkingdark/medium-article-pdf-converter
- https://github.com/gunar/medium-converter
- https://github.com/DanielArthurUK/medium-downloader
- https://github.com/hussaino/medium-to-pdf

---

Scribe.rip claims to be an alternative frontend to Medium. In my experience, it's alike to Telegram's _Instant View_ function though there are certain articles that are limited by paywalls (Some articles from Douglas Rushkoff, Jeff Jarvis, etc.) that Scribe can break through while Telegram can not.

I was tasked with converting articles that have been posted to my student society's work unit medium publication in the past, into PDFs. During the few first hours I tried Chromium and the other shenanigans that were offered by the repositories I listed above but all of them ended up not working, one in [particular](https://github.com/hussaino/medium-to-pdf) was really pushing my buttons because it uses Chromium to access Medium's reading list; but you can't log into Medium with a Google account because the client (Chromium) is not trusted. 

The solution to this was to try to sign in with an email from another browser, from which it will send a login link to your email:

<img src="assets/posts/2022/medium-pdf/image1.png" />


I tried to hack the code by inserting the login code given into the email:

<img src="assets/posts/2022/medium-pdf/image2.png" />

But it still wouldn't work because of the div on line 115 (shown below) being undefined:

<img src="assets/posts/2022/medium-pdf/image3.png" />

Anyways, I spent some time away from the code because an ordered food arrived and I ate crispy deep grilled mushrooms with plain white rice, it wasn't the most pleasant meal to have for a night but I wasn't having the best time with code either lol. I watched some film recaps and finished my food, and this is where I start to crawl to the solution.

Around 30 minutes before the food arrived, I was refilling my water bottle(s) and as I was doing that, a friend of mine sent me an article on Telegram. I was on my phone and I clicked on it via the _Instant View_ feature but it didn't quite worked, paywalled. I then try to recall the name of a site that could work for this kind of situation, and then remembered it was [https://scribe.rip], I tried that on my phone and it worked, but I put no thought into it till I finished my meal.

As it occurred to me, maybe I don't have to be limited by Medium's weird UI. I went onto [https://scribe.rip] with the articles I needed to download but... it wasn't exactly the best view you've seen in this millennium:

<img src="assets/posts/2022/medium-pdf/image4.png" />

And so, with some time searching on GitHub (`web to pdf`) I stumble across [https://github.com/danburzo/percollate]. As I've written above, the solution for me was simple:

```
percollate pdf --individual https://scribe.rip/@astro-hmdfui/inpherence-3-the-little-useful-device-gyroscope-d1fedd4e17e https://scribe.rip/@astro-hmdfui/photrait-4-marie-curie-4883c40e9f09 https://scribe.rip/@astro-hmdfui/photrait-james-prescott-joule-85ea63624a33 https://scribe.rip/@astro-hmdfui/inpherence-sejarah-elektronika-semikonduktor-dan-transistor-7cb978ca5298 https://scribe.rip/@astro-hmdfui/albert-abraham-michelson-4bcf20bf6969 https://scribe.rip/@astro-hmdfui/inpherence-2-mengapa-langit-memiliki-warna-dan-berwarna-biru-pada-siang-hari-1a6c80b583ba https://scribe.rip/@astro-hmdfui/photrait-3-jonas-ferdinand-gabriel-lippmann-836fa79b8d76 
```

After running the command above, it didn't take long for these 7 articles to be downloaded into my machine (after the downloaded, I split the files). One of the articles look like this:

<img src="assets/posts/2022/medium-pdf/image5.png" />

<img src="assets/posts/2022/medium-pdf/image6.png" />

<img src="assets/posts/2022/medium-pdf/image7.png" />

I am completely satisfied with how this turned out, though it took me about 2 hours to come to this solution of my task (`downloading medium articles into pdf`), that is why I decided to write this up in the hopes that it will someone else get to the solution faster without being bombarded by repositories that isn't necessarily helpful for this specific task at hand.