I run a functional programming weekly meeting called "FP Club" at The New York Times. We started 2020 by diving into SwiftUI. These are their stories.

# SwiftUI Club minutes

2020-04-21: We broke into small groups to build a UISwitch replacement. We got experience with `@State` vs `@Binding`, saw how `Circle`’s frame works, saw `.onTapGesture { … }`, and learned to not name your project a SwiftUI reserved word! Example project: [SwitchUI.zip](https://github.com/loganmoseley/programming-club/files/4512627/SwitchUI.zip).

2020-04-14: Zev showed us his Mini in SwiftUI project. Very cool! We talked about one advantage of SwiftUI layout versus Auto-Layout: composition/encapsulation. There’s no spooky action at a distance. That’s because Auto-Layout constraints for all views are in the linear solver all at once. We also talked about GeometryReader, combining HStack & Spacer, and [netsplit.com](https://netsplit.com/).

2020-03-31:

We looked at a challenge from [Swift Over Coffee](https://github.com/twostraws/SwiftOverCoffee), which asked listeners to build the Apple Watch "breathe" animation in 1 hour. We worked through [Paul Hudson's submission](https://gist.github.com/twostraws/c69e4080099ae7ac45bfd9b1e15a4269) to see how it worked, then experimented with animation code on our own.

<details>
 <summary>Paul Hudson's submission</summary>

```swift
//
// Gasp – a quick clone of the watchOS Breathe UI, for Swift Over Coffee
// https://github.com/twostraws/SwiftOverCoffee
//
import SwiftUI

struct ContentView: View {
    @State private var flowerOut = false

    var body: some View {
        ZStack {
            Color.black.edgesIgnoringSafeArea(.all)

            ZStack {
                ForEach(0..<6) {
                    Circle()
                        .foregroundColor(Color(red: 0.6, green: 0.9, blue: 0.8))
                        .frame(width: 200, height: 200)
                        .offset(x: self.flowerOut ? 100 : 0)
                        .rotationEffect(.degrees(Double($0) * 60))
                        .blendMode(.hardLight)
                }
            }
            .rotationEffect(.degrees(flowerOut ? 120 : 0))
            .scaleEffect(flowerOut ? 1 : 0.25)
            .animation(Animation.easeInOut(duration: 4).delay(0.75).repeatForever(autoreverses: true))
            .onAppear() {
                self.flowerOut.toggle()
            }
        }
    }
}
```
</details>

<details>
 <summary>Our first animation test</summary>

```swift
import SwiftUI

struct AnimatedView: View {

    @State var far: Bool = false

    var body: some View {
        VStack {
            HStack(spacing: self.far ? 100 : 10) {
                Text("Hello,")
                Text("World")
                    .rotation3DEffect(.degrees(self.far ? 180 : 0), axis: (x: 1, y: 1, z: 0))
            }
            .animation(Animation.easeInOut(duration: 2).repeatForever(autoreverses: true))
            Button(action: {
                self.far.toggle()
            }) {
                Text("Change stuff")
            }
        }
        .onAppear() {
            self.far.toggle()
        }
    }
}

struct AnimatedView_Previews: PreviewProvider {
    static var previews: some View {
        AnimatedView()
    }
}
```
</details>

<details>
 <summary>Our nearly-working SwiftUI loading spinner. Need to figure out why it doesn't loop correctly</summary>

```swift
import SwiftUI

struct Spinner: View {

    @State private var someBool = false

    var body: some View {
        ZStack {
            ForEach(0..<12) {
                Capsule()
                    .foregroundColor(self.someBool ? Color.blue : Color.red)
                    .frame(width: 10, height: 30)
                    .offset(x: 0, y: 40)
                    .rotationEffect(.degrees(Double($0) * 30))
                    .animation(Animation.easeOut(duration: 0.2)
                        .delay(1.0 / 12 * Double($0))
                        .repeatForever(autoreverses: false)
                )
            }
        }
        .onAppear() {
            self.someBool.toggle()
        }
    }
}

struct Spinner_Previews: PreviewProvider {
    static var previews: some View {
        Spinner()
    }
}
```
</details>

2020-03-24: We worked through Apple’s third tutorial on SwiftUI: [Handling User Input](https://developer.apple.com/tutorials/swiftui/handling-user-input). We basically learned how to pass around a brute-force state: `@EnvironmentObject`. Cool, but how should a larger app handle state, handle limiting what each view needs to know about?

2020-03-17: We worked through Apple’s second tutorial on SwiftUI: [Building Lists and Navigation](https://developer.apple.com/tutorials/swiftui/building-lists-and-navigation). It was kinda boring, but only because this is the third or fourth time we’ve done lists! We also saw how to change previews within in PreviewProvider.

2020-03-10: We worked through Apple’s [first tutorial](https://developer.apple.com/tutorials/swiftui/creating-and-combining-views) in their series of SwiftUI intro tutorials that launched at WWDC. We also looked at Paul Hudson’s [SwiftUI by Example](https://www.hackingwithswift.com/quick-start/swiftui/), but it seemed too "bottom-up," in the sense that it had detailed information on each component, but lacked a more holistic view of how to build more complete things.

We also mentioned:

- Paul Hudson’s [100 Days of SwiftUI](https://www.hackingwithswift.com/100/), a series of medium-complexity tutorials that build on each other to teach you how to make a few simple apps and games.
- [`UIViewPreviewProvider`](https://github.com/mrabiciu/UIViewPreviewProvider), an open-source repo that lets you use SwiftUI previews while developing non-SwiftUI apps.
- An [NSHipster Post](https://nshipster.com/swiftui-previews/) on a similar idea of using SwiftUI previews in non-SwiftUI development, but with a different approach. Somewhere between these two lies a nice and usable system ;)

2020-03-03: Having ended the iDine project, Paul Hudson wanted to walk us through the Xcode project template and some view modifiers. We followed [here](https://www.hackingwithswift.com/quick-start/swiftui/whats-in-the-basic-template) through and including [here](https://www.hackingwithswift.com/quick-start/swiftui/how-to-adjust-the-way-an-image-is-fitted-to-its-space).

2020-02-25: We followed [here](https://www.hackingwithswift.com/quick-start/swiftui/presenting-an-alert) through [here](https://www.hackingwithswift.com/quick-start/swiftui/wrap-up-our-swiftui-project-is-complete). We learned about alerts, editing tables, and got a few "challenges" from Paul. [iDine 2020-02-25.zip](https://github.com/loganmoseley/functional-minutes/files/4283539/iDine.2020-02-25.zip)

2020-02-18: Starting [here](https://www.hackingwithswift.com/quick-start/swiftui/adding-tabview-and-tabitem) we learned about creating TabViews, using @State bindings, Form views, two-way bindings, and formatted string interpolation. We ended at the end of [here](https://www.hackingwithswift.com/quick-start/swiftui/formatting-interpolated-strings-in-swiftui). [iDine 2020-02-18.zip](https://github.com/loganmoseley/functional-minutes/files/4283536/iDine.2020-02-18.zip)

2020-02-11: Starting [here](https://www.hackingwithswift.com/quick-start/swiftui/polishing-designs-with-fonts-and-colors) we learned about view styling, ZStack and some of SwiftUI data pipeline: environment objects and `@Published`. We ended at the end of [here](https://www.hackingwithswift.com/quick-start/swiftui/adding-items-to-an-order-with-environmentobject): [iDine 2020-02-11.zip](https://github.com/loganmoseley/functional-minutes/files/4188321/iDine.2020-02-11.zip).

2020-02-04: Switched to Paul Hudson’s _SwiftUI by Example_ book, since it seems more appropriate for our novice SwiftUI level :) We did the first three pages of [Building a complete project](https://www.hackingwithswift.com/quick-start/swiftui/swiftui-tutorial-building-a-complete-project).

2020-01-28: Welcome all the new people!

We watched and discussed the first episode of [Point-Free’s SwiftUI series](https://www.pointfree.co/episodes/ep65-swiftui-and-state-management-part-1). Follow along at home to get some SwiftUI under your fingers, or take a look at the playground: [2020-01-28 - Point-Free #65 StateManagement.playground.zip](https://github.com/nytm/ios-swift-foundation/files/4124565/2020-01-28.-.Point-Free.65.StateManagement.playground.zip).

2020-01-14: We did the first couple [exercises](https://www.pointfree.co/episodes/ep65-swiftui-and-state-management-part-1#exercises) in Point-Free episode 65.

2020-01-07: New year, new huge topic!

We watched and discussed the first episode of [Point-Free’s SwiftUI series](https://www.pointfree.co/episodes/ep65-swiftui-and-state-management-part-1) from last July. We’ll do the exercises for homework and talk about them next time.

# FP Club minutes

2020-01-07: First session of the new! We watched and discussed the first episode of [Point-Free’s SwiftUI series](https://www.pointfree.co/episodes/ep65-swiftui-and-state-management-part-1) from last July. We’ll do the exercises for homework and talk about them next time.

2019-12-03: Coordinating local & network data fetching. Kevin brought up the "repository pattern." Logan brought up composable caching, as in [Brandon Kase’s talk](https://www.youtube.com/watch?v=jxnDfU8ssK0).

2019-11-19: Property-based testing. We watched and discussed [Brian Gesiak - Functional Testing](https://www.youtube.com/watch?v=-TOp5-uComQ)

2019-11-12: An exercise in API design. More specifically, can we make the PURR library easier to test/override? We talked about different ways change it and their pros & cons. [2019-11-12 API discussion.txt](https://github.com/loganmoseley/functional-minutes/files/3860767/2019-11-12.API.discussion.txt)

2019-09-25: After some time off, we get back with pullbacks. [Pullback.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860766/Pullback.playground.zip)

2019-08-13: Once more with monoid: structs! 👩🏽‍⚖️ Trying out constructing legal requirements. 👨🏼‍⚖️ [Monoid+.playground](https://github.com/loganmoseley/functional-minutes/files/3860765/FP.2019-08-13.Monoid%2B.playground.zip).
- Also, at the very end Eric suggested it should be possible to **compose** monoids. I submit to you, [Monoid zip.playground](https://github.com/loganmoseley/functional-minutes/files/3860764/FP.2019-08-13.Monoid.zip.playground.zip)

2019-08-06: Extended the “reduce” conversation to “monoid”, a useful concept for talking about making one thing out of many things, or, “Out of many, one." [Monoid.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860763/Monoid.playground.zip)

2019-07-31: Intuition for `reduce` [Intuition for reduce.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860762/Intuition.for.reduce.playground.zip)

2019-07-23: More algebraic data types: functions are exponential! [Math:Swift.txt](https://github.com/loganmoseley/functional-minutes/files/3860761/ADT.-.School.math.to.Swift.correspondence.txt), [ADT - Function.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860760/ADT.-.Function.playground.zip)

2019-07-16: Skipped for Maker Week.

2019-07-09: Watched Point-Free’s [episode on algebraic data types](https://www.pointfree.co/episodes/ep4-algebraic-data-types). 

2019-07-02: We explore a couple uses in code of `curry`--partially applying functions. [curry in code.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860759/curry.in.code.playground.zip) We also said a few:
- In a factory pattern
- Recording a user’s plays, then scores
- Passing a token to an SDK
- Any async sequence, like user input that’s designed as two steps
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

2019-04-09: What’s the deal with `Swift.zip` and [`PointFreeCo.zip(with:)`](https://www.pointfree.co/episodes/ep23-the-many-faces-of-zip-part-1)? Let’s show how they’re related and why they’re both called "zip". [zip.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860751/zip.playground.zip)

2019-04-02: Read through [What the heck is polymorphism?](https://dev.to/jvanbruegge/what-the-heck-is-polymorphism-nmh) with some examples in Swift: [what the heck is polymorphism.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860750/what.the.heck.is.polymorphism.playground.zip). Jim drew the [subtyping relationships](https://github.com/loganmoseley/functional-minutes/files/3860749/subtyping-relationships.pdf).

2019-03-26: Reviewed the ROP composition riddle from last week. Solution in [FP-20190326.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860748/FP-20190326.playground.zip)

2019-03-19: ROP examples in Swift. Big thanks to Jim for the translation. [FP-20190319 redacted.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860747/FP-20190319.redacted.playground.zip)

2019-03-12: “Railway Oriented Programming” with Scott Wlaschin. [video](https://vimeo.com/97344498), [site & slides](https://fsharpforfunandprofit.com/rop/). The day’s playground: [FP-20190312.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860746/FP-20190312.playground.zip)

2019-03-05: What would the "Environment" style dependency injection look like in Crossword? Jim guided us through the very first bits. Point-Free [ep16](https://www.pointfree.co/episodes/ep16-dependency-injection-made-easy) & [ep18](https://www.pointfree.co/episodes/ep18-dependency-injection-made-comfortable).

2019-02-26: Jim tied together Swift sugar and functions & ideas we’ve been talking about. Definitely review the playground! [FP-20190226.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860745/FP-20190226.playground.zip)

2019-02-19: map, flatMap, compose, etc. Review because it helps :)

2019-02-12: Newsreader team wrapping up the ‘Home’ project, so this time was Crossword people looking at Crossword examples.

2019-01-15: Brian Green joins up! Diagrammed `map` with colors, which seemed to help a lot. We’re slowly starting to see how it’s not just another way to write a for-loop. More to come.

2019-01-08: Izza joins us! Refresher day. Diagrammed `compose` and diagrammed `map` on Array & Optional. [Map.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860744/Map.playground.zip)

2018-12-11: "Phantom type" and Pavel diagrammed `compose`--aka `>>>`--and `map`. [Compose.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860743/Compose.playground.zip)

2018-12-04: Showed examples of `>>>` and `|>`. Talked about `flip` and `curry`. See `>>>` and a curried `map` in [CrosswordFoundation/API/JSON.swift](https://github.com/loganmoseley/functional-minutes/files/3860798/JSON.swift.zip)

2018-11-27: Casual discussion of pointfree.co and tech things. Also, a real life stack overflow! See `HomeConverterThread` in ~~ios-newsreader/commits/d34db33f~~

2018-11-13: Function composition: motivate it, then do it. [FP 2018-11-13.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860742/FP.2018-11-13.playground.zip)

2018-10-30: Danny, Kayla, and Veronique join us! Back to basics: referential transparency, total/partial, pure/impure. [Partial.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860741/Partial.playground.zip)

2018-10-23: Type algebra

2018-10-16: Applying `Applicative` to iOS News’s `Rules.Result`

2018-10-09: Rediscovering map and flatMap in callbacks; https://vimeo.com/292702159; [Oct 2 & 9 Playgrounds.zip](https://github.com/loganmoseley/functional-minutes/files/3860740/Oct.2.9.Playgrounds.zip)

2018-10-02: Applicative

2018-09-25: Composition ideas in code, passing Bool vs fn, functor laws

2018-09-18: Globals in NYTSwiftFoundation and in News.app

2018-09-11: Jim’s styling ruleset DSL

2018-09-04: DSL practice ([pointfree.co #27](https://www.pointfree.co/episodes/ep27-domain-specific-languages-part-2))

2018-08-28: watched "I See What You Mean" by Peter Alvaro (youtube.com)

2018-08-21: Expression problem; [Expression Problem 2.playground.zip](https://github.com/loganmoseley/functional-minutes/files/3860739/Expression.Problem.2.playground.zip)

2018-08-13: Profunctor the idea and an example: Logan’s type-safe key-value store idea, `StoreQuery`

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

2018-05-08: motivate and diagram `map` and `flatMap` (Jim R and Craig H are new)

2018-05-01: (Skipped. Logan was out.)

2018-04-24: semigroup, monoid

2018-04-17: reiterate map and flatMap by diagram, the algebra of types.

2018-04-10: anatomy, theory, and motivation of map and flatMap

2018-04-03: referential transparency, total/partial, (non-)surjective, fn composition, map, and hinting at the map typeclass
