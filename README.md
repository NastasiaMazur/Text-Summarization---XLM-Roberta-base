# Text Summarization - XLM-Roberta-base

In this Project I tried to turn an XLM-R/BERT-like pretrained transformers model trained on a masked learning target into a text summarization model by treating the model as an encoder in an encoder-decoder architecture.
In the process of completing the assignment, I consulted the tutorials on Huggingface:

•	https://huggingface.co/docs/transformers/model_doc/encoder-decoder

•	https://huggingface.co/docs/transformers/tasks/summarization
and also took as a basis the data code in the model description of roberta2roberta-cnn_dailymail-fp16:

•	https://huggingface.co/patrickvonplaten/roberta2roberta-cnn_dailymail-fp16


The choice of English and Russian datasets was based on the need to reflect the different linguistic structures and cultural nuances inherent in news articles and their summaries. The original intention was that by using both languages in the training process, it would be possible to better account for the differences in syntax, vocabulary, and stylistic techniques present in these texts. It was also tempting to see how the model would cope with languages using different writing systems (in this case Cyrillic and Latin).


**Model**

•	XLM-RoBERTa (base-sized model)
https://huggingface.co/FacebookAI/xlm-roberta-base

**Datasets**

•	CNN Dailymail Dataset

https://huggingface.co/datasets/cnn_dailymail

•	Gazeta Dataset

https://huggingface.co/datasets/IlyaGusev/gazeta

**Quantity of data used for the project**

Since both of the datasets I used have a large volume, I was forced to use only a small portion of them. For fine-tuning, I used a proportional amount for both English and Russian datasets, which were subsequently merged. I took 1500 (train) and 300 (validation) text examples from both English and Russian datasets for fine tuning and evaluated on 300 examples from each dataset.

**Setup**

The entire training process was executed on Google Colab, leveraging GPU acceleration to efficiently handle the computational demands. Utilizing a CPU alone for this task proved inadequate due to several reasons. Firstly, the substantial size of the model demands significant computational resources beyond what a CPU can efficiently provide. With its intricate architecture and numerous parameters, the model necessitates parallel processing capabilities inherent to GPUs for optimal performance.
Moreover, the large volume of data involved in the training process, comprising both raw text data and summarized versions, exacerbates the computational burden. Attempting to train such a model on a CPU would inevitably lead to prolonged training times and, more critically, a heightened risk of encountering memory-related errors. Given the immense memory requirements imposed by both the model's size and the dataset's scale, relying solely on a CPU would likely result in memory exhaustion issues, hindering the training process and potentially causing system crashes.
Thus, the decision to utilize GPU acceleration in Google Colab was not only pragmatic but also imperative, ensuring efficient training and mitigating the risk of encountering memory-related constraints and errors inherent in CPU-based approaches.

**Quantitative results**

For evaluation, such ROUGE metrics were used as: precision, recall and measure.

As can be seen even from the small number of results presented, there is a significant problem with predicting summarization for the Russian dataset, leading to zero scores.

**Qualitative results**

The results above demonstrate that the program encounters difficulties in generating predictions in Russian language. The predictions for both languages lack accuracy, coherence, and relevance compared to the references. They exhibit significant gibberish with repeated letters and incomplete words, making them incomprehensible. The predictions also fail to maintain relevance to the context provided by the references.
Firstly, the model struggles to grasp the semantic meaning of the input references. Understanding the context, nuances, and relationships between words and phrases is crucial for generating coherent and relevant predictions. In these examples, the model fails to comprehend the content it's meant to emulate, resulting in nonsensical output.
Secondly, generating text often involves making logical inferences and reasoning based on the provided context. However, the model may have difficulty making accurate inferences or connecting disparate pieces of information.

Also, the limited number of resources provided by Collab in the free version caused fine tuning to be interrupted, often due to insufficient RAM or no connection to the GPU. As a result, I had to wait for resources to be available again for further work. OutofMemory errors also accompanied my work on the project.
It would certainly be interesting to experiment with the possibility of using a larger dataset in the training process and see what results it will or will not lead to. Also, thanks to this assignment, I realized firsthand what resources are required to train even small models on a relatively small amount of data. And now I have a clearer understanding of what it might look like on a larger scale and the costs and expenses it can lead to.


