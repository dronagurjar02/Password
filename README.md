# Password Project

## Overview

This is a Python-based password generation and text processing utility project. It includes tools for generating strong, memorable passwords using the XKCD-style method and harvesting parts of speech from text files.

## Project Features

### 1. **Password Generator** (`solution.py`)
A utility that creates memorable yet secure passwords by combining random words from input files. Based on the [XKCD comic #936](https://xkcd.com/936/).

**Features:**
- Generate multiple passwords with customizable parameters
- Control password complexity (number of words, word length range)
- Optional l33t-speak obfuscation for added complexity
- Reproducible results with seed support

**Usage:**
```bash
python solution.py [options] <word_file>
```

**Options:**
- `-n, --num`: Number of passwords to generate (default: 3)
- `-w, --num_words`: Number of words per password (default: 4)
- `-m, --min_word_len`: Minimum word length (default: 3)
- `-x, --max_word_len`: Maximum word length (default: 6)
- `-s, --seed`: Random seed for reproducibility
- `-l, --l33t`: Enable l33t-speak obfuscation

**Example:**
```bash
python solution.py -n 5 -w 3 -s 42 words.txt
```

### 2. **Text Harvest Utility** (`harvest.py`)
Extracts and categorizes parts of speech from text files using spaCy NLP library.

**Features:**
- Extract nouns, verbs, and adjectives from text
- Process multiple input files
- Configurable output directory
- Optional limiting to top N words
- Saves results to organized output files

**Usage:**
```bash
python harvest.py [options] <input_file(s)>
```

**Options:**
- `-o, --outdir`: Output directory for results (default: 'words')
- `-l, --limit`: Limit results to top N words (default: all)

**Output:**
Creates three files in the output directory:
- `nouns.txt` - All extracted nouns
- `verbs.txt` - All extracted verbs
- `adjs.txt` - All extracted adjectives

## Project Structure

```
Password/
├── solution.py       # Main password generator
├── harvest.py        # Text processing utility
├── test.py          # Test suite for password generator
├── unit.py          # Unit tests for helper functions
├── Makefile         # Build and test automation
├── all_test.sh      # Test runner script
├── const/           # Constants directory
├── scarlet/         # Additional resources
├── sonnets/         # Sample text files
└── README.md        # This file
```

## Installation

### Requirements
- Python 3.6+
- spaCy library with English model

### Setup
```bash
# Clone the repository
git clone https://github.com/dronagurjar02/Password.git
cd Password

# Install dependencies
pip install spacy

# Download spaCy English model
python -m spacy download en_core_web_sm
```

## Usage Examples

### Generate Passwords
```bash
# Generate 3 passwords with 4 words each
python solution.py words.txt

# Generate 10 passwords with 3 words, reproducible with seed
python solution.py -n 10 -w 3 -s 123 words.txt

# Generate passwords with l33t-speak
python solution.py -l -n 5 words.txt

# Generate passwords with specific word length range
python solution.py -m 5 -x 8 -n 3 words.txt
```

### Harvest Text
```bash
# Extract parts of speech from a file
python harvest.py text.txt

# Process multiple files and limit to top 50 words
python harvest.py -l 50 -o output file1.txt file2.txt file3.txt
```

## Testing

Run the test suite to verify functionality:

```bash
# Run all tests
make test

# Or use the test script
./all_test.sh

# Run specific test file
pytest test.py -v
pytest unit.py -v
```

## Helper Functions

### `clean(word)` - `solution.py`
Removes non-alphabetic characters from a word string.

### `ransom(text)` - `solution.py`
Randomly alternates uppercase and lowercase letters in text.

### `l33t(text)` - `solution.py`
Converts text to l33t-speak by replacing characters with symbols and adding random punctuation.

## Author

**Drona Gurjar**

## License

This project is provided as-is for educational and practical use.

## Contributing

To contribute to this project:
1. Fork the repository
2. Create a feature branch
3. Make your improvements
4. Submit a pull request

## Notes

- The password generator uses random selection, so results will vary unless a seed is specified
- The harvest utility requires the spaCy English language model to be installed
- For reproducible results, always specify a seed with the `-s` flag

---

**Last Updated:** 2026-05-13

For more information about password security, visit: https://xkcd.com/936/
