---
categories: development
date: '2018-10-23T12:00:00Z'
keywords: react-native react native web development web-development katex component display
tags: react-native web-development react
title: Displaying KaTeX in React Native
---
At Testive we are building a student native mobile app. Up until now we have relied on having a mobile friendly web-app, but since it’s been a hotly requested featuring we are currently working to build a version of our app using React Native.

The core features of the app will be the ability to answer practice questions/complete assignments, review incorrect answers, and schedule meetings with your coach. This means that a crucial feature will be the ability to display our question and answer texts.

Displaying questions requires that we not only parse our own markup language and inline HTML, but also KaTeX as that is how we display most math data in app. Parsing and displaying HTML/other Markup language, was not a particularly easy problem to solve, but after a lot of RegEx hacking I was able to parse the tags and create native components for them (a story for another blog post). Display KaTeX natively though, was not a wheel I wanted to reinvent.

My search for libraries and other solutions returned very few results, which is what I expected as parsing & displaying KaTeX in React Native is a pretty niche topic. Especially if you want a solution that works well with [Expo](https://expo.io/). The only thing close to a solution I found was a Github thread linking to [this](https://github.com/3axap4eHko/react-native-katex) library by [3axap4eHko](https://github.com/3axap4eHko) which pretty much exactly what I wanted except that it had build issues that the maintainer wasn’t responding to and that I couldn’t figure out how to fix.

So instead of rewriting something from scratch, or trying to write my own KaTeX parsing library, I decided to rebuild the library for my own purposes.

*Note: My solution here is not pretty, elegant, “correct”, or really all that good, but as there is not any other readily available solution to this problem, and I have already spent way too long trying to solve it, this is what I’m sticking with. I’m only sharing, so that some other poor soul doens’t have to spend hours digging around only to come to this same conclusion.*

## The Solution

So if you look at [3axap4eHko](https://github.com/3axap4eHko)’s solution, you’ll see they use a webview that loads the KaTeX javascript library & css, and then they feed the text they are parsing to that. This is essentially what we’ll be doing, only with a slightly different method. The crux of my solution, resolves around creating a wrapper for a webview. So let’s begin.

*(my full solution will be posted at the end of this)*

Start by creating a file that I named katex.js, that is going to house our KaTeX webview component. To start we’re going to layout a basic Component, with a webview that we’re dynamically gonna set the content of. It’s also going to include some other props that will make life easier down the road.

{% gist da788197a6489a65e43739ef554e6044 %}

As you can see, a lot of things will be defined later, but the basic idea is a webview, that we are creating content for on the fly, that accepts things like styles, and other KaTeX arguements that we might need to pass.

The crux of this is going to be defined in our getContent method, that looks like this:

{% gist e234afda977d8b567fe773ec2b7db619 %}

Originally, I tried self hosting the KaTeX JS files myself, but ran into issues trying to stringify them so they could be fed to our template literal. If you’re unfamiliar with template literals, you can read about them [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals). Basically they allow us to very easily feed javascript into our string. As I said it is not an elegant solution, and requires that our user be connected to the internet while using our app, but for our specific case it will work.

The last thing to do, is just to define our default styles, and wrap it all together which I’ll do by posting my complete definition and outlining some of the problems I’m still facing with it. Enjoy.

### katex.js

{% gist bccd1d252b82f6f03f736de491cebf27 %}

The biggest issue you’ll find, is formatting the webviews. I have hacked in a width value there, that I’m constantly tweaking and haven’t found a good solution for yet. If you find a way to have our View container’s width work well with a dynamically sized webview/katex expression please let me know in the comments. The error handling on this is also not amazing.

Anyway, I had a ton of trouble with this so I wanted to make this post so that it might be easier for someone else to land at this same solution, or figure out that there isn’t a really elegant solution to this problem right now. Please let me know any suggestions you have for this code.

Thanks for reading.
