# Overton data science test

## Introduction

*Imagine that you're Overton's latest data science hire (congrats!). You've just had a call with a university that we're working with in the UK: they've spotted a funding opportunity and need to quickly demonstrate how and where they're influenced policy. The good news is that they know Overton has the data they need to show this, the bad news is that the deadline to apply is at the end of the week. What can you do in the next 90 minutes to help them?*

Thanks for agreeing to run through this exercise! 

During it you'll be taking a real life CSV dataset representing government (and related organization) documents that refer to work done at a particular UK university. You'll analyze it in a few different ways and then visualize the results. 

You should be able to finish the exercise in about an hour and a half. After you've submitted the test we'll schedule a call where you'll have the opportunity to walk us through it.

Please don't spend too much longer than 90 minutes on this. The aim _isn't_ for you to produce perfect, production ready code; rather it's for you to be able to see some actual data from Overton and to warm up some techniques to analyze it. We're interested in your thinking as much as the results and this test gives us lots of jumping off points for chatting later, when you walk us through your work.

There are three parts to the exercise: producing some tables, producing a bar graph and doing some topic modelling.

There are some bonus tasks and questions in each part: we're _not_ expecting you to do all or many of these! But once you've finished all three parts and have time left feel free to go back and tackle a few of them.

## Getting started

*After talking it through with the rest of the team you decide to:*

1. *Create some data tables showing which countries, sources and types of policy document appear in the dataset*
2. *Plot the number of policy documents published in each year in a bar chart*
3. *Do some topic modelling to show what areas the university is most engaged in*

We'd prefer you use python in this exercise but R is also fine. You can use a notebook or command line scripts, whichever you find easiest. You can also use any tools & libraries you like: we suggest spacy, nltk, gensim and plotly.

Make sure that your environment is set up correctly and that you're able to run and edit your code on the laptop or computer you'll use when you have the follow-up call with us later on.

### The dataset

Overton collects documents relating to government policy from around the web (these are the *"policy documents"*). Each policy document has some metadata describing where we found it (the *"policy source"*), what country it's from, when it was published and so on.

Our platform analyzes the full text of each policy document to find where they mention different universities, think tanks and other organizations. This means we're able to quickly find and show documents of interest to our users.

We've queried the main database for you already and you'll find a CSV file representing policy documents relating to the client here:

```
data/data_northumbria.csv
```

Each row represents a single policy document. The row format is:

Column | Description
---- | ----
0 | **policy_document_id** : Overton assigns each policy document a unique identifier
1 | **title** : This is the title of the policy document.
2 | **description** : This is a short description of the policy document, if we have one.
3 | **date** : This is the publication date of the policy document, in YYYY-MM-DD format.
4 | **non-english language flag** : This is "f" if the policy document is in English and "t" otherwise.
5 | **policy source name** : The name of the organization that produced this document
6 | **policy source country** : The country of that organization
7 | **policy source type** : The type of organization that produced this document
8 | **policy source subtype** : The subtype - if one exists - of the organization
9 | **tags** : This is a pipe (\|) delimited list of tags that we've derived from the full text of the document

There isn't a header row in the CSV file.

The **title** and **description** fields are not guaranteed to be in English, though if the **non-English language flag** is set to "f" then you should assume it is.

The data may be messy: in particular the **description** field may contain non-UTF8 characters. If you encounter these you can skip the row.

If you've got any questions about the dataset please email us.

## Your tasks

### PART 1: Pulling out some data into tables

Using the data_northumbria CSV file, produce output showing:

* The top ten countries that the policy documents are from
* The top ten source names and their document counts
* All of the types (& their subtypes) of the policy document sources, and their document counts

You can output text, HTML tables or anything else you like as long as it's reproducible with your code (i.e. they should be generated by your code, not written by hand)

### PART 2: Plotting policy documents by year

Produce a bar chart showing the number of publications in the dataset by year, from 2011 to 2021.

This could be a graphic file, an HTML page or anything else you like as long as it's reproducible with your code.

#### Bonus tasks and questions (completely optional)

1. What other visualizations might you include?
2. How could you mix in the data tables from the previous section with graphs, and deliver both to the client?

### PART 3: Topic modelling

Perform topic modelling twice on the documents in the CSV file. Use LDA for this.

In your first run:

* For each English language document, take their **title** and **description** and tokenize this
* Look for 5 topics
* Display the topics: show five or six representative words for each
* Find and show up to five document titles associated with each topic

In your second run:

* Use the **tags** in each row (both English and non-English) as tokens
* Look for 5 topics
* Display the topics: show five or six representative tags for each
* Find and show up to five document titles associated with each topic

Note that the tags field is a string containing individual tags (which are not necessarily single words) separated by the pipe ("\|") character.

#### Pointers

* [Topic modelling in Python](https://towardsdatascience.com/topic-modelling-in-python-with-nltk-and-gensim-4ef03213cd21)
* [Topic modelling in R](https://towardsdatascience.com/beginners-guide-to-lda-topic-modelling-with-r-e57a5a8e7a25)
* [More in-depth post on topic modelling in Python](https://www.machinelearningplus.com/nlp/topic-modeling-gensim-python/)

#### Bonus tasks and questions (completely optional)

Assume you have access to the entire Overton database, which is able to give you baseline data on tag and token frequencies etc.

1. How would you visualize these topics and their relation to each other for the client?
2. How would you find the optimal number of topics to look for?
3. How might you add to, change or clean-up the input or tokenization process to improve the topics found in the first run?
4. How might you pre-process the tags to improve topics in the second run? 
5. How might you assign sensible, human readable names to each topic?
6. How would you handle non-English texts?
7. Was topic modelling the best approach here? How else could we have shown the range of policy areas in which the university is engaged?

### Questions to think about for when we chat

1. What other analyses, visualizations or narratives you could give the client that might help them understand where they've influenced policy in some way?
2. If the university wanted to identify similar organizations - other universities with a similar policy footprint - how would you go about doing it?
3. We used a third party service to automatically create tags (which correspond to Wikipedia pages) from the fulltext of policy documents. If we were to do this in-house what would your approach be?

## Submitting your code

Well done! 

If you've prepared a notebook or other interactive approach, please share the link with us.

If you've written command line scripts please upload your code to Github and either make the repository public or give read access to "mrstew" then send us the link.

If you're using the repository please make sure you include any output files (the graph, the tables, the topics...) as well as the code used to generate them.