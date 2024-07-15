**MSc. ETH Zurich and Università della Svizzera italiana**  
**Faculty of Computer Science**  
**MSc. in Artificial Intelligence**  

**Topic: Intelligent Information Access - Question Answering [2014]**  
**Author: Heider Jeffer**  

**Instructor: Mehdi Jazayeri**  
**Assistant: Sasa Nesic**  

**Instructor: Professor Fabio**  
**Assistant: Dr. Robert Gambera**

---

### Visitors-Counter

#### Question Answering

Information retrieval (IR) techniques have proven effective at locating relevant documents within large collections based on user queries. However, users often seek brief answers to specific questions rather than entire documents. Examples of such queries include:

- "How old is the president of the United States?"
- "Who was the second person on the moon?"
- "When was the storming of the Bastille?"

Recent research projects have focused on developing computational techniques for answering these types of questions by extracting brief passages directly from texts. These projects aim to handle not only short, fact-based questions but also more complex queries requiring detailed answers, such as descriptions of events, object comparisons, discussions, and opinions.

The systems developed in these projects typically follow a standard structure. They generate a query from the user's question, perform IR to locate document segments likely to contain the answer, and pinpoint the most probable answer within these segments. The primary difference among these systems lies in their approach to pinpointing the answer.

A **pure IR approach** identifies segments that best match the query and returns them as the answer. The challenge here is to make the segments small enough to be concise answers while still being indexable.

A **pure Natural Language Processing (NLP) approach** matches the parsed and/or semantically interpreted questions against parsed and/or semantically interpreted sentences in candidate documents. The challenge is to perform parsing, interpretation, and matching quickly enough to be practical, given the large volumes of text.

Effectively answering short questions thus requires a combination of IR and NLP techniques. IR techniques narrow down the set of likely candidate segments, while NLP techniques handle the complexities of language, such as paraphrasing and inference.

#### Question Types

Questions can be categorized to facilitate different processing and answer formats. Examples include:

- **FACTOID:** "How far is it from Earth to the moon?"
- **LIST:** "List the names of chewing gums."
- **DEFINITION:** "Who is Vlad the Impaler?"
- **RELATIONSHIP:** "What is the connection between Trotsky and Lenin?"
- **SUPERLATIVE:** "What is the largest city on Earth?"
- **YES OR NO:** "Is Saddam Hussein alive?"
- **OPINION:** "What do most Americans think of gun control?"
- **CAUSE AND EFFECT:** "Why did Iraq invade Kuwait?"

#### Answer Types

The type of answer sought by the question can be classified as follows:

- **PERSON:** "Who?"
- **PLACE:** "Where?"
- **DATE:** "When?"
- **NUMBER:** "How many?"
- **EXPLANATION:** "Why?"
- **METHOD:** "How?"

These answer types are closely tied to the categories recognized by the system’s named entity recognizer.

#### Question Focus and Topic

- **Question Focus:** The specific property or entity being sought by the question. For example, in "What is the population of Russia?" the focus is "population."
- **Question Topic:** The broader object or event the question is about. For example, in "What is the height of the Tower of Babel?" the topic is "Tower of Babel."

#### Harder Questions

Answering factoid questions is relatively straightforward. More challenging tasks involve answering questions where the answers are fluid and require synthesizing information from multiple sources over time. Examples include:

- "Who is Hannibal?"
- "Who is Nebuchadnezzar?"

#### Web and Question Answering

In TREC (Text Retrieval Conference) and many commercial applications, retrieval is performed against a small, closed collection of texts. The diversity of expression on the web means that popular factoids are likely to be expressed in many different ways. Therefore, leveraging the web to match question formulations can be effective.

#### The TREC QA Task

QA encompasses a range of activities from simple yes/no responses to presenting complex results synthesized from multiple data sources. The TREC task focused on returning text snippets from a large corpus of newspaper articles in response to fact-based short answer questions such as "How many calories are in one liter of milk?"

The task was restricted to closed-class questions, but the subject domain was unconstrained as the document set comprised newspaper articles.

#### QA Test Collection

TREC has improved document retrieval performance by creating appropriate test collections for system development. Building such collections is time-consuming and expensive. One goal of the QA track was to create a reusable QA test collection. However, the judgment sets produced by assessors do not constitute a reusable test collection because the entire answer string is judged. Different QA runs rarely return exactly the same answer strings, making it difficult to determine automatically if differences are significant regarding answer correctness.

To approximate a solution, a set of Perl string-matching patterns was created from judged correct strings. An answer string matching any pattern for its question is marked correct, otherwise, it is marked incorrect.
