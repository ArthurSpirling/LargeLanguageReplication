# Replication for Language Models: Non-Technical Explainer

Our paper has some technical parts, but the basic argument---and our evidence for that argument---is  simple. Here we give a non-technical account of our project, the questions we answer and how we go about doing that.  The intended audience is social scientists who are interested in "AI" for their research tasks, but who perhaps have less training in using language models than they would like. Below each section you will find a "too long, didn't read" summary. 

## 1. Replication: what it means and what it is for

At most top scholarly journals today, when a researcher has a paper accepted, they must deposit "replication" or "verification" materials.  For quantitative researchers, this is the data and code they used to produce the results in their paper.  Whole infrastructures have grown up to support this practice. These include the [Harvard Dataverse](https://dataverse.harvard.edu/) and software services like [Codeocean](https://codeocean.com/).  At some journals, the requirement is much more stringent than simply *providing* these items. At the [AJPS](https://ajps.org/ajps-verification-policy/), for example, a third party (i.e. not the authors themselves) will take those materials and they  

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
Large Language Models are as their name suggests. Working backwards they are: 
- **models** insofar as they have contain an implicit set of assumptions which is used to produce estimates for something.  
- **language models** insofar as the thing the model produces is language. Speaking very crudely, they can *predict* the best choice for the next word in a sequence.  So, for example, if the sequence was
 
> He sat down for lunch and ate a [_____]

the next word is more likely to be [sandwich] than [whole roast chicken] or [automobile]

- **large language models** insofar as they do this---that is, they model/generate language---by using billions of parameters.  This means that are very complicated, and need to "see" lots of training data---written language, essentially---so they know how to map what has been written so far in the sentence to what might optimally come next.

These (Large) Language Models (LMs) have proved remarkably helpful in social science research. It turns out they can do things like [code](https://arxiv.org/abs/2303.15056) manifestos into "left" or "right" ideologically camps.  They can also "converse" with subjects in experiments, and perhaps convince them of the wisdom of certain political positions. This save a lot of time and money.

### The Problem
So what is the problem?  First, as noted above, these models are inherently very complicated. They have lots of parameters that interact with each other in unexpected and unexplainable ways.  This is obviously different to something like a linear regression where the form of the equation is simple, and we know exactly how the variables are included to predict the outcome. For an LM, even if you have access to all the underlying parameter estimates themselves (called the "weights" of which there might be billions), you still won't necessarily be able to understand (in a deep sense) how changing some inputs "leads" to different outputs.  But it's worse than this because generally we do **not** have access to the underlying mechanics of the model.  

Second then, the problem is that the LMs most commonly used are *proprietary*.  For instance, products like chatGPT and GPT4 from OpenAI have this property. They are commercial and "closed" insofar as one cannot inspect *how* they work exactly. They contain a "sercret sauce"---the model and or the data they use, and or the techniques by which the parameters are updated---that is not available to those outside the organization.  One can, of course, experiment with the product such that we gain some understanding of what it is capable of and/or how it responds, but one can never know for sure.  It is truly a "black box" in that sense.  

But it gets worse even than this: we know that companies selling LMs routinely make changes to the product on the "back end".  This means that the model response to a given problem is not constant *by design*.  In our example above, the model might return the best answer as [steak] sometimes, and [pizza] another time. Users cannot download and keep specific *versions* of the LM, so whatever the company wants to change, maintain or retire at a given time is what is available.  

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

**tl;dr: interest in using large language models has exploded, but there analysis is generally impossible to exactly replicate. Journals do not seem aware of this problem or if they are, have not designed procredures that give us a way to tackle it**

## 3. A Typology of Replication Practices

Above we noted that "replication" is confusing because the same term is used with a different meaning in other fields.  But even *within* political science, there are what we call different *visions* of replication.  There are, to our mind, three main types of practices: 
1. **deterministic**.  Here the idea is that one can simply download the author's data and code, and run it again.  And one should see *exactly* the results that previous author presented. This is probably the most traditional or conventional understanding of replication. 
2. **stochastic**.  This is a more recent understanding of the term, and relies primarily on crowdsourcing. The idea, at least as [discussed in political science](https://kenbenoit.net/pdfs/Crowd_sourced_data_coding_APSR.pdf), is to reproduce the data *itself*.  So, on a given coding task, one asks a crowdworking service (like Amazon Mechanical Turk) to provide workers for simple component pieces of the project---say, placing a manifesto as conservative or liberal.
3. **rule-based**.  This is probably the oldest vision of replication, and mostly just means defining one's decisions simply and clearly.  For example, listing off what US states one considers to be in the `South` for dummy variable coding.

All these visions have strengths and weaknesses.  But we specifically think about the problem along two axes: first, in terms of whether *exact* replication is possible. Put simply: can I get exactly the same results as you if I follow this procedure? And the second axes is in terms of whether the replication method is *fragile* or not.  Put simply: can I depart from the particular method or code you used and expect to "replicate" what you did nonetheless?

This leads to the following typology of visions: 

<table>
 
   <tr>  
    <td> space </td>
    <td colspan="2">Eaxct Replication Possible</td>
  </tr>
  <tr>
    <td>1</td>
    <td>2</td>
    <td>3</td>
  </tr>

</table>






## 4. Experiments on LM Replication

## 5. Advice for Practitioners

