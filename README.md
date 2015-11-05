- Feature Name: PUT Incentive Model
- Type: New Feature
- Conflicts With: Pay APP devs using Gets
- Related components: Anything that has to do with the network rewarding APPs

# Summary

The PUT Incentive Model is designed to solve many problems, and most recently many have come to the surface. Issues regarding:

* Safecoin Divisibility
* Pay the Producer
* Network Bankrupsy via Free GETs
* APP reward mechanism

are all affected in some way by this proposal. This is intended to set the stage for a fair network, wherein all who participate in their various functions (Farmer, APP Dev, Content Creator, End-User) will all have an opportunity to benefit and benefit from the network.

The PUT Incentive Model notion was previously introduced by @bcndanos [here](https://forum.safenetwork.io/t/safe-pod-sf-safecoin-the-safe-ecosystem/2938/37) and has since been floating around in the forums, while the plan was still to reward APP developers by GETs. A simpler proposal can be found [here](https://forum.safenetwork.io/t/proposal-app-rewards-by-pay-per-put-commission/5812) by @polpolrene and @DavidMtl. This plan does not set out to change the fact that APP developers be paid, but the way that the network does so and how APP developers can use these funds to help cultivate a community both around their individual APPs, as well as the SAFE Network in general.

# Motivation

There have been many discussions about rewarding APP developers with GETs, and how that system can be gamed without End-Users really noticing. Without End-Users really *feeling the impact* of how these malicious APPs could cheat the system, they will not be motivated in any visceral way to dissuade this type of behavior until it is too late and the SAFE Network fails because of these greedy developers.

By rewarding per PUT, if a malicious app developer were to institute a policy wherein an APP were to make more PUTs than was necessary, then the initial funds to facilitate these extraneous PUTs would necessarily come out of the wallets of the End-Users. This is easily recognizable, and we can rely on human nature, specifically greed, to ensure that these types of APPs, no matter the quality of their functionality, will not prosper.

This is the most significant and belabored point in the PUT Incentive Model, and one that is enough to warrant a careful consideration of the topic on its own. But as we explore the proposal deeper, there will emerge several other inherent benefits to this system that deal with several issues that the community at large has been exploring.

For the argument that "Not all APPs need to PUT" see the "Drawbacks" section.

# Detailed design

To preface this section, there will be no concrete detailed network design as of yet, this is simply a Request for Comments that is based on the morality of the feature alone. (and as such is not a complete RFC, but rather one to discuss in the community).

## Network Bankruptcy

It has been put forth by @jreighley that [Free GETs aren't going to fly](https://forum.safenetwork.io/t/free-gets-arent-going-to-fly/5836). There are a couple points to the effect that they may, but many of the solutions chip away at the problem, and don't provide a paradigm shift to counteract the effect.

Assuming that the premise of and responses to the argument are understood, there still remains one big unanswered problem - GETs are free *and* can generate income. If the economics that I understand still hold, this will not work. Namely that you can't get something for nothing.

There has been much speculation (and math) done that suggest that GETs will be overwhelmingly more popular than PUTs. So the question I have is "Why would we reward that which is over-abundant, prone to gaming, and not contributing anything to the network?"

The answer is that we shouldn't. Providing an *inherant value* to the network should be rewarded. PUTs are a value to the network in both a technological sense, and a common one. Technologically speaking, this will cause more PUTs to happen to balance out the cost of operating the network. From a more abstract point of view, it increases the ubiquitousness of PUTs, while making sure that APPs are designed to contribute to the collective amount of information that is on the network. This helps to both increase adoption, and disseminate information into the right hands.

Unfortunately, this does nothing to ease the load of the network's [Vault Routing Burden](https://forum.safenetwork.io/t/vault-routing-burden/5663/70) (sorry @Seneca!) other than the fact that the network does not need to worry about rewarding APP devs per GET, only per PUT. (of which there will be less.)

## Identification for reward purposes

There is also the problem of how to distinguish a particular APP's GETs from another. This may lead to many ideas that compromise, if not outright break the anonymity that the network works so hard to maintain. Think browser tracking via UserAgent strings. (also UserAgent spoofing...) I would assert that it would be easier to identify PUTs made from specific APPs rather than GETs.

One of the reasons being that APPs (following the premise of this proposal) will already be designed in such a way as to facilitate PUTting information on behalf of the End-User. This then can be structured to include information in - or be able derive from the context of - the data indicating which application is deserving of a reward.

### Persona Home Directories

One such implementation is to structure all public data into groupings - either personified or anonymous.

For the time being, it would be best to think of the network as a typical structured filesystem - although this is not the case, and the implementation for this system may be amended to reflect the structure of the network. (worse-case scenario this is not possible, but the idea would just be structured differently)

In this example implementation, every persona that a person wishes to post under will have subdirectories under their one "persona directory" which is created one per each app that the persona uses. Any public data can be stored there, and when retrieving the data the APP can determine which persona the data falls under based on the parent directory.

Also then, each app can have their own directory for anonymous content that was PUT - not tied to any persona or any other identifying mark. All that is known is that *this APP* caused the data to be PUT, and therefore the reward mechanism is triggered.

### Tagging

Another implementation is PUT tagging. This is where any PUT that is done on the bahalf of an End-User by an APP is tagged to specify that *this APP* posted that data on behalf of the user, and the reward mechanism is triggered.

This is not as recommended because it may decrease the amount of data that one chunk can store, as well as possibly open vectors to de-anonymization attacks. There is no way to prove this however, and it *does* remain one of the better ideas on how to implement this.

## APP Wallets

This proposition includes a new type of wallet. An autonomous APP Wallet that is driven solely by code, and no one user has access to all of the APPs funds (unless they code themselves to).

The implementation is intended to facilitate the handling of Payments *from* the network, and *to* devs and content creators alike.

### Reward Mechanisms

The assumption is that the rewards will all be pooled together to eventually be split out to the devs and the content creators. The hope is that this will incentivize community building as well as development contributions in the race for a bigger rewards pool per APP.

The times at which the rewarding the individual payouts happen will be up to the APP devs (and therefore the community)

The percentage that the content creators get will be up to the APP devs (and therefore the community)

The percentage that the devs get will be up to the magical Git-Jira APP (see: To the Devs)


#### To the Devs

There is one thing that I've been scratching my head about for the longest time. In open source software, isn't it better to have many people want to participate in one good APP instead of having many people start their own individual (similar) under-maintained APPs? Well, then why limit the wallet address to one person's? This no doubt will start more flame wars than vim has ever ended.

There is an APP that has yet to be coded - and this proposal is designed to motivate it's development. I see it as a combination of Github and Jira - in that it is a decentralized (distributed) repository of source code with all of the usual pull requests, merges, forks...all the goodies along with story points.

With the information supplied by that APP, there can be code to distribute the reward generated by the APP to the individual devs based on the statistics of the contributions to the APP. This provides the motivation for devs to both contribute to larger codebases, as well as start their own Apps.

#### To the Content Creators

So many artists, so little money, *amiright?!*  Well, let's change that.

> @DavidMtl
>
> Instead of thinking that we fixed the producer problem by rewarding uploaders with the Get reward, I think it would be much much more productive to develop platform that will help them get real money like: Shop plugins, crowdfunding, patreonage, subscriptions, gift[ing/ tipping], etc.

There is no mandate in this proposal that says that content creators need to be given a reward oportunity - and neither should there be. However, this proposal facilitates, even *encourages* such a system to be commonplace in the scenarios where it is appropriate.

##### Revenue Sharing

This entire system encourages revenue sharing by pooling together the various PUT rewards for one APP under one APP Wallet. However, not everyone gets an equal slice of the pie. That would just be communism.

###### Accessing vs Appreciating Content

The point has been brought up that accessing information does not necessarily mean that you are in favor of it.

If the network was to reward every *bad guy* blog post that I read, I would never read them. Therefore would never comment on his posts, and therefore never stop the next Hitler with my kind and rational debates.

That may be a drastic scenario, however the point remains that the internet, and before that the television, and before that the radio, and before that the printing press...their creators all held high hopes that while learning about each other, we could come to respect each other's differences and work together.

If an End-User is afraid to reward something that they think they might disagree with, then they will mostly likely elect to keep themselves ignorant. This is sad but true. Only by making information both free and accessible without consequence will we take a step closer to a greater understanding of one another. Remember, many wars were fought based on misunderstandings.

###### Voting System

This proposal allows developers to code a voting system into their APP. I'm sure most of us here are familiar with reddit and it's style, so that's the example I will be using for this...uh...example.

Giving an thumbs up/upvote as a sign of approval is a well-documented process both pre and post internet. It signifies that a viewer sees value in the subject at hand.

Contrary to a tipping mechanism (such that every upvote is a safecoin that comes out of the user's wallet) a voting system can be implemented against the reward pool. Higher upvoted content will get a bigger reward, while downvoted content will not. The price will be similar (if not the same) to PUT each piece of data (say - a self, text post) but the reward *only* depends on the value that viewers see in that content.

This means that your homemade cat video has the same chance of getting massively rewarded as professional coverage of bombings in the middle east. Will there be different apps for different content? Possibly - but that's up to the evolution of the network and all up to the attitudes of the End-Users.

##### Subscription Services

Subscription services are great for distributing data that both gets stale quickly, and is easily replaced. Typically these come from a single source - say a particular porn company or your local newspaper.

These types of APPs will not necessarily distribute content though. There is a high demand for apps which provide a service independent of the content consumed (think Wolfram|Alpha...it's why I passed AP Calc). These are the APPs that don't have content creators to pay, but still provide useful information. However, since they generate little-to-no PUTs (although they certainly can) they may be sold with a subscription to the service or it's own database of information.

Whichever paradigm an APP centers itself around, there may be a need to use a subscription-based business model. This proposal does not hinder nor unproportionally reward those APPs.

##### Tipping services

Tipping services are seen as the next wave of online revenue generation. While I may disagree, I certainly must admit that it is on the rise, and that this is a very good thing.

Tipping very easily fits into the paradigm of the SAFE Network, and APPs who implement this will have no shortage of content creators hoping to make it big through tips. And I mean...that's really all there is to say about that. I don't see why *any* APP that provides content wouldn't have a tipping mechanism to reward the creators.

### Safecoin Divisibility

Since this proposal revolves mainly around splitting up the reward that any given APP recieves, instead of inflation to counteract the overvaluation of Safecoin, this supports Safecoin Divisibility as that would lead to the ability for an APP to pay out both the micro-est of micro-payments and the largest of reward sums to the respective deserving parties.

# Drawbacks

1) Not all APPs need to PUT

No, they don't. This obviously doesn't affect content creators (as the content would necessarily have to be PUT) so we can leave them out of this.

So what can the devs do for APPs that don't PUT? Well, there is always the payment directly from the users to the APP Wallet. (such as micro-payments or subscription services)

Also, keep in mind that not all PUTs have to be in the form of public content. PUTs can be initiated for configuration files, or messages. There are all types of PUTs, and different APPs will utilize space on the network differently.

1a) Lurkers make up 90% of the existing Internet

And they are not contributing therefore need not be rewarded, or reward those who facilitate them although they are certainly free to lurk. When they decide to contribute they can do so in the most advantageous way possible.

2) I'll just create an APP to PUT everything I want to.

If you're just talking about PUTting your CD collection up and getting rewarded for it, hell, I'll probably be the first one to do that. Seems like a good idea to me. And if it's good enough to compete with LiteStuff (or other spin-offs) by all means go for it!

But are you going to create a interface for every APP that you use? Not likely. Are End-Users going to be using it too? Not if it's bad. What if it's good? Then either you got yourself your own killer APP, or you merge into the bigger APP (whose funds you started siphoning anyways) and the combination of the two services can provide more revenue than either could alone (by virtue of them separately splitting up the community and therefore the reward pool).

3) This will encourage high-PUT APPs

What number of PUTs is high? How many are necessary? These questions and more can only be figured out with the natural evolution of the network. If an APP of the same quality and compatability with a popular APP shows up and does the same actions with less PUT costs, it stands to reason that the users will use that APP.

However, if that APP is limited by the amount of features, where the more expensive APP has more features, some may choose to use the fully-featured APP that's more expensive. It's a free market, baby!

4) Content Copying

This proposal does not aim to solve the problem of copying content by slightly amending to or altering the file. As such it is still vulnerable to any exploitation of copied content that PtP would be. This is still an issue that needs to be solved. (Specifically both Watermarking and Proof of Unique Human require further investigation for a solution to be found).

For the time being, I would assert that this would be most effectively done at the APP level, with some sort of decentralized moderation technique. But that is beyond the scope of this document.

5) What if my associated APP went belly-up / I want to move my content to another APP?

Well, that's the thing about content, once it's there it's there (unless it's copied - see above). It is then consumed.

If it needed to be formatted in a separate way in order to allow it to be accessed by another APP, that may constitute a change such that another PUT would have to be issued to resubmit it to the network under a new APP. I'm not sure.

This is more of a technical question about the implementation of which I haven't even nailed down yet.

# Alternatives

See @dyamanaka's OP [here](https://forum.safenetwork.io/t/app-developer-rewards-discussion/3045)

* GET incentive model
* GET & PUT incentive model

The alternatives below (also mentioned in the above link) are not necessarily mutally exclusive to the proposed system.

* One-time payment model
* Subscription Payment
* Reoccurring micropayment

# Unresolved questions

Many I'm sure, but right now I would like to hear analysis of this proposal that the community has to offer.
