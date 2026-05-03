```bash
https://www.geeksforgeeks.org/artificial-intelligence/chunking-strategies/
```
### 📦 What is Chunking?

**Chunking means breaking large data (like documents, text, or files) into smaller, manageable pieces called “chunks.”**

**Instead of processing a whole big document at once, we divide it into smaller parts so AI can understand and process it better.**

### 🤔 Why is Chunking Needed?
#### Limited Context Size

**AI models (like LLMs) can only read a limited amount of text at one time (called context window).**

#### 👉 Example:

- If a model can handle 4,000 words
But your document has 20,000 words
➡️ You must split it into chunks
#### Better Understanding

##### Smaller chunks help AI:

- Focus on specific information
- Reduce confusion
- Improve accuracy
#### Faster Processing

##### Processing small chunks:

- Uses less memory
- Speeds up response time
#### 📄 Example of Chunking
**Without Chunking:**
```bash
Document (10 pages)→ Sent directly to AI ❌ (too large)
```
**With Chunking:**
```bash

Document (10 pages)
→ Page 1-2 → Chunk 1
→ Page 3-4 → Chunk 2
→ Page 5-6 → Chunk 3
→ ...
```

#### Now AI processes each chunk separately ✅

## 🔧 Types of Chunking
#### 1. Fixed Chunking

**Split text into equal sizes.**

#### 👉 Example:
```bash
Chunk 1: 500 words  
Chunk 2: 500 words  
Chunk 3: 500 words

✔ Simple
❌ May break sentences or meaning
```
#### 2. Semantic Chunking (Smart Chunking)

**Split based on meaning.**
```bash
👉 Example:

One chunk = one topic
One chunk = one section

✔ Better understanding
✔ Keeps context meaningful
```
#### 3. Overlapping Chunking

**Chunks share some common content.**
```bash
👉 Example:

Chunk 1: Line 1–100  
Chunk 2: Line 80–180  

✔ Keeps continuity
✔ Avoids missing important info
```
### 🧠 Chunking in AI Applications

#### Chunking is widely used in:

- Document search systems (RAG – Retrieval Augmented Generation)
- Chatbots using PDFs
Knowledge base systems
- Vector databases
### 🔗 How Chunking Connects to Other Concepts

**Chunking is usually followed by:**
```bash
Chunking →
Convert chunks into vectors (Embeddings) →
Store in vector DB →
Retrieve relevant chunks →
Send to AI for answer
```

##  🚀 Simple Real-Life Analogy

**Think of chunking like reading a book:**
- ❌ Reading entire book at once → confusing
- ✅ Reading chapter by chapter → easy to understand

```bash
## chunking 

from langchain_text_splitters  import CharacterTextSplitter,RecursiveCharacterTextSplitter,CharacterTextSplitter 
from langchain_community.document_loaders import TextLoader

# loader=TextLoader("../data/text_files/ai_intro.txt",encoding='utf-8')
# document=loader.load()
# print(document)
# text_splitter = RecursiveCharacterTextSplitter(chunk_size=100, chunk_overlap=0,keep_separator=',')
# texts = text_splitter.split_text(document)
# texts
# text_splitter = CharacterTextSplitter.from_tiktoken_encoder(
#     encoding_name="cl100k_base", chunk_size=100, chunk_overlap=0
# )
# texts = text_splitter.split_text(document)

# Load an example document
with open("../data/text_files/ai_intro.txt",encoding="utf-8") as f:
    state_of_the_union = f.read()

text_splitter = CharacterTextSplitter(
    separator="\n\n",
    chunk_size=500,
    chunk_overlap=10,
    length_function=len,
    is_separator_regex=False,
)
texts = text_splitter.create_documents([state_of_the_union])
print(texts[0])
```