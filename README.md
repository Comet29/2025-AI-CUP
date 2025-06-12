# 2025-AICUP-Medical Speech Sensitive Personal Information Identification Challenge
## Setup
I ran the following program on Google Colab (Pro), using a T4 GPU.

## Main code
This program performs audio transcription with timestamp alignment and utilizes OpenAI to identify Sensitive Health Information (SHI); however, it currently supports only English audio files.
<pre> !pip install -q datasets openai-whisper </pre>
<pre> pip install -U bitsandbytes transformers </pre>
<pre> !pip install openai </pre>
<pre> !pip install whisperx </pre>

## Chinese Audio
This program has been patched to support Chinese audio files(Chinese Audio Bug Fix), but its functionality is currently limited to transcription and timestamp alignment only.
<pre> !pip install -q datasets openai-whisper </pre>
<pre> !pip install whisperx </pre>
<pre> !sed -i 's/frame_emission\[tokens.clamp(min=0)\]/frame_emission[tokens.clamp(min=0).long()]/g' /usr/local/lib/python3.11/dist-packages/whisperx/alignment.py </pre>
<pre> !pip install opencc-python-reimplemented </pre>

## Chinese SHI
This program extracts SHI from text.
<pre> !pip install openai </pre>
### Input
Users must manually input the path to the text file (.txt).
Format: Each line contains an integer index, followed by a tab character, then a Chinese sentence to be processed.
<pre> TXT_INPUT_FILE = "/content/transcription_zh.txt" </pre>
### Output
Structured extraction results for each input line.
Format: A JSON object where each key is the line index from the input file. Each entry contains the original sentence (transcript) and the extracted structured results (gpt_result) in various categories.
<pre> OUT_JSON = "multi_txt_results.json" </pre>
Tab-delimited, line-by-line annotated SHI phrases.
Format: Each line contains the index, a category (in uppercase), and the extracted phrase, separated by tabs.
<pre> OUT_TEXT2 = "text2_zh.txt" </pre>
Indices of lines that failed to process.
Format: Each line contains the index of an input line that failed to process due to an API error or parsing failure.
<pre> OUT_WRONG = "wrong_json.txt" </pre>
