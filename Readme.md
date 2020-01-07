# FP time minutes

2020-01-07: First session of the new! We watched and discussed the first episode of [Point-Free's SwiftUI series](https://www.pointfree.co/episodes/ep65-swiftui-and-state-management-part-1) from last July. We'll do the exercises for homework and talk about them next time.

2019-12-03: Coordinating local & network data fetching. Kevin brought up the "repository pattern." Logan brought up composable caching, as in [Brandon Kase's talk](https://www.youtube.com/watch?v=jxnDfU8ssK0).

2019-11-19: Property-based testing. We watched and discussed [Brian Gesiak - Functional Testing](https://www.youtube.com/watch?v=-TOp5-uComQ)

2019-11-12: An exercise in API design. More specifically, can we make the PURR library easier to test/override? We talked about different ways change it and their pros & cons. [2019-11-12 API discussion.txt](https://github.com/loganmoseley/functional-minutes/files/3860767/2019-11-12.API.discussion.txt)

2019-09-25: After some time off, we get back with pullbacks. [Pullback.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860766/Pullback.playground.zip)

2019-08-13: Once more with monoid: structs! 👩🏽‍⚖️ Trying out constructing legal requirements. 👨🏼‍⚖️ [Monoid+.playground](https://github.com/loganmoseley/functional-minutes/files/3860765/FP.2019-08-13.Monoid%2B.playground.zip).
- Also, at the very end Eric suggested it should be possible to **compose** monoids. I submit to you, [Monoid zip.playground](https://github.com/loganmoseley/functional-minutes/files/3860764/FP.2019-08-13.Monoid.zip.playground.zip)

2019-08-06: Extended the 'reduce' conversation to 'monoid', a useful concept for talking about making one thing out of many things, or, “Out of many, one." [Monoid.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860763/Monoid.playground.zip)

2019-07-31: Intuition for `reduce` [Intuition for reduce.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860762/Intuition.for.reduce.playground.zip)

2019-07-23: More algebraic data types: functions are exponential! [Math:Swift.txt](https://github.com/loganmoseley/functional-minutes/files/3860761/ADT.-.School.math.to.Swift.correspondence.txt), [ADT - Function.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860760/ADT.-.Function.playground.zip)

2019-07-16: Skipped for Maker Week.

2019-07-09: Watched Point-Free’s [episode on algebraic data types](https://www.pointfree.co/episodes/ep4-algebraic-data-types). 

2019-07-02: We explore a couple uses in code of `curry`--partially applying functions. [curry in code.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860759/curry.in.code.playground.zip) We also said a few:
- In a factory pattern
- Recording a user's plays, then scores
- Passing a token to an SDK
- Any async sequence, like user input that's designed as two steps
- Calling `map`

2019-06-23: Methods are functions in disguise. Plus, [“currying”](https://stackoverflow.com/questions/36314/what-is-currying#36321). [Methods are functions; currying.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860758/Methods.are.functions.currying.playground.zip)

2019-06-18: We asked: what’s a problem we’ve had recently? or what’s been on our minds? Some things said:
- News: e.g. SectionFrontVC with “FollowingChannel”
- News: UI getting weird when logging out because the UI also wants some different data because you’ve logged out
- Crossword: LbzFlowController’s use of reduce
→ We talked about the “diamond problem” for Observables. (Combine has the same behavior.)
[Observable diamond.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860757/Observable.diamond.playground.zip); [Combine diamond.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860756/Combine.diamond.playground.zip)

2019-06-11: What were our favorite things out of WWDC? What’s up with this new `Combine` library?

2019-05-28: Functor laws, some in Haskell and in Swift. [Functor.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860755/Functor.playground.zip)

2019-05-21: We *discovered* Functor. [Haskell/Functor](https://en.wikibooks.org/wiki/Haskell/The_Functor_class), [PointFree.co: map](https://www.pointfree.co/episodes/ep13-the-many-faces-of-map)

2019-05-17: We talked in groups to relate Array.map and Observable.map. We came up with three ideas:
1. Array elements are known instantly, map is called once and the closure is called instantly. (eager) OTOH, Observable elements are not known in advance, the Observable instance keeps the closure and applies is lazily. (lazy, JIT)
2. Their types are similar: `Array.map -> Array` & `Observable.map -> Observable`
3. Both preserve the order & count of the input.

2019-05-10: Reactive programming. What do “map” and “merge” mean for Observable?

2019-04-30: “zip” on Optional & Result! [zip for Optional & Result.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860754/zip.for.Optional.Result.playground.zip)

2019-04-23: All about implementing different “zip” functions ourselves. “How do you get to Carnegie Hall?” [implementing zip.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860753/implementing.zip.playground.zip)

2019-04-16: Last week was “zip” for Array. On the 16th we extended “zip” to Optional. One concept, two types? What does it mean?? [zip for Optional.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860752/zip.for.Optional.playground.zip)

2019-04-09: What's the deal with `Swift.zip` and [`PointFreeCo.zip(with:)`](https://www.pointfree.co/episodes/ep23-the-many-faces-of-zip-part-1)? Let's show how they’re related and why they're both called "zip". [zip.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860751/zip.playground.zip)

2019-04-02: Read through [What the heck is polymorphism?](https://dev.to/jvanbruegge/what-the-heck-is-polymorphism-nmh) with some examples in Swift: [what the heck is polymorphism.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860750/what.the.heck.is.polymorphism.playground.zip). Jim drew the [subtyping relationships](https://github.com/loganmoseley/functional-minutes/files/3860749/subtyping-relationships.pdf).

2019-03-26: Reviewed the ROP composition riddle from last week. Solution in [FP-20190326.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860748/FP-20190326.playground.zip)

2019-03-19: ROP examples in Swift. Big thanks to Jim for the translation. [FP-20190319 redacted.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860747/FP-20190319.redacted.playground.zip)

2019-03-12: “Railway Oriented Programming” with Scott Wlaschin. [video](https://vimeo.com/97344498), [site & slides](https://fsharpforfunandprofit.com/rop/). The day's playground: [FP-20190312.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860746/FP-20190312.playground.zip)

2019-03-05: What would the "Environment" style dependency injection look like in Crossword? Jim guided us through the very first bits. Point-Free [ep16](https://www.pointfree.co/episodes/ep16-dependency-injection-made-easy) & [ep18](https://www.pointfree.co/episodes/ep18-dependency-injection-made-comfortable).

2019-02-26: Jim tied together Swift sugar and functions & ideas we've been talking about. Definitely review the playground! [FP-20190226.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860745/FP-20190226.playground.zip)

2019-02-19: map, flatMap, compose, etc. Review because it helps :)

2019-02-12: Newsreader team wrapping up the ‘Home’ project, so this time was Crossword people looking at Crossword examples.

2019-01-15: Brian Green joins up! Diagrammed `map` with colors, which seemed to help a lot. We're slowly starting to see how it's not just another way to write a for-loop. More to come.

2019-01-08: Izza joins us! Refresher day. Diagrammed `compose` and diagrammed `map` on Array & Optional. [Map.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860744/Map.playground.zip)

2018-12-11: "Phantom type" and Pavel diagrammed `compose`--aka `>>>`--and `map`. [Compose.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860743/Compose.playground.zip)

2018-12-04: Showed examples of `>>>` and `|>`. Talked about `flip` and `curry`. See `>>>` and a curried `map` in [CrosswordFoundation/API/JSON.swift](https://github.com/loganmoseley/functional-minutes/files/3860798/JSON.swift.zip)

2018-11-27: Casual discussion of pointfree.co and tech things. Also, a real life stack overflow! See `HomeConverterThread` in ~~ios-newsreader/commits/d34db33f~~

2018-11-13: Function composition: motivate it, then do it. [FP 2018-11-13.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860742/FP.2018-11-13.playground.zip)

2018-10-30: Danny, Kayla, and Veronique join us! Back to basics: referential transparency, total/partial, pure/impure. [Partial.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860741/Partial.playground.zip)

2018-10-23: Type algebra

2018-10-16: Applying 'Applicative' to iOS News's 'Rules.Result'

2018-10-09: Rediscovering map and flatMap in callbacks; https://vimeo.com/292702159; [Oct 2 & 9 Playgrounds.zip](https://github.com/loganmoseley/functional-minutes/files/3860740/Oct.2.9.Playgrounds.zip)

2018-10-02: Applicative

2018-09-25: Composition ideas in code, passing Bool vs fn, functor laws

2018-09-18: Globals in NYTSwiftFoundation and in News.app

2018-09-11: Jim's styling ruleset DSL

2018-09-04: DSL practice ([pointfree.co #27](https://www.pointfree.co/episodes/ep27-domain-specific-languages-part-2))

2018-08-28: watched "I See What You Mean" by Peter Alvaro (youtube.com)

2018-08-21: Expression problem; [Expression Problem 2.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860739/Expression.Problem.2.playground.zip)

2018-08-13: Profunctor the idea and an example: Logan's type-safe key-value store idea, `StoreQuery`

2018-08-07: Lambda calculus, Lambda cube, polymorphism (subtyping, ad hoc), type operators (kinds), dependent types

2018-07-31: Contrafunctor and Profunctor

2018-07-17: Discuss flatMap and Kleisli composition >=>; [Kleisli.aquarium.zip](https://github.com/loganmoseley/functional-minutes/files/3860738/Kleisli.aquarium.zip); [Kleisli.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860737/Kleisli.playground.zip)

2018-07-10: Drew map and flatMap, discussed “functional”

2018-07-03: (Skipped. Early out before July 4.)

2018-06-26: overall motivation. what is FP? map, bimap, flatMap

2018-06-19: split & bimap, `A??.flatMap(id) -> A?`

2018-06-12: curry; apply `|>` and `<|`; compose `>>>` and `<<<`

2018-06-05: fish operator `>=>` glug glug

2018-05-14: reviewed examples from Crossword and Newsreader of the more "functional" style

2018-05-08: motivate and diagram 'map' and 'flatMap' (Jim R and Craig H are new)

2018-05-01: (Skipped. Logan was out.)

2018-04-24: semigroup, monoid

2018-04-17: reiterate map and flatMap by diagram, the algebra of types.

2018-04-10: anatomy, theory, and motivation of map and flatMap

2018-04-03: referential transparency, total/partial, (non-)surjective, fn composition, map, and hinting at the map typeclass
