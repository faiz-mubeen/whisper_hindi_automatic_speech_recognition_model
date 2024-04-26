
# Whisper Hindi ASR(Automatic speech recognition):

In this Automatic Speech Recognition task, I employ the OpenAI Whisper "large" Model to transcribe Hindi audio files into text. Utilizing the Word Error Rate (WER) score metric, I gauge the accuracy of the transcribed text compared to the original reference, offering valuable insights into the performance of the Whisper model and the transcription process's overall efficacy.





## Whisper

Whisper is a general-purpose speech recognition model. It is trained on a large dataset of diverse audio and is also a multitasking model that can perform multilingual speech recognition, speech translation, and language identification. [Whisper](https://github.com/openai/whisper/tree/main)
## Setup

Cloning the whisper repository along with its Python dependencies:

```bash
  !pip install git+https://github.com/openai/whisper.git
```
    
## Whisper Model and sample usage

#### Model used: 
Whisper `"large"` with 1550 M parameters.

```python
import whisper

model = whisper.load_model("large")
```


`Reference text:` 01-00031-03 क्यूँकि हमारी पुलिस तो फेसबुक और दुसरे सोशल मीडिया के माध्यमों पर अपराध करने वालों को पकड़ने में ही असमर्थ है

#### Transcribed text
```python
result = model.transcribe('/content/drive/MyDrive/Colab Notebooks/ASR/GV_Eval_3h/Audio/01-00031-03.mp3',language='hi')
print(result["text"])
```
`Tanscribed Output:`क्योंकि हमारी पुलिस का फेस्बुक और गुशे सुसल मिग्रे के माध्यमों पर अप्राज करने वालों को पकड़ने में ही असमर्थ है।

Now we have `reference text` and `transcribed text`, we used Word error rate `(WER)` to get the accuracy of the transcribed text compared to the original reference.

### Word Error Rate (WER)
Word Error Rate (WER) is a common metric of the performance of a speech recognition or machine translation system. It is like a score that measures how well a computer system can turn spoken words into written words. 

It quantifies the differences between the transcribed output produced by the ASR system and the actual reference or correct transcription.

To calculate WER, we count the total number of errors—such as insertions (extra words added), deletions (missing words), and substitutions (wrong words used)—needed to align the transcribed text with the reference text. This count is then divided by the total number of words in the reference text. The resulting ratio provides a standardized measure of the accuracy of the ASR system, allowing for comparisons and insights into its performance.

The lower the WER, the better the system is at accurately transcribing speech into text. So, it helps us understand how accurate the transcription is compared to the original spoken words.