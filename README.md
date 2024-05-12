# Bert-Question-Answering
 
### Aim
- Develop a Question Answering model to efficiently extract answers from extensive text documents 📖

### Use case
- Legal documents, with their numerous clauses, pose a challenge for human comprehension due to their sheer volume. This model aims to aid users in swiftly retrieving relevant information from such documents, thereby saving time and effort.

### Tools used
- 1. PDFminer  
- 2. TFIDF and Spacy
- 3. bert-base-uncased trained on [SQuAD2.0]([url](https://rajpurkar.github.io/SQuAD-explorer/explore/v2.0/dev/)) Dataset. 

### Approach
- **PDFminer** : Utilized for text extraction from PDFs. For scanned documents, OCR tools like [TesserOCR](https://anaconda.org/conda-forge/tesserocr) can be employed.
- **Similarity** : Spacy similarity identifies the top 100 paragraphs similar to the question, aiding in filtering out irrelevant content. Additionally, TFIDF and cosine similarity are explored. Paragraphs exhibiting high similarity with the question are more likely to contain relevant answers.
- **BERT** : Trained on the SQuAD dataset from Hugging Face transformers. Model fine-tuning on custom datasets can facilitate domain adaptation. The 'topk' parameter can be adjusted to retrieve the top 'k' answers along with their confidence scores. The model also provides start and end logits, facilitating backtracking into the original paragraph in the PDF. Further steps could involve highlighting answers in the original PDF using PDF plumber, though this aspect is not included in the current implementation.

### Future Improvements
- 1. Explore advanced similarity techniques like ELMO or doc2vec for enhanced performance, especially with longer sequences and paragraphs.
- 2. Consider employing a more suitable model like Longformer, which handles longer sequences more effectively than BERT. BERT's sequence length limit of 512 may not process the entire information at once. However, for short clauses, BERT suffices for the current scenario.
