<H3>NAME : FRANKLIN RAJ G</H3>
<H3>REGISTER NO. 212223230058</H3>
<H3>EX. NO.9</H3>
<H3>DATE :6.09.2026 </H3>
<H1 ALIGN =CENTER>Implementation of Text  Summarization</H1>
<H3>Aim: </H3> To perform automatic text summarization using Natural Language Processing (NLP) techniques. 
 <BR>
<h3>Algorithm:</h3>
Step 1: Import necessary libraries for natural language processing tasks.<BR>
Step 2: Download NLTK resources, including the punkt tokenizer and stopwords.<BR>
Step 3: Define Text Preprocessing Function to tokenize, remove stopwords, and perform stemming.<BR>
Step 4: Define the Text Summarization Function using a simple frequency-based approach.<br>
    - Calculate the frequency of each word in the preprocessed text.<br>
    - Calculate a score for each sentence based on the sum of word frequencies.<br>
    - Select the top N sentences with the highest scores to form the summary.<br>
Step 5: Construct the main program to read the paragraph  and perform text summarization<br>
      - Generate and print the original text.<br>
      - Generate and print the text summary using the  Text Summarization function<br>
<BR>
<H3>Program:</H3>
<BR>

```python

import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize, sent_tokenize
from nltk.stem import PorterStemmer

nltk.download('punkt')
nltk.download('punkt_tab')
nltk.download('stopwords')

def preprocess(text):
    words = word_tokenize(text)
    stop_words = set(stopwords.words('english'))
    words = [w for w in words if w.lower() not in stop_words and w.isalnum()]
    return [PorterStemmer().stem(w) for w in words]

def summarize(text, n=3):
    sentences = sent_tokenize(text)
    freq = nltk.FreqDist(preprocess(text))
    scores = {s: sum(freq[w] for w in freq if w in s.lower()) for s in sentences}
    return ' '.join(sorted(scores, key=scores.get, reverse=True)[:n])

text = """Natural language processing (NLP) is a subfield of artificial intelligence.
It involves the development of algorithms and models that enact NLP.
NLP is used in various applications, including chatbots, language understanding,
and language generation. This program demonstrates a simple text summarization using NLP."""

print("Original Text:\n", text)
print("\nSummary:\n", summarize(text))

```

<H3>Output</H3>

<img width="747" height="213" alt="image" src="https://github.com/user-attachments/assets/2ffaec13-28b6-4bf0-8820-4dc7533f57b4" />

<H3>Result:</H3>
Thus, the program to perform the Text summarization is executed sucessfully.
