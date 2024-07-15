# <span class="smallcaps">ETH Zurich and UNIVERSITÀ DELLA SVIZZERA ITALIANA</span>

# FACULTY OF COMPUTER SCIENCE

# MSc. in Artificial Intelligence

# Topic: Intelligent Information Access - Question Answering \[2014\]

By Heider Jeffer

Instructor: Mehdi Jazayeri

Assistant: Sasa Nesic

Instructor: Professor Fabio

Assistant: Dr. Robert Gambera

 <body>
<img src = "https://github-vistors-counter.onrender.com/github?username=https://github.com/HeiderJeffer/Intelligent-Information-Access/edit/main/README.md" alt = "Visitors-Counter"/>
</body>




# Question Answering

IR techniques have proven quite successful at a location within large
collections of documents for the user query. Often, however, the user
wants not whole documents but brief answers to specific questions:

How old is the president of the United States? Who was the second person
on the moon? When was the storming of the Bastille? Recently several
search projects have investigated the computational techniques needed
for effective performance at this level of granularity focusing on the
questions that can be answered in few words taken as a passage directly
from a single text left aside, for the answering of longer more complex
answers, such as ( stories about events, description of objects, compare
and contracts discussions, arguments of opinions ,,, etc ).

The systems being built in these projects exhibit a fairly standard
structure, all create a query from the user's questions, perform IR with
query to locate (segments of ) documents likely to contain an answer,
and then pinpoint the most likely answer within candidate documents, the
most common difference of approach in the pinpointing.

A (pure IR) approach would segments that best match the query, and
return them as an answer, the change here would be (to make it so small
as to be just an answer-sized but still long enough to be indexable).

A (pure NLP) approach would be to match the parse and/or semantic
interpretation of the questions against the parse and/or semantic
interpretation of each sentence in the candidate answer containing
documents and return the best matches, the challenge here would be (to
perform parsing, interpretation and matching fast enough to be
practical, given argue volumes of the text to be handled ).

Answering short questions thus becomes a problem of finding the best
combination of word-level (IR) and syntactic/semantic-level (NLP)
techniques, the former to produce as short a set of likely candidate
segments as possible because languages allow paraphrasing and inference,
however, working out the details is not entirely straightforward.

# Question Type

An idiomatic categorization of questions for porpoises of distinguishing
between different processioning and/or answer formats, eg. TREC2003

1.  FACTOID: “How many far is it from Earth to the moon? ”

2.  LIST: “List the names of chewing gums “ 3.DEFINITION: “Who is Voled
    the impaler? “

3.  RELATIONSHIP: ”What is the connection between Trotsky & Lenin ?”

4.  SUPPER RELATIVE: “What is the largest city on the earth ?”

5.  YES OR NO: ”Is Saddam Hussein Alive ?”

6.  OPINION: “What do most Americans think of gun control ?”

7.  CAUSE OF EFFECT: “Why did Iraq invade Kuwait?”

# Answer Type

The classes of the object sought by the question, eg. :

1.  PERSON: ( “ From”, “Who?” )

2.  PLACES: ( “From”, “Where?” )

3.  DATE: (“From”, “When?” )

4.  NUMBER:( “From”,” How many ?” )

5.  EXPLANATION:(“From”,” Why?” )

6.  METHODS:(“From”, “How?”)

“Answer types are usually tied intimately to the classes recognized by
the system’s named entity recognizer.”

# Question Focus

The property or entity that is being sought by the question,e.g. “In
what state is the Code of Hammurabi ?”

“What is the population of Russia ?”

# Question Topic

The object (person, place, …. ), or event that the question is about,
the question might be about a property of the topic, which will be the
question focus, e.g. “What is the height of the Tower of Babel ?”, the
focus, Tower of Babel, is the topic.

# Harder Questions

Factoid questions answering is quite simple, a more interesting task is
one where the answers are fluid and depend on the fusion of the material
from disparate texts over time. e.g. Who is Hannibal? Who is
Nebuchadnezzar ?

# Web and Q.A

In TREC (the text retrieval conference) (and most commercial
applications), retrieval is performed against a smallish closed
collection of texts, the diversity of creativity in how people express
themselves necessitates all that works to bring the question and the
answer texts together, but on the Web popular factoids are likely to be
expressed in a very large number of different ways, at least of a few of
which will likely match the way the question was asked, so why not just
grep (or agree) the web using all price of the original question.

# The TREC QA TASK

QA covers a broad of activities from simple (yes/no) responses to
(true/false) questions to the (presentation) of complex results
synthesized. From multiple data sources, the specific task in the TREC
track was to return text snippets drawn from a large corpus of newspaper
articles in response to fact-based short answer questions such as “How
many calories are there in one liter of milk?

“The TREC task was restricted in that only closed-class questions were
used, yet the subject domain was essentially unconstrained since the
documents set were newspaper articles.

# Q.A Test Collection

The primary way TREC has been successful in improving documents
retrieval performance is by (creating appropriate test collections for
researchers to use when developing their systems ) while creating a
large collection can be (time- consuming) and expensive ,one of the Rey
goals of the QA track was to build a reusable QA test collection that is
to devise a means to evaluate a QA run that uses the same document and
question sets but not among the runs judged by the assumes
,unfortunately, the judgment sets produced by the assessors for the TREC
, QA track do not constitute a reusable test collection because the unit
that is judged is the entire answer string, different QA runs very
seldom return exactly the same the same answer strings and it’s quite
difficult to determine automatically whether the difference between a
new string and judged string is significant with respect to the
correctness of the answer , to an approximate solution to the problemist
created a set of Perl string-matching patterns from the set strings that
the seasons judged correct ,An answer string that matches any pattern
for its question is marked correct ,an answer string matches any pattern
for its questions is marked correct ,and marked in correct otherwise.
