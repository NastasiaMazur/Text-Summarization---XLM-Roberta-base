# Text-Summarization---XLM-Roberta-base

In this Project I tried to turn an XLM-R/BERT-like pretrained transformers model trained on a masked learning target into a text summarization model by treating the model as an encoder in an encoder-decoder architecture.
In the process of completing the assignment, I consulted the tutorials on Huggingface:
•	https://huggingface.co/docs/transformers/model_doc/encoder-decoder
•	https://huggingface.co/docs/transformers/tasks/summarization
and also took as a basis the data code in the model description of roberta2roberta-cnn_dailymail-fp16:
•	https://huggingface.co/patrickvonplaten/roberta2roberta-cnn_dailymail-fp16


The choice of English and Russian datasets was based on the need to reflect the different linguistic structures and cultural nuances inherent in news articles and their summaries. The original intention was that by using both languages in the training process, it would be possible to better account for the differences in syntax, vocabulary, and stylistic techniques present in these texts. It was also tempting to see how the model would cope with languages using different writing systems (in this case Cyrillic and Latin).
