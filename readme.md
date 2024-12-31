# Ref2Json

Extract structured citation data from images of academic reference pages using vision-language models.

## Overview

Ref2Json is a tool that converts images of academic reference pages into structured JSON data. It uses a vision-language model to directly process reference page images and extract citation information in a standardized format, making it easier to work with bibliographic data programmatically.

## Features

- Process JPG images of reference pages from academic papers
- Extract structured citation data including:
  - Authors
  - Publication year
  - Title 
  - Journal/Publication name
  - Volume
  - Issue
  - Page numbers
  - DOI (when available)
- Generate standardized JSON output
- Batch processing of multiple images
- Robust error handling and validation
- Detailed processing logs

## Requirements

```
unsloth
torch
transformers
Pillow
```


The script will:
1. Process each image in the input directory
2. Extract citation information using the vision model
3. Generate JSON files containing the structured reference data
4. Save output files with `_references.json` suffix

## JSON Output Format

```json
[
  {
    "authors": ["Last, F. M.", "Second, A. B."],
    "year": "2024",
    "title": "Example paper title",
    "journal": "Journal Name",
    "volume": "15",
    "issue": "2",
    "pages": "123-145",
    "doi": "10.1234/example.doi"
  }
]
```

## Technical Details

### Vision Model Configuration
- Model: Llama-3.2-11B-Vision-Instruct
- 4-bit quantization for reduced memory usage
- Unsloth gradient checkpointing for improved performance
- Temperature: 0.2
- Minimum probability: 0.1
- Maximum new tokens: 5000

### JSON Extraction Process
The system employs a two-stage extraction approach:
1. Primary extraction attempts to find and parse a complete JSON array
2. Fallback mechanism identifies and parses individual JSON objects when array parsing fails

### Error Handling
- Robust JSON parsing with nested bracket tracking
- String literal and escape character handling
- Detailed error logging and processing status updates
- Graceful handling of malformed or missing JSON data

## Limitations

- Currently supports JPG images only
- Requires CUDA-capable GPU for model inference
- Designed for APA-style references
- Performance depends on image quality and reference formatting


## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

