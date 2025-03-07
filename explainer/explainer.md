# Replication for Language Models: Non-Technical Explainer

Our paper has some technical parts, but the basic argument---and our evidence for that argument---is  simple. Here we give a non-technical account of our project, the questions we answer and how we go about doing that.  The intended audience is social scientists who are interested in "AI" for their research tasks, but who perhaps have less training in using language models than they would like. Below each section you will find a "too long, didn't read" summary. If you want something even shorter, here is the bottom line:

1. Replication---the ability to reproduce a previous author's findings *exactly*, given their materials---is vital for scientific integrity.
2. Almost all Large Language Model (LM) work currently being published is not held to this standard, and does not meet it.
3. To the extent that LM replication is comparable to other visions of that term in political science, the LM case has special combined weaknesses that should make us especially nervous
4. This matters: LMs are not consistent over time, even on *exactly* the same tasks---so many findings cannot be replicated even on their "own terms"
5. Researchers need to get serious about what replication for LMs means.

## 1. Replication: what it means and what it is for

At most top scholarly journals today, when a researcher has a paper accepted, they must deposit "replication" or "verification" materials.  For quantitative researchers, this is the data and code they used to produce the results in their paper.  Whole infrastructures have grown up to support this practice. These include the [Harvard Dataverse](https://dataverse.harvard.edu/) and software services like [Codeocean](https://codeocean.com/).  At some journals, the requirement is much more stringent than simply *providing* these items. At the [AJPS](https://ajps.org/ajps-verification-policy/) for example, a third party (i.e. not the authors or the journal) will take those materials and they  

> will be verified to confirm that they do, in fact, reproduce the analytic results reported in the article. Publication in the American Journal of Political Science is contingent upon provision of complete verification materials and successful verification of their content.

At a high level, such practices contribute to "research transparency".  This is the idea that we can read what the authors said they did, and check they *really* did it.  In a narrow sense, it prevents fraud or terrible errors.  But it is much broader in spirit: it allows future researchers a useful starting point for building on prior efforts, including checking how different assumptions or methods might affect the robustness of the published results. It also encourages authors depositing such materials to "get it right" first time (i.e. to double-check their code actually does what they say it does). 

At this point, it's helpful to clarify a very confusing definitional issue.  In our paper, and in this explainer, we are focused on **replication** which we define as the idea that

> a scholar can take the materials from a given paper—its exact data, programming code, information on the operating system and environment used—and produce the same results as were reported in *that* paper.

This is how grad students in political science are [taught](https://gking.harvard.edu/files/gking/files/replication.pdf) to use the term.  

This is different to *reproducibility* which, as we use that term, means taking the same broad procedures of the original study to a new or independent dataset and seeing to what extent the original findings hold up.  The problem is that different fields use these terms in exactly opposite ways. So when, for example colleagues discuss the "[replication crisis](https://www.psychologytoday.com/us/basics/replication-crisis)" in Psychology, they are concerned about the inability to "reproduce" (in our terms) major results from the past today.

**tl;dr: replication---the idea that you can take published work's data and code and verify you get the same result as the original author---is a vital part of today's quantitative social science practice. It is central to research transparency.**

## 2. The state of replication for Language Models (isn't good)

Given that we have norms around replication, and we provide both carrots (free data hosting) and sticks (journals require verification pre-publication), what is the problem to be solved? In brief it is that there has been an explosion of interest and use of a new technology called "[Large Language Models](https://en.wikipedia.org/wiki/Large_language_model)" in social science, but without commensurate attention to the complications that these methods create for replication.  Consequently, in our view, almost nothing using these models and being published today is "replicable" to anything like the standard we have come to demand and expect.

### Large Language Models
Large Language Models are as their name suggests. Working backwards they are... 
- **models** insofar as they have contain an implicit set of assumptions that is used to produce estimates for something.  
- **language models** insofar as the thing the model produces is language. Speaking very crudely, they can *predict* the best choice for the next word in a sequence.  So, for example, if the sequence was
 
> He sat down for lunch and ate a [_____]

the next word is more likely to be [`sandwich`] than [`whole roast chicken`] or [`automobile`]

- **large language models** insofar as they do this---that is, they model/generate language---by using billions of parameters.  This means they are very complicated, and need to "see" lots of training data---written language, essentially---so they know how to map what has been written so far in the sentence to what might optimally come next.

These (Large) Language Models (LMs) have proved remarkably helpful in social science research. It turns out they can do things like [code](https://arxiv.org/abs/2303.15056) manifestos into "left" or "right" ideologically camps.  They can also "converse" with subjects in experiments, and perhaps [help](https://www.pnas.org/doi/10.1073/pnas.2311627120) [convince them](https://www.tandfonline.com/doi/full/10.1080/00323187.2024.2335471) of the wisdom of certain political positions. This saves a lot of time and money.

### The Problem
So what is the problem?  

First, as noted above, these models are inherently very complicated. They have lots of parameters that interact with each other in unexpected and unexplainable ways. The figure to the right gives a basic "[transformer](https://en.wikipedia.org/wiki/Transformer_(deep_learning_architecture))" schematic. <img align="right" src="transformer.png" width=330 title="Basic transformer setup">
This is obviously different to something like a linear regression where the form of the equation is simple, and we know exactly how the variables are included to predict the outcome. For an LM, even if you have access to all the underlying parameter estimates themselves (called the "weights" of which there might be billions), you still won't necessarily be able to understand (in a deep sense) how changing some inputs "leads" to different outputs.  But it's worse than this because generally we do **not** have access to the underlying mechanics of the model.  

Second then, the problem is that the LMs most commonly used are *proprietary*.  For instance, products like chatGPT and GPT4 from OpenAI have this property. They are commercial and "closed" insofar as one cannot inspect *how* they work exactly. They contain a "secret sauce"---the model and or the data they use, and or the techniques by which the parameters are updated---that is not available to those outside the organization.  One can, of course, experiment with the product such that we gain some understanding of what it is capable of and/or how it responds, but one can never know for sure.  It is truly a "black box" in that sense.  

But it gets worse even than this: we know that companies selling LMs routinely [make](https://www.theverge.com/2024/2/21/24079047/chatgpt-malfunction-hallucination-responses-openai) [changes](https://www.nbcnews.com/tech/tech-news/google-making-changes-gemini-ai-portrayed-people-color-inaccurately-rcna140007) to the product on the "back end".  This means that the model response to a given problem is not constant *by design*.  In our example above, the model might return the best answer as [`steak`] sometimes, and [`pizza`] another time. Users cannot download and keep specific *versions* of the LM, so whatever the company wants to change, maintain or retire at a given time is what is available.  

### Replication State of the Art

This matters because political scientists routinely report their "prompts"---the instructions they gave to a specific LM on a specific day---as their only replication materials.  For example, [Gilardi et al](https://arxiv.org/pdf/2303.15056) (S1.4, Task 2) report the following for a particular task in which an LM must decide if a tweet is (politically) relevant or not:

```
For each tweet in the sample, follow these instructions:
1. Carefully read the text of the tweet, paying close attention to details.
2. Classify the tweet as either relevant (1) or irrelevant (0)
Tweets should be coded as RELEVANT if they include POLITICAL CONTENT, as defined above.
Tweets should be coded as IRRELEVANT if they do NOT include POLITICAL CONTENT, as defined above
```

But we have no way of knowing whether this prompt will return what the original authors got when they applied it (now) over a year ago.  To be clear: this is not the authors' fault: there is simply no way they can archive a given "copy" of GPT for someone else to use in the exact same way they did.  We checked a whole slew of journals on this point, and none had (more) specific LM replication instructions.  It is true that there are [some products](https://arxiv.org/abs/2402.10379) that will allow one to take a type of "snapshot" of what one did exactly (i.e. what model, what specification) on a given run.  But this is not the same as being able to serve up that underlying model itself. 

Readers may reasonably respond that perhaps this doesn't matter---that running the same prompt today may, as an empirical matter, return the same results.  We will show that's false. Readers may also argue that such random variation is not unhead of in political science.  For example, expert coders (or undergraduates), often show considerable random differences over time and cannot be "versioned" either.  We think that is a false analogy too, and we'll explain why below. 

**tl;dr: interest in using large language models has exploded, but their analysis is generally impossible to exactly replicate. Journals do not seem aware of this problem or if they are, have not designed procedures that give us a way to tackle it**

## 3. A Typology of Replication Practices

Above we noted that "replication" is confusing because the same term is used with a different meaning in other fields.  But even *within* political science, there are what we call different *visions* of replication.  There are, to our mind, three main types of practices: 
1. **deterministic**.  Here the idea is that one can simply download the author's data and code, and run it again.  And one should see *exactly* the results that previous author presented. This is probably the most traditional or conventional understanding of replication. Per our comments above, it is what [King (1995)](https://gking.harvard.edu/sites/scholar.harvard.edu/files/gking/files/replication.pdf) calls "replication"
2. **stochastic**.  This is a more recent understanding of the term, and relies primarily on crowdsourcing. The idea, at least as [discussed in political science](https://kenbenoit.net/pdfs/Crowd_sourced_data_coding_APSR.pdf), is to reproduce the data *itself*.  So, on a given coding task, one asks a crowdworking service (like Amazon Mechanical Turk) to provide workers for simple component pieces of the project---say, placing a manifesto on a conservative to liberal spectrum. Note that crowdworkers do not have *zero* variability when doing tasks over time but the variability is nonetheless small.  And to the extent that replication ever fails, it does so in predictable ways (e.g. the workers are given a task that is too hard). 
3. **rule-based**.  This is probably the oldest vision of replication, and mostly just means defining one's decisions simply and clearly.  For example, listing off what US states one considers to be in the `South` for dummy variable coding.

All these visions have strengths and weaknesses.  But we specifically think about the problem along two axes: first, in terms of whether *exact* replication is possible. Put simply: can I get exactly the same results as you if I follow this procedure? And the second axes is in terms of whether the replication method is *fragile* or not.  Put simply: can I depart from the particular method or code you used and expect to "replicate" what you did nonetheless?

This leads to the following typology of visions: 

<table>
 
   <tr>  
    <td>  </td>
    <td colspan="2"> <b>Exact Replication Possible?</b>  </td>
  </tr>
  <tr>
    <td> </td>
    <td> <b>No</b> </td>
    <td> <b>Yes</b> </td>
  </tr>
 <tr>
    <td><b>Fragile</b> </td>
    <td> Language Models </td>
    <td> Deterministic Replication </td>
 </tr>
 <tr>
      <td><b>Robust</b></td>
    <td> Stochastic Replication </td>
    <td> Rule-based </td>
  </tr>
 
</table>

The point we make in the paper is that LMs (top left) have the weaknesses of other replication methods, without their strengths.  For instance, like deterministic "code + data" replication they are *fragile*.  That is, the language model must be exactly the same between runs, and as we noted this is very hard to achieve especially for proprietary systems.  But LMs also do not facilitate exact replication even if you use what is nominally the same product.  This is partly due to the fact that the models are inherently variable, but also because there are back-end changes by the programming teams that serve them.  So in this sense, they are like crowdsourcing methods, but without the relative low dependence on a particular program or system that such methods usually show. And unlike crowdsourcing, predicting how and when the LM will catestrophically fail ([hullicinate](https://en.wikipedia.org/wiki/Hallucination_(artificial_intelligence)) or just not function) is very hard. 

Of course, how much of an issue this all is in practice is debatable.  In the next section, we'll show it's troubling, and often severely so. 

**tl;dr: LMs have unique and troubling combinations of weaknesses when it comes to replication.  They are not "just like "human coders".**


## 4. Experiments on LM Replication
The empirical core of our paper is seeing whether, in fact, we should worry about the issues we raised above.  The basic design was to...

1. **do multiple common coding tasks**
- these include coding manifestos, and recording details from news stories
- some tasks are *static* meaning the data to be coded (like the documents or events) is *exactly the same* each time. Some tasks are *dynamic* meaning they are a random sample from a larger dataset.  
2. **using several different Language Models**
- we used two proprietary models, [Gemini](https://gemini.google.com/) and [GPT4](https://openai.com/index/gpt-4/); and one open model, [LLaMa 2](https://www.llama.com/llama2/)
3. **over a relatively long time period**
- we repeated the same tasks once a month for six months (so far)
4. **we do all the steps above but for crowdworkers too**
- they do the same tasks, over the same period. 

Then, we compare the models and the crowd in terms of their performance and performance *variance*.  This latter point is important: while we do care about how well the crowd and the models can do the tasks, we also care about how much the answers they give *vary* between runs.  Put crudely, the more they vary the less "replicable" the results are.  Note that we would expect and hope that the *static* tasks in particular return very consistent results over time. 

### Results

What did we find?  Very briefly: 
<img align="right" src="variance.jpg" width=450 title="LM Variance Results">

- crowdworkers are quite accurate, but not as accurate as the top performing LMs.  This is inline with other work on coding problems.
- crowdworkers are much *lower variance* on average than LMs. That is, they tend to not move around too much in terms of performance quality.
- some LMs have much higher variance than others.  For example, GPT generally exhibits higher variance than LLaMA, and Gemini is often more variable than both.
- the lowest variance occurs for the open-LLM (LLaMA) on the static task.  In fact, the results have essentially zero variance, and are "perfectly" replicable in that sense.

The figure makes these points.  When the dots are to the left, variance is low.  To the right, variance is higher.  The rows just list the various combinations of tasks, types and models being tried for that iteration. 

Does the way that LMs code things matter for downstream results?  In a sense, it must do: if LMs measure something "differently" to other coding options, this will affect subsequent regressions using those items.  This is what we see, albeit our example requires some nuance.  We used GPT to code a bunch of texts on a populism scale; we used crowdworkers to do the same thing.  This populism measure was then the dependent variable in a regression---the specification for which we took from a [published paper](https://journals.sagepub.com/doi/full/10.1177/00491241221122317). We did many draws of diffrent parts of the data to  build up a sort of simulated sampling distribution of what might happen in some "general" sense outside this specific study. 

For this problem, we noted that the GPT codings were often not very accurate; specifically, GPT seemed to "over" code speeches as populist that were not.  This sort of systematic (i.e. non-random) measurement error typically results in biased coefficients.  And that's what we observe when we plot (see figure on the right) the implied sampling distribution (the possible values of the relevant estimated <em>&beta;</em>s).  In particular, it is quite close to zero (on average) for GPT.  What about the crowdsourced comparison?  It has higher variance, but the mean is much further from zero.  And in fact, it ends up with an estimated <em>&beta;</em> of around $-1.5$ (on average).  Ths is more or less what the original authors reported.  Perhaps unsurprisingly, the distribution of simulated *p*-values tends to be different too. 

<img align="right" src="downstream.jpg" width=450 title="LM Downstream Problems">

A final point in this section is that one of the LMs, Gemini, simply would not work much of the time.  To say the results are therefore 'non-replicable' is an understatement---one cannot even use the same technique. 

**tl;dr: the variance for LMs, especially proprietary ones, is high. Some tasks with some LMs cannot be replicated at all.  Open models with offline versioning are the exception**

## 5. Advice for Practitioners
What follows from all this?  We have five suggestions:


1. **Take replication seriously** Researchers and journals need to be aware that replication matters for LM work as much as anything else.  Don't allow a new/worse "replication crisis" to emerge. 
2. **Consider open models that allow off-line versioning**.  LLaMA wasn't always the best performer, but it was very good and allowed almost *perfect* replication.  Consider this when coding in your own work.
3. **Justify closed models if they must be used**.  Closed models are non-transparent, so [explain](https://www.nature.com/articles/s43588-023-00585-1.epdf?sharing_token=MzweryQ216mZhRFFWcZPM9RgN0jAjWel9jnR3ZoTv0PqiD0oRUy182GqZiF90Sm6fQqacfY_AtePs54IZ4YiSsQos1QKJefRb3mjojyQVC83mDj3jqR0B80bdJeedFcrZq9KIgpieI_OR_d3bhiCAxpOsZD3eZ1MnXWnFi6Uweg%3D) why we must pay this cost in your case. 
4. **Work in an “anti-fragile” way**. If you must use closed models, try to reduce the variances in their outputs. Setting temperatures may help, but this is no panacea. 
5. **Replicate Your Work**. Researchers should run their own routines multiple times, preferable over multiple days or weeks or months and be honest about the variance they observe.
