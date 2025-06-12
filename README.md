# 2025-AI-CUP
## Setup

### Main code

<pre> !pip install -q datasets openai-whisper </pre>
<pre> pip install -U bitsandbytes transformers </pre>
<pre> !pip install openai </pre>
<pre> !pip install whisperx </pre>

### Chinese Audio
<pre> !pip install -q datasets openai-whisper </pre>
<pre> !pip install whisperx </pre>
<pre> !sed -i 's/frame_emission\[tokens.clamp(min=0)\]/frame_emission[tokens.clamp(min=0).long()]/g' /usr/local/lib/python3.11/dist-packages/whisperx/alignment.py </pre>
<pre> !pip install opencc-python-reimplemented </pre>
