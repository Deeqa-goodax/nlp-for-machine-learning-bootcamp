# Assignment 1 – NLP Foundations

## 1. What is Natural Language Processing?

Natural Language Processing (NLP) is a part of computer science and Artificial Intelligence (AI) that focuses on helping computers understand, process, and work with human languages. These languages can be written or spoken. We use NLP in many applications, including translation, chatbots, search engines, spam detection, and text summarization.

NLP, AI, and Machine Learning (ML) are connected, but they have different meanings. AI is the broad field of making computers perform tasks that normally require human intelligence. Machine Learning is one approach used in AI. It allows computers to learn patterns from examples instead of following only manually written rules. NLP focuses on language-related problems and can use machine learning, deep learning, or rule-based methods to solve them (Jurafsky & Martin, 2026).

**Example: SMS spam detection**

Think about receiving a text message that says, "Congratulations! You have won a free prize. Click here." An NLP system can process the message, and a machine-learning model can predict whether it is spam or a normal message.

To build this system, we first collect messages and label them as `spam` or `ham`. The model learns patterns from those examples. When a new message arrives, it uses what it learned to make a prediction. This can help users identify unwanted messages, although the model may sometimes make mistakes.

## 2. Corpus, Document, Token, Vocabulary, Feature, and Label

To understand these terms, I will use a small SMS spam-detection dataset as an example.

| Term | Meaning | Example |
|---|---|---|
| Corpus | A collection of text documents used for a particular task. | A dataset containing 1,000 SMS messages. |
| Document | One individual text item in the corpus. | "Win a free prize today!" |
| Token | A piece of text produced when a document is divided into smaller units. | `Win`, `a`, `free`, `prize`, `today`. |
| Vocabulary | All the unique tokens found in the text collection. | `win`, `free`, `prize`, `call`, `meeting`. |
| Feature | A numerical value that represents some information about a document and is used by a model. | The number of times the word `prize` appears in a message. |
| Label | The correct category assigned to a document in a supervised learning task. | `spam` or `ham`. |

For example, consider these two messages:

| Message | Label |
|---|---|
| "Please call me after class." | ham |
| "Win a free prize today!" | spam |

The complete collection of messages is the corpus, while each message is a document. When we divide a message into words, we get tokens. The vocabulary contains the unique words from the collection.

Features are the numerical information that the machine-learning model uses to learn. Labels provide the correct answers during training.

It is also important to understand that a feature and a label are not the same. A feature is information given to the model, while a label is the expected result that the model should learn to predict.

## 3. Four Common NLP Tasks

NLP can be used to solve different language problems. Four common tasks are:

| NLP Task | Input | Output | Example |
|---|---|---|---|
| Text classification | A complete message, review, or document. | A category or class. | Identifying whether an SMS is spam or normal. |
| Sequence labeling | A sentence divided into tokens. | A label for each token or text section. | Identifying `Amina` as a person and `Muqdisho` as a location. |
| Search and text similarity | A search query and a collection of documents. | Relevant documents or a similarity score. | Searching for phone battery problems and finding reviews about batteries that do not last long. |
| Text generation | A prompt or an existing text. | New text produced by the system. | Generating a summary of a long article. |

These tasks are different because they do not produce the same type of result. Text classification gives a category to a complete document. Sequence labeling identifies information within a sentence. Search finds relevant information, while text generation creates new text (Jurafsky & Martin, 2026).

## 4. Supervised and Unsupervised Learning in NLP

Supervised and unsupervised learning are two ways machine-learning systems can learn from data.

**Supervised learning**

Supervised learning uses data that already has labels. The model receives examples together with their correct answers and learns how to predict those answers.

For example, when building an SMS spam detector, we can collect messages and label each one as `spam` or `ham`. The model studies the messages and their labels. After training, it can predict the category of a message it has not seen before.

**Unsupervised learning**

Unsupervised learning works with data that does not have labels for the task. Instead of being given the correct answers, the algorithm looks for patterns or similarities in the data.

For example, we could collect customer reviews without marking them as positive or negative. A clustering algorithm could group reviews that use similar words or discuss similar subjects.

**Main difference:** Supervised learning uses labelled examples because it learns to predict known answers. Unsupervised learning does not require those labels because it tries to discover patterns or groups in the data (Manning, Raghavan, & Schütze, 2008).

## 5. Why Do We Convert Text into Numbers?

Most traditional machine-learning algorithms work with numerical data. They perform mathematical calculations to find patterns and make predictions. However, ordinary text consists of words and characters, so it usually needs to be converted into numbers before it can be used by these algorithms.

One simple method is called **Bag of Words (BoW)**.

Bag of Words creates a vocabulary from the text and represents each document using the number of times each vocabulary word appears. It focuses on word occurrence rather than sentence structure.

For example, suppose we have this vocabulary:

`[free, meeting, prize]`

We can represent two messages like this:

| Message | free | meeting | prize | Numerical representation |
|---|---:|---:|---:|---|
| "free prize" | 1 | 0 | 1 | [1, 0, 1] |
| "free meeting" | 1 | 1 | 0 | [1, 1, 0] |

The number `1` means that the word appears in the message, while `0` means it does not appear.

One weakness of Bag of Words is that it does not understand word order or the full meaning of a sentence. For example, "the dog chased the cat" and "the cat chased the dog" can have the same word counts even though they describe different situations.

It can also produce large numerical vectors when the vocabulary contains many words. More advanced methods, such as TF-IDF and word embeddings, can represent text in other ways and address some of these limitations (Manning et al., 2008; Jurafsky & Martin, 2026).

## 6. Challenges of NLP for Low-Resource Languages Such as Somali

A low-resource language is a language that has fewer digital resources available for developing language technologies. These resources may include large text datasets, labelled examples, dictionaries, and language-processing tools.

Somali is an important example to consider because developing reliable NLP applications requires data and tools that represent how people actually use the language.

Some major challenges include:

### 6.1 Limited labelled data

Many NLP models need examples that have been labelled by people. For example, a sentiment-analysis model needs messages labelled as positive, negative, or neutral.

When there are not enough labelled Somali examples, a model may struggle to learn different expressions and writing styles. It may perform well on the examples used during training but make mistakes when it receives new messages.

Collecting and labelling more Somali data requires time, resources, and people who understand the language. Research such as AfriSenti shows the importance of building datasets for African languages and supporting NLP research beyond widely resourced languages (Muhammad et al., 2023).

### 6.2 Spelling differences

People do not always write words in exactly the same way, especially when using social media or informal messages.

For example, someone might write `Soomaaliya`, while another person writes `Somalia`. A computer system may treat these as two different words even when they refer to the same place.

Text normalization can help reduce some spelling differences, but it needs to be done carefully so that important information is not lost.

### 6.3 Word forms and morphology

Somali words can change depending on grammatical information. For example, `nin` means "man", while `ninka` means "the man".

A basic NLP model may treat these as completely different words. This can make the vocabulary larger and make it harder for the model to recognize related word forms.

Stemming and lemmatization may help with this problem, but English-based tools should not automatically be used for Somali. We need suitable Somali language resources and should test whether the preprocessing method actually improves the results.

### 6.4 Dialects and mixed-language writing

Somali speakers may use different dialects, including Maxaa Tiri and Maay. If a dataset mostly contains one variety, a model may not work equally well for speakers who use another.

People also mix Somali and English in everyday communication. For example, someone might write `meeting-ka`. A system designed only for English may not process this expression correctly.

Because of these challenges, developers should collect data from different sources and speakers, pay attention to spelling and dialect differences, and test their models on examples that were not used during training. A high accuracy score alone does not prove that a model works well for everyone.

## 7. Case Study: Somali Dialect Identification Using Machine Learning and Deep Learning

One relevant example of NLP research involving Somali is the study by Gedi and colleagues (2025), titled *Somali Dialect Identification: A Low-Resource Benchmark for MAXAA TIRI and MAAY Using Machine and Deep Learning*.

This research is available as a Research Square preprint posted on July 22, 2025. It should therefore be understood as preliminary research rather than a peer-reviewed journal or conference publication.

**Task**

The researchers worked on identifying whether a Somali text sample belongs to the Maxaa Tiri or Maay dialect. The system receives a text sample and predicts its dialect category.

**Dataset**

The study reports using 3,011 text samples collected from sources such as social media and formal documents. The samples were labelled according to their dialect.

**Methods**

The researchers compared different approaches:

- Naive Bayes
- Support Vector Machine (SVM)
- Bidirectional Long Short-Term Memory (BiLSTM)

They also reported cross-source testing and a web-based interface as part of the study.

**Findings**

According to the reported results, Naive Bayes achieved 99.86% accuracy, while BiLSTM achieved 99.57%.

These results are interesting, but they should be considered carefully. The dataset contains 3,011 samples, and performance on other sources, regions, and writing styles would need to be examined. A model can sometimes learn patterns related to the source of a document instead of learning the dialect itself.

**Connection to the NLP tasks**

This study is an example of **text classification**. The input is a complete Somali text sample, and the output is a category such as Maxaa Tiri or Maay.

It is not sequence labeling because the model predicts one category for the complete sample rather than assigning a label to every word.

I chose this study because it focuses directly on Somali and demonstrates how machine-learning and deep-learning methods can be applied to a real language-processing problem.

## Conclusion

NLP helps computers work with human language and is used in applications such as spam detection, search, translation, and text generation. Before building an NLP model, it is important to understand the text data and concepts such as documents, tokens, vocabulary, features, and labels.

Text also needs to be represented numerically so that many machine-learning algorithms can process it. Simple methods such as Bag of Words are useful for learning the basics, although they have limitations because they do not capture word order or context.

For Somali NLP, challenges such as limited labelled data, spelling differences, word forms, dialects, and mixed-language writing need special attention. The Somali dialect-identification study provides an example of how these challenges can be investigated through practical NLP research.

## References

1. Gedi, A. A., Ahmed, Y. M., Mohamed, S. A., Yusuf, Y. A., & Ebdiyow, A. U. (2025). *Somali Dialect Identification: A Low-Resource Benchmark for MAXAA TIRI and MAAY Using Machine and Deep Learning*. Research Square preprint, posted July 22, 2025. https://doi.org/10.21203/rs.3.rs-7163778/v1

2. Jurafsky, D., & Martin, J. H. (2026). *Speech and Language Processing: An Introduction to Natural Language Processing, Computational Linguistics, and Speech Recognition with Language Models* (3rd ed., online manuscript released August 19, 2026). https://web.stanford.edu/~jurafsky/slp3/

3. Manning, C. D., Raghavan, P., & Schütze, H. (2008). *Introduction to Information Retrieval*. Cambridge University Press. https://nlp.stanford.edu/IR-book/

4. Muhammad, S. H., Abdulmumin, I., Ayele, A. A., Ousidhoum, N., Adelani, D. I., Yimam, S. M., Ahmad, I. S., Beloucif, M., Mohammad, S. M., Ruder, S., Hourrane, O., Brazdil, P., Jorge, A., Ali, F. D. M. A., David, D., Osei, S., Bello, B. S., Ibrahim, F., Gwadabe, T., Rutunda, S., Belay, T., Messelle, W. B., Balcha, H. B., Chala, S. A., Gebremichael, H. T., Opoku, B., & Arthur, S. (2023). AfriSenti: A Twitter Sentiment Analysis Benchmark for African Languages. *Proceedings of the 2023 Conference on Empirical Methods in Natural Language Processing*, 13968–13981. https://doi.org/10.18653/v1/2023.emnlp-main.862
