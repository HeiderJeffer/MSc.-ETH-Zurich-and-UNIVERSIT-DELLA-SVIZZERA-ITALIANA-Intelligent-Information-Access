<body>
<img src = "https://github-vistors-counter.onrender.com/github?username=https://github.com/HeiderJeffer/MSc.-ETH-Zurich-and-UNIVERSIT-DELLA-SVIZZERA-ITALIANA-Intelligent-Information-Access" alt = "Visitors-Counter"/>
</body>

**ETH Zurich and Università della Svizzera italiana**  
**Faculty of Computer Science**  
**MSc. in Artificial Intelligence**  

**Topic: Intelligent Information Access - Question Answering [2014]**  
**Author: Heider Jeffer**  

**Instructor: Mehdi Jazayeri**  
**Assistant: Sasa Nesic**  

**Instructor: Professor Fabio**  
**Assistant: Dr. Robert Gambera**

Let's break down the different sections of the provided research topic and write Python code to demonstrate each concept with an example.

### Visitors-Counter
We'll start by creating a simple visitors counter using Python. This counter will increment each time a visitor (simulated here) "visits" the website.

```python
class VisitorsCounter:
    def __init__(self):
        self.count = 0

    def visit(self):
        self.count += 1
        return self.count

# Example usage
counter = VisitorsCounter()
print(f"Visitor 1: {counter.visit()}")  # Visitor 1: 1
print(f"Visitor 2: {counter.visit()}")  # Visitor 2: 2
print(f"Visitor 3: {counter.visit()}")  # Visitor 3: 3
```

### Question Answering
We'll create a basic example using a predefined set of questions and answers. The system will answer questions based on keyword matching.

```python
class QuestionAnswering:
    def __init__(self):
        self.qa_pairs = {
            "How old is the president of the United States?": "As of 2024, the president is 81 years old.",
            "Who was the second person on the moon?": "Buzz Aldrin was the second person on the moon.",
            "When was the storming of the Bastille?": "The storming of the Bastille was on July 14, 1789."
        }

    def get_answer(self, question):
        return self.qa_pairs.get(question, "Sorry, I don't know the answer to that question.")

# Example usage
qa_system = QuestionAnswering()
print(qa_system.get_answer("How old is the president of the United States?"))
print(qa_system.get_answer("Who was the second person on the moon?"))
print(qa_system.get_answer("When was the storming of the Bastille?"))
print(qa_system.get_answer("What is the capital of France?"))  # Unknown question
```

### Information Retrieval and NLP Techniques
This example demonstrates a simple combination of IR and NLP using the `spaCy` library for named entity recognition (NER).

```python
import spacy

class IR_NLP_System:
    def __init__(self):
        self.documents = [
            "Joe Biden is the president of the United States.",
            "Buzz Aldrin was the second person to walk on the moon.",
            "The storming of the Bastille occurred on July 14, 1789."
        ]
        self.nlp = spacy.load("en_core_web_sm")

    def find_relevant_documents(self, query):
        return [doc for doc in self.documents if any(word in doc for word in query.split())]

    def extract_answer(self, documents, query):
        for doc in documents:
            nlp_doc = self.nlp(doc)
            for ent in nlp_doc.ents:
                if query.lower() in ent.text.lower():
                    return ent.text
        return "No relevant information found."

# Example usage
ir_nlp_system = IR_NLP_System()
query = "president of the United States"
docs = ir_nlp_system.find_relevant_documents(query)
answer = ir_nlp_system.extract_answer(docs, query)
print(f"Query: {query}\nAnswer: {answer}")
```

### Question Types and Answer Types
We'll create a function that identifies the type of question and the expected answer type using simple keyword detection.

```python
def identify_question_type(question):
    if "how far" in question.lower():
        return "FACTOID", "NUMBER"
    elif "list" in question.lower():
        return "LIST", "LIST"
    elif "who is" in question.lower():
        return "DEFINITION", "PERSON"
    elif "connection" in question.lower():
        return "RELATIONSHIP", "RELATIONSHIP"
    elif "largest" in question.lower():
        return "SUPERLATIVE", "PLACE"
    elif "is" in question.lower():
        return "YES OR NO", "BOOLEAN"
    elif "think" in question.lower():
        return "OPINION", "OPINION"
    elif "why" in question.lower():
        return "CAUSE AND EFFECT", "EXPLANATION"
    else:
        return "UNKNOWN", "UNKNOWN"

# Example usage
question = "Who is Vlad the Impaler?"
q_type, a_type = identify_question_type(question)
print(f"Question: {question}\nType: {q_type}\nAnswer Type: {a_type}")
```

### Question Focus and Topic
We'll create a function to extract the focus and topic from a question using the `spaCy` library.

```python
def extract_focus_and_topic(question):
    nlp = spacy.load("en_core_web_sm")
    doc = nlp(question)
    focus = [chunk.text for chunk in doc.noun_chunks if chunk.root.dep_ == "pobj"]
    topic = [ent.text for ent in doc.ents]
    return focus, topic

# Example usage
question = "What is the population of Russia?"
focus, topic = extract_focus_and_topic(question)
print(f"Question: {question}\nFocus: {focus}\nTopic: {topic}")
```

### Harder Questions and Web-based Question Answering
Simulating web-based question answering is complex, so we'll simplify it by using predefined responses and keyword matching.

```python
class WebBasedQA:
    def __init__(self):
        self.knowledge_base = {
            "Hannibal": "Hannibal was a Carthaginian general.",
            "Nebuchadnezzar": "Nebuchadnezzar was a king of Babylon."
        }

    def web_answer(self, question):
        for key in self.knowledge_base.keys():
            if key.lower() in question.lower():
                return self.knowledge_base[key]
        return "Sorry, I don't have information on that."

# Example usage
web_qa = WebBasedQA()
print(web_qa.web_answer("Who is Hannibal?"))
print(web_qa.web_answer("Who is Nebuchadnezzar?"))
```

### The TREC QA Task
This example demonstrates a simplified TREC QA task using predefined newspaper articles and a simple search mechanism.

```python
class TRECQA:
    def __init__(self):
        self.articles = [
            "One liter of milk contains approximately 640 calories.",
            "The Eiffel Tower is one of the most famous landmarks in Paris."
        ]

    def trec_qa(self, question):
        for article in self.articles:
            if any(word in article for word in question.split()):
                return article
        return "No relevant articles found."

# Example usage
trec_qa = TRECQA()
question = "How many calories are in one liter of milk?"
print(trec_qa.trec_qa(question))
```

### QA Test Collection
We’ll create a function that matches answers using string patterns.

```python
import re

def evaluate_answers(question, provided_answer):
    correct_patterns = {
        "How many calories are in one liter of milk?": [r"\b640\b", r"\bcalories\b"],
    }

    patterns = correct_patterns.get(question, [])
    for pattern in patterns:
        if re.search(pattern, provided_answer):
            return True
    return False

# Example usage
question = "How many calories are in one liter of milk?"
provided_answer = "One liter of milk contains approximately 640 calories."
print(evaluate_answers(question, provided_answer))  # True
```

These examples demonstrate the core actions described in the research topic, providing a basic implementation of each concept in Python.
