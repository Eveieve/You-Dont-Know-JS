# You Don't Know JS Yet: Getting Started - 2nd Edition
# Chapter 1: Getting To Know JavaScript

| NOTE: |
| :--- |
| Work in progress |

You don't know JS, yet. Neither do I, not fully anyway. None of us do. That's the whole point of this book series!

But here's where you start that *journey* of getting to know the language a little better. I emphasize the word journey because *knowing JS* is not a destination, it's a direction. No matter how much time you spend with the language, you will always be able to find something else to learn and understand a little better.

In this chapter we'll take care of some background and housekeeping details, and then in the next chapter we'll move into talking about the code parts of the language.

## Name

The name JavaScript is probably the most misunderstood programming language name ever.

Is this language related to Java? Is it only the script form for Java? Is it only for writing scripts and not real programs?

The truth is, the name JavaScript is an artifact of marketing shenanigans. When Brendan Eich first conceived of the language, he code named it Mocha. Internally at Netscape, the brand LiveScript was used. But when it came time to publicly name the language, "JavaScript" won the vote.

Why? Because this language was originally designed to appeal to an audience of mostly Java programmers, and because the word "script" was popular at the time to refer to lightweight programs. These lightweight "scripts" would be the first ones to embed inside of pages on this new thing called the web!

In other words, JavaScript was a marketing ploy to try to position this language as a palatable alternative to writing the heavier and more well-known Java of the day. It could just as easily have been called "WebJava", for that matter.

There are some superficial resemblances between JavaScript's code and Java code. But those are actually mostly from a common root: C (and to an extent, C++).

For example, we use the `{` to begin a block of code and the `}` to end that block of code, just like C/C++ and Java. We also use the `;` to punctuate the end of a statment.

In fact, the relationships run even deeper than the superficial. Oracle (via Sun), the company that still owns and runs Java, also owns the official trademark for the name "JavaScript" (via Netscape). This trademark is almost never enforced, and likely couldn't be at this point.

Some have suggested we use JS instead of JavaScript. That is a very common shorthand, if not a good candidate for an official language branding itself.

To distance the language from the Oracle-owned trademark, the official name of the language specified by TC39 and formalized by the ECMA standards body is: ECMAScript. And indeed, since 2016, the official language name has also been suffixed by the revision year; as of this writing, that's ECMAScript 2019, or otherwise abbreviated ES2019.

In other words, JavaScript (in your browser, or in Node.js) is *an* implementation of the ES2019 standard.

| NOTE: |
| :--- |
| Don't use terms like "JS6" or "ES8" to refer to the language. Some do, but those terms only serve to perpetuate confusion. "ES20xx" or just "JS" are what you should stick to. |

Whether you call it JavaScript, JS, ECMAScript, or ES2019, it's most definitely not a variant of the Java language!

> "Java is to JavaScript as ham is to hamster." --Jeremey Keith, 2009

## Specification

I mentioned a moment ago that TC39 -- the technical steering committee that manages JS -- votes on changes to submit to ECMA, the standards body.

The set of syntax and behavior that *is* JavaScript is this ES specification.

ES2019 happens to be the 10th numbered specification/revision since JavaScript's inception, so in the specification's official URL as hosted by ECMA, you'll find "10.0":

https://www.ecma-international.org/ecma-262/10.0/

The TC39 committee is comprised of between 50 and about 100 different people from a broad section of web-invested companies, such as browser makers (Mozilla, Google, Apple) and device makers (Samsung, etc). All members of the committee are volunteers, though many of them are employees of these companies and so may receive compensation in part for their duties on the committee.

TC39 meets generally about every other month, usually for about 3 days, to review work done by members since the last meeting, discuss issues, and vote on proposals. Meeting locations rotate among member companies willing to host.

All TC39 proposals progress through a five stage process -- of course, since we're programmers, it's 0-based! -- Stage 0 through Stage 4. You can read more about the Stage process here: https://tc39.es/process-document/

Stage 0 means roughly, someone on TC39 thinks it's a worthy idea and plans to champion and work on it. That means lots of ideas that non-TC39 members "propose", through informal means such as social media or blog posts, are really "pre-stage 0". You have to get a TC39 member to champion a proposal for it to be considered "Stage 0" officially.

Once a proposal reaches "Stage 4" status, it is eligible to be included in the next yearly revision of the language. It can take anywhere from several months to a few years for a proposal to work its way through these stages.

All proposals are managed in the open, on TC39's Github repository: https://github.com/tc39/proposals

Anyone, whether on TC39 or not, is welcome to participate in these public discussions and the processes for working on the proposals. However, only TC39 members can attend meetings and vote on the proposals and changes. So in effect, the voice of a TC39 member carries a lot of weight in where JS will go.

Contrary to some established and frustratingly perpetuated myth, there are *not* multiple versions of JavaScript in the wild. There's just **one JS**, the official standard as maintained by TC39 and ECMA.

Back in the early 2000's, when Microsoft maintained a forked and reverse-engineered (and not entirely compatible) version of JS called "JScript", there were legitimately "multiple versions" of JS. But those days are long gone. It's outdated and inaccurate to make such claims about JS today.

All major browsers and device makers have committed to keeping their JS implementations compliant with this one central specification. Of course, engines implement features at different times. But it should never be the case that the v8 engine (Chrome's JS engine) implements a specified feature differently or incompatibly as compared to the SpiderMonkey engine (Mozilla's JS engine).

That means you can learn **one JS**, and rely on that same JS everywhere.

## Backwards and Forwards

One of the most foundational principles that guides JavaScript is preservation of *backwards compatibility*. Many are confused by the implications of this term, and often confuse it with a related by different term: *forwards compatibility*.

Let's set the record straight. Backwards compatibility means that once something is accepted as valid JS, there will not be a future change to the language that causes that code to become invalid JS. Code written in 1995 -- however primitive or limited it may have been! -- should still work today. As TC39 members often proclaim, "we don't break the web!"

The idea is that JS developers can write code with confidence that their code won't stop working unpredictably because a browser update is released. This makes the decision to choose JS for a program a more wise and safe investment, for years into the future.

That "guarantee" is no small thing. Maintaining backwards compatibility, stretched out across almost 25 years of the language's history, creates an enormous burden and a whole slew of unique challenges. You'd be hard pressed to find any other example in all of computing of such a committment to backwards compatibility.

The costs of sticking to this principle should not be casually dismissed. It necessarily creates a very high bar to including changing or extending the language; any decision becomes effectively permanent, mistakes and all. Once it's in JS, it can't be taken out because it might break programs, even if we'd really, really like to remove it!

There are some small exceptions to this rule. JS has made backwards-incompatible changes, but TC39 is extremely cautious in doing so. They study existing code on the web (via browser data gathering) to estimate the impact of such breakage, and browsers ultimately decide and vote on whether they're willing to take the heat from users for a very small scale breakage weighed against the benefits of fixing or improving some aspect of the language for many more sites (and users).

These kinds of changes are rare, and are almost always in corner cases of usage that are unlikely to be observably breaking in many sites.

Compare *backwards compatibility* to its counterpart, *forwards compatibility*. Being forwards-compatible means that including a new addition to the language in a program would not cause that program to break if it were run in an older JS engine. **JS is not forwards-compatible**, despite many wishing such, and even incorrectly believing the myth that it is.

HTML and CSS are, by contrast, forwards-compatible, but are not backwards-compatible. If you found some HTML or CSS from 1995, it's entirely possible it would not work (or work the same) today. But, if you use a new CSS feature from 2019 and it runs in a CSS engine from 2010, the CSS does not break; the style engine merely skips over anything it does not recognize.

### Jumping The Gap

Since JS is not forwards-compatible, it means that there is always the potential for a gap between code that you can write that's valid JS, and the oldest engine that your site or application needs to support. If you run a program that uses an ES2019 feature in an engine from 2016, you're very likely to see the program break and crash.

If the feature is a new syntax, the program will in general completely fail to compile and run, generally throwing a syntax error. If the feature is an API (such as ES6's `Object.is(..)`), the program may run up to a point but then throw a runtime exception and stop once it encounters the reference to the unknown API.

Does this mean JS developers should always lag behind the pace of progress, using only code which is on the trailing edge of the oldest JS engine environments they need to support? No!

But it does mean that JS developers need to take special care to address this gap.

For new and incompatible syntax, the solution is transpiling. Transpiling is a contrived and community-invented term to describe using a tool to convert the source code of a program from one form to another (but still as textual source code). Typically, forwards-compatibility problems related to syntax are solved by using a transpiler -- the most common one being Babel (https://babeljs.io) -- to convert from that newer JS syntax version to an equivalent of code that uses an older syntax.

For example, a developer may write a snippet of code like:

```js
if (something) {
	let x = 3;
	console.log(x);
}
else {
	let x = 4;
	console.log(x);
}
```

This is how the code would look in the source code tree for that application. But when producing the file(s) to deploy to the public website, the Babel transpiler might convert that code to look like this:

```js
var x$0;
var x$1;
if (something) {
	x$1 = 3;
	console.log(x$1);
}
else {
	x$2 = 4;
	console.log(x$2);
}
```

The original snippet relied on `let` to create block-scoped `x` variables in both the `if` and `else` clauses which did not interfere with each other. An equivalent program (with minimal re-working) that Babel can produce just chooses to name two different variables with unique names, producing the same non-interference outcome.

| NOTE: |
| :--- |
| The `let` keyword was added in ES6 (in 2015). The above example of transpiling would only need to apply if an application needed to run in an pre-ES6 supporting JS environment. The example here is just for simplicity of illustration. When ES6 was new, the need for such a transpilation was quite prevalent, but in 2019 it's much less common to need to support pre-ES6 environments. The "target" used for transpiliation is thus a sliding window that shifts upward only as decisions are made for a site/application to stop supporting some old browser/engine. |

You may wonder: why go to the trouble of using a tool to convert from a newer syntax version to an older one? Couldn't we just write the two variables and skip using the `let` keyword? The reason is, it's strongly recommended that developers use the latest version of JS so that their code is clean and communicates its ideas most effectively. Developers focus on writing the clean, new syntax forms, and let the tools take care of producing a forwards-compatible versions of that code that is suitable to deploy and run on the oldest supported JS engine environments.

### Filling The Gap

If the forwards-compatibility issue is not related to new syntax, but rather to a missing API method that was only recently added, the most common solution is to provide a definition for that missing API method that stands in and acts as if the older environment had already had it natively defined. This pattern is called a polyfill (aka "shim").

Consider this code:

```js
// getSomeRecords() returns us a promise for some
// data it will fetch
var pr = getSomeRecords();

// show the UI spinner while we get the data
startSpinner();

pr
.then(renderRecords)   // render if successful
.catch(showError)      // show an error if not
.finally(hideSpinner)  // always hide the spinner
```

This code uses an ES2019 feature, the `finally(..)` method on the promise prototype. If this code were used in a pre-ES2019 environment, the `finally(..)` method would not exist, and an error would occur.

A basic polyfill for `finally(..)` in pre-ES2019 environments could look like this:

```js
if (!Promise.prototype.finally) {
	Promise.prototype.finally = function f(fn){
		return this.then(fn,fn);
	};
}
```

| NOTE: |
| :--- |
| This is only a simple illustration of a naive polyfill for `finally(..)`. Don't use this approach in your code; always use a robust, official polyfill wherever possible, such as the collection of polyfills/shims in ES-Shim. |

The `if` statement protects the polyfill definition by preventing it from running in any environment where the JS engine has already defined that method. In older environments, the polyfill is defined, but in newer environments the `if` statement is quietly skipped.

Transpilers like Babel typically detect which polyfills your code needs and provide them automatically for you. But occassionally you may need to include/define them explicitly, which works similar to the above snippet.

Always write code using the most appropriate features to communicate its ideas and intent effectively. In general, this means using the most recent stable JS version. Avoid negatively impacting the code's readability by trying to manually adjust for the syntax/API gaps. That's what tools are for!

Transpilation and polyfilling are two highly effective techniques for addressing that gap between code that uses the latest stable features in the language and the old environments a site or application needs to still support. Since JS isn't going to stop improving, the gap will never go away. Both techniques should be embraced as a standard part of every JS project's production chain going forward.

## Interpretation or Compilation

A long-debated question for code written in JS: is it an interpreted script or a compiled program?

The majority opinion seems to be that JS is an interpreted (scripting) language. But the truth is more complicated than that.

Let's consider the question in more detail.

First, why do people even debate or care about this? Why does it matter?

For much of the history of programming languages, "interpreted" languages and "scripting" languages have been looked down as inferior compared to their compiled counterparts. The reasons for this acrimony are numerous, including a perception of lack of performance optimization, as well as dislike of certain language characteristics, such as scripting languages generally using dynamic typing instead of the "more mature" statically typed languages.

Languages typically considered in the "compiled" category usually produce a portable (binary) representation of the program that is distributed for execute later. Since we don't really see that same model with JS -- we distribute the source code, not the binary form -- many claim that disqualifies JS from the category. In reality, the distribution model for a program's "executable" form has become drastically more varied and equally less relevant over the last few decades; to the question at hand, it doesn't really matter so much anymore what form of a program gets passed around.

These misinformed claims and criticisms should be set aside. The real reason it matters to have a clear picture on whether JS is interpreted or compiled relates to the nature of how errors are handled.

Historically, scripted or interpreted languages were executed in generally a top-down and line-by-line fashion; there's typically not an initial pass through the program to process it before execution begins. In those languages, an error on line 5 is not discovered until lines 1 through 4 have already executed. Notably, that error on line 5 might be due to a runtime condition, such as some variable or value having an unsuitable value for an operation, or it may be due to a malformed statement/command on that line. Depending on context, deferring error handling to the line the error occurs on may be a desirable or undesirable effect.

Compare that to languages which do go through a processing step (typically, called parsing) before any execution occurs. In that scenario, an invalid command (such as broken syntax) on line 5 would be caught during this parsing, before any execution has begun, and none of the program would run. For catching syntax (or otherwise "static") errors, generally it's preferred to know about them ahead of any doomed partial execution.

So what do "parsed" languages have in common with "compiled" languages? First, all compiled languages are parsed. So a parsed language is quite a ways down the road toward being compiled already. In classic compilation theory, the last remaining step after parsing is code generation: producing an executable form.

Once any source program has been fully parsed, it's very common that its subsequent execution will, in some form or fashion, include a translation from the parsed form of the program -- usually called an Abstract Syntax Tree (AST) -- to that executable form.

In other words, parsed languages usually also have code generation before execution, so it's not that much of a stretch to say that, in spirit, it's a compiled language.

JS source code is parsed before it is executed. The specification requires as much, because it calls for "early errors" -- statically determined errors in code, such as a duplicate parameter name -- to be reported before the code starts executing. Those errors cannot be recognized without the code having been parsed.

So JS is a parsed language, but is it compiled? In general, the answer is closer to yes than no. The parsed JS is converted to an optimized (binary) form, and that "code" is subsequently executed; the engine does not commonly switch back into line-by-line execution mode after it has finished all the hard work of parsing.

To be specific, this "compilation" produces a binary byte code (of sorts), which is then handed to a "JS virtual machine" to execute. Some like to say this VM is "interpreting" the byte code... but then that means Java, which also runs via a VM, is also intrepreted rather than compiled. That contradicts the typical impression that Java is a compiled language.

Another wrinkle is that JS engines employ multiple layers of JIT (Just-In-Time) processing, which again could reasonably be labeled either "compilation" or "interpretation". It's actually a fantastically complex situation under the hood of a JS engine.

So what do all these nitty gritty details boil down to?

Consider the entire context of how a JS source program is handled: the moment it leaves a developer's editor, it gets transpiled by Babel, then packed by Webpack, then undergoes half a dozen build processes, then it gets delivered in that very different form to a JS engine, and then that engine parses the code to an AST, then the engine converts that AST to a kind-of byte code, then that byte code is converted even further by the optimizing JIT compiler, and finally the JS VM executes the code.

Is that more like an interpreted, line-by-line script (such as Bash), or is that more like a compiled language that's processed in one-to-several passes first, before execution?

I think it's clear that in spirit, if not in actuality, JS is a compiled language.

And again, the reason that matters is, since JS is compiled, it means we are informed of static errors (such as malformed syntax) before our code is executed. That is a substantively different interaction model than typical "scripting" programs.









