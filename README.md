# Humor Style Classification XAI Dataset

This repository contains the eXplainable AI (XAI) analysis data for humor style classification, accompanying the paper "Explaining Humour Style Classifications: An XAI Approach to Understanding Computational Humour Analysis" (2024).

## Repository Structure
- ├── LIME_plots/             # LIME visualization plots for all analyzed jokes
- ├── linguistic_affective_analysis_json/  # Individual JSON files for each joke
- ├── XAI.xlsx                # Combined analysis data
- └── README.md

## Dataset Description

The dataset contains XAI analysis for 293 jokes classified into five categories:
- Self-enhancing
- Self-deprecating
- Affiliative
- Aggressive
- Neutral

### LIME_plots/
Contains PNG files of LIME (Local Interpretable Model-agnostic Explanations) visualizations for all 293 analyzed jokes. Each plot shows:
- Word-level feature importance
- Contribution to classification decision
- Confidence scores

File naming convention: `lime_explanation_joke_{id}.png`

### linguistic_affective_analysis_json/
Individual JSON files containing detailed linguistic and affective analysis for each joke, including:
- Linguistic features (syllable complexity, semantic conflicts, homonyms, etc.)
- Affective patterns (sentiment, emotion, sarcasm)
- Structural elements (self-references, POS patterns)
- Classification results

File naming convention: `detailed_analysis_joke_{id}.json`

### XAI.xlsx
A consolidated excel file combining all analysis data, with columns:
- joke_id: Unique identifier for each joke
- joke_text: The actual joke content
- true_label: Ground truth humor style
- predicted_label: Model's classification
- confidence_score: Classification confidence
- linguistic_features: Extracted linguistic patterns
- affective_features: Emotional and sentiment analysis
- lime_features: Top contributing features from LIME analysis
- error_analysis: Misclassification details (where applicable)

## Requirements

Python 3.7+
pandas
matplotlib
PIL (Python Imaging Library)

## Citation
If you use this dataset in your research, please cite:
@inproceedings{kenneth2024explaining,
  title={Explaining Humour Style Classifications: An XAI Approach to Understanding Computational Humour Analysis},
  author={Kenneth, Mary Ogbuka and Khosmood, Foaad and Edalat, Abbas},
  booktitle={Journal of Data Mining and Digital Humanities},
  year={2024}
}

## License
This dataset is released under MIT License.You can read more about it at https://opensource.org/license/MIT.

## Usage

The data can be loaded and analyzed using standard Python libraries:

```python
import pandas as pd
import json
import matplotlib.pyplot as plt

# Load consolidated data
xai_data = pd.read_excel('XAI.xlsx')

# Load individual JSON analysis
with open('linguistic_affective_analysis_json/detailed_analysis_1.json', 'r') as f:
    joke_analysis = json.load(f)

# View LIME plots
from PIL import Image
img = Image.open('LIME_plots/plots/lime_explanation_0001.png')
plt.imshow(img)
plt.axis('off')
plt.show()

