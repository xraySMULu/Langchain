# Langchain Examples
[![forthebadge made-with-python](http://ForTheBadge.com/images/badges/made-with-python.svg)](https://www.python.org/)
[![made-with-VS-Code](https://img.shields.io/badge/Visual%20Studio%20Code-007ACC?logo=visualstudiocode&logoColor=fff&style=plastic)](https://code.visualstudio.com/)

## What is Lang Chain?
Lang Chain provides AI developers with tools to connect language models with external data sources. LLMs are large deep-learning models pre-trained on large amounts of data that can generate responses to user queries by answering questions or creating images from text-based prompts.

## What is the Prompt?
A language model prompt is a collection of user-provided instructions or input that guides the model’s response, assisting it in understanding the context and producing appropriate and meaningful output, such as answering questions, completing phrases, or engaging in a conversation.

## What is a Vector Store?
Compared to traditional databases, vector stores handle high-dimensional vector data more efficiently. They excel at finding similar data points, scale effortlessly to handle large amounts of data, and are compatible with common machine learning tools. This makes them invaluable assets for tasks such as recommendation systems, text analysis, chatbots, and more. One of the most frequent methods for storing and searching unstructured data is to embed it and save the generated embedding vectors, followed by embedding the unstructured query and retrieving the embedding vectors that are ’most similar’ to the embedded query. A vector store stores embedded data and performs vector searches for you.

## Vector Databases
Lang Chain supports async operations on vector stores. All the methods might be called using their packages.
* Chroma
Chroma is an open-source embedding database. Chroma makes it simple to create LLM apps by making knowledge, facts, and abilities connected for LLMs.
* FAISS
Facebook AI Similarity Search (FAISS) is a library for efficient similarity search. It offers methods for searching sets of vectors of any size, including ones that may not fit in RAM. It also includes support code for evaluation and parameter adjustment.

There is a variety of vector store types available, offering functionalities to suit different needs. You can explore more vector store types and their capabilities at https://python.langchain.com/docs/integrations/vectorstores/

## What Are Chains in AI Text Generation in LangChain?
Chains refer to sequences of calls — whether to an LLM, a tool, or a data preprocessing step. In Lang Chain, a chain functions similar to a necklace, where each bead contributes a unique element to the overall structure. Chains have various components that the Lang Chain library offers, making our work with LLMs easier and more efficient.
* Why do we need chains?
Chains combine LLMs with other components, creating applications by executing a sequence of functions.
There are several types of chains, each designed to deal with certain problems and make specific use of language models’ strengths. This section looks at frequently utilized LLM chain types.
* Components of chains in LangChain
    * LLMs (Large Language Models): These are core processing units used for tasks like generation, translation, summarization, and question answering.
    * Memory: Stores information between nodes or across chain runs for context continuity.
    * Tools: Perform specific tasks like summarization, sentiment analysis, or data retrieval.
    * Agents: Act as decision-makers, choosing which tools to use based on input and context.
    * Data Retrieval Components: Fetch data from internal databases, external APIs, or local files.
* Types of Chains?
    * Conversational Retrieval Chain
    It is a type of chain that responds to a query by retrieving documents related to the query. This is only one of many ways that Retrieval-Augmented Generation may be done. However, in addition to responding to your most recent question, it will use the conversation history to enhance the RAG’s quality.
    * LLM Chain
    A PromptTemplate along with a language model form an LLMChain. The input key values and, if available, memory key values are used to prepare the prompt template. The formatted string is then passed to LLM, and the LLM output is returned.
    * Retrieval QA
    The process of extracting the most relevant documents from a significant amount of data is known as retrieval. In question-answering (QA), a system receives a question and is required to provide the closet response.
    * Stuff Documents Chain
    This chain starts by merging a collection of documents into a single string. It does this by using document_prompt to format each document into a string and document_separator for connecting them all together. The new string is then added to the inputs with the variable name set. The llm_chain receives those inputs. Additionally, there are other types of document chains such as MapReduceChain, ReduceDocumentsChain, RefineDocumentsChain, and various other chain types.
## Retrieval-Augmented Generative Models(RAG)
Let’s see how to create a “retrieval-augmented generation” chain by integrating a retrieval step into an LLM and prompt. Retrieval Augmented Generation (RAG) is the process of bringing the relevant data and inserting it into the model prompt.

* RAG consists of two main parts:
    * Indexing: A pipeline for ingesting and indexing data from a source. Usually, this takes place offline.
    * Generation and retrieval: the real RAG chain, which receives the user query at runtime, extracts relevant data from the index, and then provides it to the model.
        * Indexing :
        Load: Our data must first be loaded. To do this, DocumentLoaders are used.
        Split: Text splitters divide long documents into smaller sections. Since large chunks are more difficult to search through and won’t fit in a model’s limited context window, this is helpful for both indexing data and feeding it into a model.
        Store: In order to be able to search over our splits later, we need a place to index and store them. Embeddings and VectorStore are frequently used for this.
        * Retrieval and generation :
        Retrieve: A Retriever is used to retrieve relevant data from memory based on user input.
        Generate: By utilizing a prompt that contains both the question and the returned data, LLM generates a response.

## Enhancing Performance using memory
* A conversational interface is found in most LLM programs. Being able to reference information that was introduced previously in the discussion is crucial. A conversational system should at least be able to open a window with previous messages directly. In order to do tasks like maintaining data on entities and their relationships, a more sophisticated system will require an updating model.
* We refer to this ability to keep details of previous interactions as “memory”. Lots of utilities for adding a system’s memory are available from LangChain. These tools can be smoothly integrated into a chain or utilized alone.
* The two fundamental functions of a memory system are writing and reading. Keep in mind that each chain specifies some basic execution logic that requires specific inputs. While some of these inputs may originate from memory, others may come directly from the user.
* Memory Types
There are many different types of memory. They are all helpful in different situations and have different parameters and return types.
  * Conversation Buffer
    Langchain’s Buffer Memory is a basic memory buffer that stores the conversation history. It has a buffer property that returns a list of messages from the chat memory. This type of memory is important for storing and retrieving the most recent history of a discussion.
  * Conversation Buffer Window
    This type of memory adds a window to the buffer memory that remembers only K number of previous interactions. This reduces the number of tokens utilized, but it loses the context of any inputs that came before the previous K interactions.
  * Conversation Summary
    Conversation summary memory creates an overview of conversations overtime. The summary is continuously updated and can be integrated into prompt/chains. This approach is useful in long conversations where including the entire message history becomes impractical due to over-consumption of tokens.
    * Conversation Summary Buffer
    This type of memory preserves a buffer of recent interactions in memory, but instead of completely clearing previous interactions, it combines them into a summary and uses both. It determines when to flush interactions based on token length rather than the number of interactions.
    Langchain offers a diverse array of memory types accessible via https://python.langchain.com/docs/modules/memory/. Additionally, you can explore customization options and learn how to utilize multiple memory classes in the provided references.

## Documentation
[1] Custom Memory : https://python.langchain.com/docs/modules/memory/custom_memory
[2] Multiple Memory Classes: https://python.langchain.com/docs/modules/memory/multiple_memory

## Code of Conduct

This project has adopted the code of conduct defined by the Contributor Covenant to clarify expected behavior in our community.
For more information see the [Python Software Foundation Code of Conduct](https://policies.python.org/python.org/code-of-conduct/).


## Support

[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://GitHub.com/Naereen/StrapDown.js/graphs/commit-activity)
data-sourcing-challenge is an open-source project with a single maintainer. The best way to resolve your issue is to fix it yourself. Fork the repository and submit a pull request. 

### Get help

Ask the maintainer: [Chris Gilbert][1]

[1]: https://github.com/xraySMULu