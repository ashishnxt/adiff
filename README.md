# adiff - Advanced XML Comparison CLI Tool

## Overview

`adiff` is a Python-based command-line tool that compares one or more XML files against a main reference XML file. It highlights differences, supports filtering, and can generate well-formatted Excel reports for analysis.

## Features

* Compare one or more XML files against a reference XML
* Detect missing or extra tags/attributes
* Filter by tag label (e.g., CAMERA, SENSOR, etc.)
* Output console-friendly tabulated results
* Export to Excel with color-coded formatting
* Options to show only differences for large datasets

---

## Prerequisites

### On Ubuntu/Debian Systems:

```bash
sudo apt update
sudo apt install python3 python3-pip

```

## Installation via pip


```bash
pip install adiff
```
---

## Usage Examples

### 1. Basic Comparison

```bash
adiff main-update.xml *.xml
```

Compare all XML files in the current directory against `main-update.xml`.

### 2. Compare Specific Files

```bash
adiff main-update.xml file1.xml file2.xml file3.xml
```

### 3. Show Only Differences

```bash
adiff main-update.xml *.xml --differences-only
```

### 4. Filter by Label

```bash
adiff main-update.xml *.xml --filter-label "CAMERA"
```

### 5. Excel Output

```bash
adiff main-update.xml *.xml --excel comparison_results.xlsx
```

Generates a colorful Excel file with formatted comparison results.

### 6. Excel Output - Differences Only

```bash
adiff main-update.xml *.xml --excel differences.xlsx --differences-only
```

---

## Installation via pip

After packaging and uploading `adiff` to PyPI, install it via:

```bash
pip install adiff
```

This installs the `adiff` CLI globally.

---

## Project Structure

```
adiff/
├── adiff/
│   ├── __init__.py
│   └── cli.py         # Main Python logic (renamed from xml_compare.py)
├── setup.py
├── pyproject.toml
├── README.md
├── LICENSE
```

---

## Packaging and Publishing to PyPI

### 1. Install build tools

```bash
pip install build twine
```

### 2. Build package

```bash
python3 -m build
```

### 3. Upload to PyPI

```bash
twine upload dist/*
```

To test before full release:

```bash
twine upload --repository-url https://test.pypi.org/legacy/ dist/*
```

---

## Setup.py Sample

```python
from setuptools import setup, find_packages

setup(
    name='adiff',
    version='1.0.0',
    packages=find_packages(),
    install_requires=[
        'pandas',
        'tabulate',
        'lxml',
        'openpyxl'
    ],
    entry_points={
        'console_scripts': [
            'adiff=adiff.cli:main',
        ],
    },
    author='Your Name',
    author_email='your.email@example.com',
    description='Advanced XML Comparison CLI Tool',
    long_description=open('README.md').read(),
    long_description_content_type='text/markdown',
    url='https://github.com/yourusername/adiff',
    classifiers=[
        'Programming Language :: Python :: 3',
        'Operating System :: OS Independent',
        'License :: OSI Approved :: MIT License',
        'Topic :: Text Processing :: Markup :: XML',
        'Intended Audience :: Developers'
    ],
    python_requires='>=3.6',
)
```

---

## CLI Entry Point

This line in `setup.py` ensures that `adiff` can be run as a terminal command:

```python
entry_points={
    'console_scripts': [
        'adiff=adiff.cli:main',
    ],
},
```

---

## License

This tool is published under the MIT License.

---

