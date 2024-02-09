

# BERT

bertsummarizer.ipynb is main file and , summary_audio.mp3 is result of summary and Bert.mkv is video of implementing model

## Code Overview

This Python script leverages the Hugging Face `transformers` library to perform text summarization using the BART (Bidirectional and Auto-Regressive Transformers) model. The script provides functions for summarizing text, splitting it into manageable pieces, and recursively summarizing lengthy documents.

### Dependencies
- Ensure you have the required packages installed using the following commands:
  ```bash
  !pip install transformers
  !pip install torch
  !pip install tensorflow
  !pip install gtts
  ```

### Usage

1. Import the necessary modules and load the pre-trained BART model and tokenizer.

2. Use the `summarize` function to generate a summary of a given text.

    ```python
    summary = summarize(text, maxSummarylength=500)
    ```

3. The `split_text_into_pieces` function breaks down a text into smaller pieces to avoid tokenization limitations.

    ```python
    text_pieces = split_text_into_pieces(text, max_tokens=900, overlapPercent=10)
    ```

4. For handling longer documents, the `recursive_summarize` function recursively summarizes each piece, concatenates the results, and continues the process until the final summary is within the specified length.

    ```python
    final_summary = recursive_summarize(text, max_length=200, recursionLevel=0)
    ```

### Example

An example text is provided in the script, and you can replace it with your own text for testing.

```python
text = '''[Your text goes here]'''
final_summary = recursive_summarize(text)
print("Final summary:", final_summary)
```

### Text-to-Speech (TTS)

The script also includes functionality to convert the final summary into an audio file using Google Text-to-Speech (gTTS). The audio file is saved as "summary_audio.mp3".

```python
from gtts import gTTS
language = 'en'
tts = gTTS(text=final_summary, lang=language, slow=False)
tts.save("summary_audio.mp3")
```

### Notes

- Adjust parameters such as `maxSummarylength`, `max_tokens`, and `overlapPercent` based on your specific requirements.
- Ensure the input text is well-formatted for effective summarization.

Feel free to modify and integrate this script into your projects as needed!
