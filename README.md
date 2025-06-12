# 2025-AICUP-Medical Speech Sensitive Personal Information Identification Challenge
## Setup
I ran the following program on Google Colab (Pro), using a T4 GPU.

## Main code
This program performs audio transcription with timestamp alignment and utilizes OpenAI to identify Sensitive Health Information (SHI); however, it currently supports only English audio files.
<pre> !pip install -q datasets openai-whisper </pre>
<pre> pip install -U bitsandbytes transformers </pre>
<pre> !pip install openai </pre>
<pre> !pip install whisperx </pre>
### Input
Users must manually input the path to the Audio folder.
<pre> AUDIO_FOLDER = "/content/drive/MyDrive/Private_dataset/private" </pre>
### Output
Full structured results for each audio file, including transcription, time alignment, and extracted sensitive information. <br>
Format: A JSON object where each key is the base filename (without extension) of an audio file.(gpt_result) in various categories.
<pre> multi_audio_results.json </pre>
Plain text transcripts (one per line, with filename). <br>
Format: Each line contains the base filename of the audio file, followed by a tab and the full transcribed text.
<pre> text1.txt </pre>
Time-aligned, post-processed annotations (one per entity, per line, with filename and time range). <br>
Format: Each line contains the base filename, the annotation category (in uppercase), the start time, end time (in seconds), and the extracted phrase, all separated by tabs.
<pre> text2.txt </pre>
List of audio files that failed to process, for troubleshooting. <br>
Format: Each line contains the base filename (without extension) of an audio file that failed to process due to transcription errors, API errors, or JSON parsing errors.
<pre> wrong_json.txt </pre>

## Chinese Audio
This program has been patched to support Chinese audio files(Chinese Audio Bug Fix), but its functionality is currently limited to transcription and timestamp alignment only.
<pre> !pip install -q datasets openai-whisper </pre>
<pre> !pip install whisperx </pre>
<pre> !sed -i 's/frame_emission\[tokens.clamp(min=0)\]/frame_emission[tokens.clamp(min=0).long()]/g' /usr/local/lib/python3.11/dist-packages/whisperx/alignment.py </pre>
<pre> !pip install opencc-python-reimplemented </pre>
### Input
Users must manually input the path to the Audio folder.
<pre> audio_folder = r"/content/drive/MyDrive/Private_dataset/private" </pre>
### Output
The full transcript of each audio file in Traditional Chinese, one file per line. <br>
Format: Each line contains the base filename (without extension), a tab character, and the full transcribed text in Traditional Chinese (converted from Simplified Chinese if necessary).
<pre> transcription_zh.txt </pre>
The word-level time alignment for each audio file, all in Traditional Chinese. <br>
Format: For each audio file, the base filename is written on one line. The following lines list each word on a separate line, with its start and end timestamps (in seconds) and the word in Traditional Chinese.
<pre> word_segments_zh.txt </pre>

## Chinese SHI
This program extracts SHI from text.
<pre> !pip install openai </pre>
### Input
Users must manually input the path to the text file (.txt).
Format: Each line contains an integer index, followed by a tab character, then a Chinese sentence to be processed.</be>
<pre> TXT_INPUT_FILE = "/content/transcription_zh.txt" </pre>
### Output
Structured extraction results for each input line. <br>
Format: A JSON object where each key is the line index from the input file. Each entry contains the original sentence (transcript) and the extracted structured results (gpt_result) in various categories.
<pre> multi_txt_results.json </pre>
Tab-delimited, line-by-line annotated SHI phrases. <br>
Format: Each line contains the index, a category (in uppercase), and the extracted phrase, separated by tabs.
<pre> text2_zh.txt </pre>
Indices of lines that failed to process. <br>
Format: Each line contains the index of an input line that failed to process due to an API error or parsing failure.
<pre> wrong_json.txt </pre>
