<h1 style="font-size: 24px;">Project Title: HeartBert</h1>

**Team Members:**
- Saeed Farzi
- Saedeh Tahery
- Fatemeh HamidAkhlaghi
- Termeh Amirsoleimani
- Fatemeh Afghah
- Ali Owfi

<div style="text-align: justify">

**Overview:**

In this project, we present HeartBert, a  dedicated language model tailored for ECG (Electrocardiogram) data analysis. Leveraging the power of Roberta, a BERT-like architecture, we trained a specialized model from scratch using diverse datasets, including the [MIT-BIH Arrhythmia Database](https://www.physionet.org/content/mitdb/1.0.0/), [PTB-XL](https://physionet.org/content/ptb-xl/1.0.0/), and [European ST-T Database](https://physionet.org/content/edb/1.0.0/). Our approach involves translating ECG signals into text representations, enabling seamless integration of natural language processing techniques with physiological data analysis.

</div>

**Data Preprocessing:**

<div style="text-align: justify">

To prepare the ECG data, we resampled all signals to 360 Hz and normalized them to a range of [0, 1]. We adopted a quantization approach, namely Lloyd-Max with a quantization level set at 100, to convert ECG signals into text. Additionally, we windowed signals with a maximum window size of 4000 for efficient processing.

</div>

**Model Training:**

<div style="text-align: justify">

The HeartBert model comprises 6 layers and was trained on our prepared dataset for 1000 epochs. This comprehensive training ensures that the model captures intricate patterns and features within the ECG data, empowering it to make accurate predictions.

</div>

**Application and Usage:**

<div style="text-align: justify">

The trained HeartBert model offers capabilities for various downstream tasks in healthcare analytics, utilizing ECG data. It can be fine-tuned for tasks such as sleep stage classification and heart disease diagnosis, facilitating medical research and clinical decision-making.

</div>


## RESULT

**testing the effect of embedding:**
<div style="text-align: justify">

We adopted the model described in this paper as our initial model. To evaluate the impact of HeartBERT, we employed the initial model for sleep stage classification. We tested the model for 3-class and 5-class scenarios. First, we used raw ECG signals as the model input. Next, to assess potential enhancements, we fed the ECG signals into HeartBERT and used the generated embeddings as input for the initial model.
The following chart compares the accuracy resulting from raw ECG signals versus embeddings.
<br><br><br>
<img src="https://github.com/ecgResearch/HeartBert/blob/main/images/embedding.png" width="30%">
<br><br>
</div>

**testing the effect of unfreezing HeartBERT layers:**
<div style="text-align: justify">
To assess the impact of training layers in HeartBERT, we implemented a basic model in which we input HeartBERT-generated embeddings into a bi-LSTM for classifying ECG signals into 3 and 5 classes. In this experiment, we unfroze the layers of HeartBERT to further train them on our dataset. The following chart demonstrates the comparison between training all six layers of HeartBERT and training only the last three layers.
<br><br><br>
<img src="https://github.com/ecgResearch/HeartBert/blob/main/images/3or6.png" width="30%">
<br><br>
</div>

**Accessing the Model:**

<div style="text-align: justify">

The trained HeartBert model (and tokenizer) is available for use via the following link:

- [HeartBert](https://drive.google.com/drive/folders/10flbRia9rDWeS8-TLScRUT6JBv81iN-4)

To load the tokenizer and HeartBert model in your environment, you can use the provided code snippet:

```python
from transformers import AutoTokenizer, AutoModel

tokenizer = AutoTokenizer.from_pretrained(pretrained_model_name_or_path="[link_to_tokenizer]")
heartbert_model = AutoModel.from_pretrained("[link_to_model]")
