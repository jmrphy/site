---
title: "The moral foundations of social justice warriors"
subtitle: The new ideological fractures
summary: "Are Social Justice Warriors a real ideological faction of the Left, with a unique moral psychology? The first in a multi-part series using 'big data' to understand obscure ideological subcultures."
date: 2018-01-15
url: blog/2018/01/15/moral-foundations-of-social-justice-warriors
tags:
- academic research
- social science
- ideology
- data
- R
- visualization
categories:
- theory & empirics
keywords:
- social justice warriors
- sjw
- moral justice
- social justice foundation
- psychology of morality
- what is sjw
- define social justice warrior
- social justice warrior definition
- moral foundations
- what is a social justice warrior
- jonathan haidt sjw
- haidt moral foundations
---

What is a social justice warrior? The term *SJW*, short for *social justice warrior,* is now a well-known piece of internet slang. It refers to a particular tendency within left-wing political activism today. People often ask me to define "social justice warrior", or they ask: "Isn't that just an epithet, like 'political correctness,'  used by conservatives to dismiss the claims of marginalized people?" Or else it is sometimes suggested that such an ideologically loaded term is beneath a Serious Social Scientist. But I've been thinking about these questions a lot, and my sense is that *SJW* seems to reasonably distinguish a particular dimension of left-wing ideology and behavior from the larger multidimensional umbrella of "the Left." 

Whether *SJW* is a defensible analytical construct is ultimately an empirical question. Is "SJW" a term that conservatives use, without logical constraint, to dismiss any lefty they feel like dismissing? Or does *SJW* name a particular type of leftist statistically distinguishable from other leftists?

### Data and Method: Self-identified SJWs on Twitter

How might we do this? One approach would be to list clear, observable criteria that we believe define SJWism, and which distinguish it from leftism in general. We could then go find people who meet the criteria; collect data on their speech or behavior; and compare them to the general population and/or other leftists. One immediate problem with this approach is
that many leftists would deny being SJWs, no matter how much they matched our definition. This would seem to preclude the intersubjective consensus to which science generally aspires.

After thinking about this for a while, one possibly clever solution dawned on me. A non-trivial number of leftists on the internet *self-identify* as SJWs. Although they are often being ironic, of course, their decision to own the label suggests they are likely the same individuals right-wingers have in mind when they use the term pejoratively. While there is likely significant normative disagreement between ironically self-identified SJWs and their right-wing critics about what the SJW persona means, self-identification with SJWism provides a reasonably attractive solution for how to draw an empirical sample of this vexing, semi-mythical ideological faction.

To investigate whether SJWs are empirically distinguishable from other leftists, I collected more than a million Twitter status updates by more than 500 individuals who self-identify as "SJW" or "social justice warrior" in their Twitter bio. I manually checked the accounts and removed cases where SJW was used in other ways, (e.g. as initials for someone's full name.) I then collected a similarly sized sample of tweets drawn randomly from the Twitterverse, and a similarly sized sample from accounts whose profile includes the phrase "FeelTheBern." These are our reference groups: the average user, and then Bernie Sanders supporters. The intuition for isolating Bernie Sanders supporters is that their broader-based, often class-centric,
democratic socialism likely revolves around principles different than those at the core of SJWism. To be sure, there would certainly be SJWs within the camp of "Berners," but the center of gravity is likely different. Note, however, that this overlap is not a problem for us; in fact, it will only make differences between SJWs and Berners *harder* to distinguish statistically, which means that, if I identify some, this confounding should increase rather than decrease our confidence that these differences are real.

In future work I hope to pursue this question in greater detail, but for this blog post, I am curious about the possibility that SJWs have different "moral foundations" compared to the average leftist. Moral Foundations Theory may help. Jonathan Haidt and his co-authors have identified specific moral foundations, some of which help to explain the difference between leftists and conservatives (see <a target="_blank" href="https://www.amazon.com/gp/product/0307455777/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=0307455777&linkCode=as2&tag=jmrphy-20&linkId=d25f4bb9eaf812f1b7ee03b5f81f5ef6">Haidt's book <i>The Righteous Mind</i></a><img src="//ir-na.amazon-adsystem.com/e/ir?t=jmrphy-20&l=am2&o=1&a=0307455777" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />). Might these differences in the sense of moral justice also help to explain SJWism as a deviation from general leftism?

### Analysis

After reducing the samples to English-only status updates, I then reduced the two largest corpora to equal the smallest of the three. Each final corpus consists of 894,337 tweets. I then applied the [Moral Foundations Dictionary](http://www.moralfoundations.org/sites/default/files/files/downloads/moral%20foundations%20dictionary.dic) developed by Graham and Haidt, using the R package [*quanteda*](http://quanteda.io/). One question is whether SJWs are generally more moralistic. A first look at the total number of moral features across the three corpora shows that SJWs are not generally more moralistic than Berners. For both groups, there are about .3 moral features per tweet, on average (about .32 for Berners and .3 for SJWs). Unsurprisingly, both activist tendencies invoke moral terms more frequently than in the random sample of tweets (20% moralistic.)

Figure 1 plots, for each corpus of tweets, the number of moral features in each category, divided by the total number of tweets in the corpus. This gives us a sense of how much each group emphasises each moral foundation, relative to their whole output. Figure 1 shows only the 5 primary foundations identified by Jonathan Haidt and colleagues, plus a separate category for general moral terms that do not clearly fall into any of the moral foundations. As you can see from Figure 1, SJWs and Berners do not use moral terms very often, but certainly more often than the random sample.

![The Moral Foundations of SJWs Figure 1](https://i.imgur.com/XZNLypn.png "Frequency of Moral Words per Tweet")

Figure 2 plots the same data at a finer resolution, breaking each foundation into positive/virtuous terms and negative/vice terms. This plot highlights how general moralistic language seems uniquely common among SJWs, a point I will return to in the Discussion section.

![The Moral Foundations of SJWs Figure 2](https://i.imgur.com/8KlvwfY.png "Frequency of moral terms across 11 categories")

Figure 3 plots the relative frequency of moral words, which gives us a sense of how important each foundation is relative to the other foundations, within each corpus. The values here are equal to 1 within each corpus.

![The Moral Foundations of SJWs Figure 3](https://i.imgur.com/Tofju33.png "Relative frequency of moral features")

Next I consider the degree to which the different moral foundations are correlated within each corpus. Such correlations might provide a somewhat richer sense of the moral priorities of each group, by showing whether each camp is more or less likely to link certain foundations. Figures 4 and 5 show visualizations of feature co-occurence matrices for SJWs and Berners, respectively. The size and color of each circle reflects the number of tweets in which one moral feature co-occurs with another moral feature.

![Feature co-occurence matrix for SJWs](https://i.imgur.com/Ygjtfbi.png "Feature co-occurence matrix for SJWs")

![Feature co-occurence matrix for Bernie Sanders supporters](https://i.imgur.com/xHlE5OK.png "Feature co-occurence matrix for Bernie Sanders supporters")

The main point of interest about the feature co-occurence matrices--the main way that SJWs differ from Berners in their linkage of moral concepts--is that Berners are inclined to link Loyalty and Harm more than SJWs.

### Discussion

Let's begin with certain observations the data, interestingly, do not support. SJWs do not appear especially concerned with Purity, as one common perception suggests. Also, it is somewhat surprising to me that Fairness is not more frequently invoked by Berners or SJWs. My understanding of Haidt's work is that left-wingers care the most about Harm and Fairness, so I guess I was expecting these to be the social justice foundations, and Fairness to be much more salient for both groups. After looking into the Moral Foundations dictionary, I think this pattern might be due to idiosyncratic word usage specific to left-wing radicalism, which confounds the dictionary definitions. For instance, the word "class" appears in the dictionary under "Authority (Virtue)" but in radical left circles I believe this word will more likely reflect the Fairness foundation. On the left today, "class" will generally refer more to economic inequality than cultural hierarchy.

There are a few, possibly meaningful and interpretable differences. It is interesting that Harm appears to loom marginally larger in the Berner camp, relative to SJWs. This is perhaps most interesting as a negative diagnostic: this would speak against the possibility that SJWs are hyper-concerned with Harm in particular--a possibility I have wondered about.

One difference that is consistent with my expectations is that, relative to Berners, SJWs are more likely to use general moralistic language outside of the five primary moral foundations. I find this quite interesting because I have often noted that one defining characteristic of what is SJW is what seems to be a particularly unconstrained linguistic *instrumentalism,* i.e., concepts of moral justice are deployed in wildly diverse and inconsistent ways to advance essentially non-moral interests of the speaker. I have written extensively on how [modern instrumental rationality](http://jmrphy.net/blog/2014/06/21/a-theory-of-ethically-biased-technological-change-toward-an-empirical-test-of-the-frankfurt-school/) short-circuits [the possibility of radical social change](http://jmrphy.net/blog/2017/01/27/mark-fisher-and-my-revolutionary-friends/). I have therefore thought for some time that perhaps SJWs are like the vanguard of a new, shamelessly instrumental version of the left-wing tradition: whereas normal people deploy language in self-serving ways to rationalize their moral intutions, and leftists generally deploy language that reflects their greater concern for Harm relative to conservatives, perhaps SJWism follows from the realization that moralism is a useful tool with or without any felt moral intuitions. This would be consistent with the finding here that SJWs are relatively more likely to use moralistic language outside of the five moral tastebuds Jonathan Haidt and colleagues have found to be primary across cultures. It would also be consistent with my writings on the detrimental pervasiveness of instrumentalism in left-wing activism. SJWism: left-wing moralism without foundations?

SJWs are somewhat less likely to invoke Authority and Loyalty, relative to Berners. Again we should be careful not to over-interpret what are quite small differences, but we can still reflect on possible interpretations--especially if the few small differences seem to make sense together. The lower degree of Authority emphasis is interesting because it speaks against the common description of the politically correct, SJW left as "authoritarian." The lower degree of Loyalty emphasis is interesting because it speaks against SJWism as an esoteric, cult-like sect--a perception outsiders sometimes have, given the highly idiosyncratic, specialist vocabulary associated with SJWism ("intersectionality," "safe spaces," etc.) There are no noticeable differences on Purity or Fairness.

With respect to the co-occurence matrices, I noted above that Berners are inclined to link Loyalty and Harm more than SJWs. I did not examine examples, but I wager this linkage reflects the democratic-socalist logic of "Capitalism harms people so we all have to stick together." Harm is bad but solidarity is good. Not only is solidarity good, but it can defeat the harms, etc. This makes sense in relation to the first graphs: Berners appear to deploy a somewhat richer web of moral concepts, whereas SJWs are more likely to use generalized moral terms in relatively unpatterned ways.

### Conclusion

Can the analyses presented here speak to the question of what is a social justice warrior?

By collecting a large writing sample of self-identified "social justice warriors" on Twitter (more than a million status updates from more than 500 different users), I have been able to provide one of the first empirical investigations of this semi-mythical, politically correct persona. In contemporary politics, the investigation of ideological micro-factions is uniquely difficult because of highly decentralized, rapidly changing, strategically motivated language use. I have leveraged the practice of ironic self-identification with pejorative monikers as a reasonable solution to the problem of drawing a fair sample. On the whole, linguistically observable differences in the moral psychology of self-identified SJWs and one alternative left-wing reference group (Bernie Sander supporters) are small but suggestive, and theoretically sensible. The small size of the differences could be due to the research design: given some degree of SJWism within the Bernie Sanders camp, the small differences we observe here might appear more clearly if we could draw a brighter line between groups. We could have compared SJWs to anti-SJWs but the hard and crucial test is whether SJWs are different from other leftists. We also noted at least one example of how the Moral Foundations dictionary might be confounded by idiosyncratic language use on the radical left, which also might have caused us to underestimate the differences between our groups. Obviously, more research is needed, beyond this short blog post, to know whether the differences identified here are real and significant.

That said, what is the takeaway here? I might hazard the following. On the whole, the language of SJWs appears somewhat less *morally constrained* than the alternative activist reference group. By *morally unconstrained* I refer to a cluster of small but linked observations that emerged from the data here. In some sense, this is likely just because SJWs are not an organized movement, as Bernie Sanders supporters are, to some degree. But this is interesting to learn anyway, precisely because SJWs are often interpreted as if they are an organized, morally coherent "movement" of some kind.  

First, SJWs are less morally constrained in the sense that they appear less driven by the primary, biologically coherent moral intuitions that have been observed consistently across cultures. Second, we also saw an "unconstrained" quality in the co-occurrence of moral features. For SJWs, the different moral foundations observed within their documents are less correlated. Whereas Berners are somewhat inclined to link Harm and Loyalty, this is less the case with SJWs. That SJWs invoke Loyalty less than Berners also seems to suggest that SJWs are relatively less likely to celebrate good "members" and less likely to condem betrayal. Now, we know that SJWs certainly criticize and attack in-group and out-group members if and when they violate certain taboos, but from this analysis we might infer that they do so in generalized, non-foundational terms. A former in-group member who uses racist language, for instance, is perhaps not primarily guilty of betraying the group or "movement;" they are simply deserving of negative moral descriptors, and SJWs will use any number of them in diverse ways. While I do not test for this here directly, these observations are at least consistent with what I have written elsewhere about the social justice warrior or SJW representing a shamelessly instrumental wing of left-wing activism. Whereas most leftists instrumentally rationalize their own moral intuitions, as all partisans do, online and in the real world, perhaps SJWs are the vanguard of a more sophisticated level of self-interested rationalization: to set flight from the constraints of their own moral intuitions, which otherwise constrain the self-interested language use of the typical modern partisan. We certainly could not justify such a bold generalization from the data presented in this short blog post, but this is what the data have me wondering.

Are there other questions it might be interesting to ask of this data, or a different data set? Let me know if you think of something and I will consider looking into it.

