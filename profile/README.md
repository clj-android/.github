# Clojure on Android

This is a modernization of the [clojure-android](https://github.com/clojure-android/) project. It lets you build Android apps in Clojure as the name suggests, provides ergonomic wrappers for some of the Android Java APIs, and it gives you an nREPL connection to your running app over ADB.

It builds with Gradle and should work for F-Droid. It can build release without dynamic class loading (optionally), which makes Google Play approval easier. 

## Keep Android Open

Google plans to prevent most Android users from installing apps unless the developer registers with Google, giving Google the power to ban developers and apps it doesn't like. See https://keepandroidopen.org/ for what you can do about it.

## Getting started

Clone the [sample app](https://github.com/clj-android/sample) and follow the build instructions in its README. It's a template repository and CC0 license, so you are encouraged to use it as a starting point for your own apps.

## Maturity

This is not very mature at this point. A lot of the code was written by a robot; it's [plausible, but not necessarily correct](https://blog.katanaquant.com/p/your-llm-doesnt-write-correct-code), and it works on my machine (tm).

I've used this to build [Ceilingbounce](https://github.com/zakwilson/ceilingbounce), a datalogging app for flashlight reviewers. It's hand written so I've had some opportunity to get a feel for pain points and fix them.

Please try this for your hobby project. Your investors would like me to say please don't bet your company on it.

## Docs

See the [docs](https://github.com/clj-android/docs) repo for mostly machine-generated documentation.

## Anticipated Frequent Questions (it's too early to have FAQ)

### What's with the Java activity shims?

They make the use of a dynamic classloader optional. If you follow the pattern of subclassing ClojureActivity, you don't really have to write any Java.

### How do I...?

The source code of the sample app is designed to serve as part of the documentation. It's also helpful to use `neko.doc/describe` from the REPL.

### Why doesn't Neko use Jetpack Compose?

It requires Kotlin-specific features that aren't straightforward to call via Java interop.

### Native Clojure apps used to be really slow to launch on Android. Is it better now?

Yes. Your phone is probably a lot faster now. Apps compiled with the current toolchain also launch much faster on the same hardware.

### I hate AI and this is dumb

#### slop, videcoding, boiling oceans, etc...

I share your concerns, but I also know that it's perilous to ignore major technological shifts. I wanted to see what LLM coding tools can do, and this seemed like a good project for it since there was an existing implementation to work from and a well-defined success condition.

I wouldn't have done this if I had to do it all by hand, and neither did anybody else in the nine years clojure-android has been unusable.

Now I get to hand-code Clojure for my phone with all the joy inherent in that experience. You can too if you like.

### I love AI and this is dumb

#### LLMs don't care what language they're using, just use Kotlin or TypeScript, and don't waste time hand-coding anything

I **like** hand-coding in nice environments, and I'm not convinced human developers are as obsolete as the AI maximalists would like the world to believe. See the link about plausible code above.

I also think this is a good environment for LLM tools for two reasons. One is that they can use the Clojure REPL via MCP or command-line tools. LLMs make a lot of mistakes, so they're faster and more accurate given a tight feedback loop. The other is that a language which enables more succinct code uses fewer tokens. That makes it cheaper, but more importantly, LLMs consistently produce more correct results when the context is smaller.
