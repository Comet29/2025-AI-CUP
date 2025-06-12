# 2025-AICUP-Medical Speech Sensitive Personal Information Identification Challenge
## Setup
I ran the following program on Google Colab (Pro), using a T4 GPU.
### Main code
This program performs audio transcription with timestamp alignment and utilizes OpenAI to identify Sensitive Health Information (SHI); however, it currently supports only English audio files.
<pre> !pip install -q datasets openai-whisper </pre>
<pre> pip install -U bitsandbytes transformers </pre>
<pre> !pip install openai </pre>
<pre> !pip install whisperx </pre>

### Chinese Audio
This program has been patched to support Chinese audio files(Chinese Audio Bug Fix), but its functionality is currently limited to transcription and timestamp alignment only.
<pre> !pip install -q datasets openai-whisper </pre>
<pre> !pip install whisperx </pre>
<pre> !sed -i 's/frame_emission\[tokens.clamp(min=0)\]/frame_emission[tokens.clamp(min=0).long()]/g' /usr/local/lib/python3.11/dist-packages/whisperx/alignment.py </pre>
<pre> !pip install opencc-python-reimplemented </pre>

### Chinese ShI
This program has been patched to support Chinese audio files(Chinese Audio Bug Fix), but its functionality is currently limited to transcription and timestamp alignment only.
<pre> !pip install -q datasets openai-whisper </pre>
<pre> !pip install whisperx </pre>
<pre> !sed -i 's/frame_emission\[tokens.clamp(min=0)\]/frame_emission[tokens.clamp(min=0).long()]/g' /usr/local/lib/python3.11/dist-packages/whisperx/alignment.py </pre>
<pre> !pip install opencc-python-reimplemented </pre>
