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

**Accessing the Model:**

<div style="text-align: justify">

The trained HeartBert model (and tokenizer) is available for use via the following link:

- [HeartBert](https://drive.google.com/drive/folders/10flbRia9rDWeS8-TLScRUT6JBv81iN-4)

To load the tokenizer and HeartBert model in your environment, you can use the provided code snippet:

```python
from transformers import AutoTokenizer, AutoModel

tokenizer = AutoTokenizer.from_pretrained(pretrained_model_name_or_path="[link_to_tokenizer]")
heartbert_model = AutoModel.from_pretrained("[link_to_model]")
