# Stanford RNA 3D Folding Inference Pipeline

## Overview
This repository showcases a professional, production-ready inference pipeline designed to predict the 3D atomic coordinates of RNA sequences. Originally developed for the Stanford RNA 3D folding competition, this codebase implements a robust environment for evaluating RNA structures using the `Protenix` deep learning architecture. 

## Key Features
* **Offline-Ready Setup:** Includes an automated script to install necessary Python wheels (`.whl`) without internet access, ensuring compatibility with restricted execution environments like Kaggle.
* **Robust Configuration Handling:** Implements a custom iterative stack-based configuration patcher to bypass Python `RecursionError` limits when loading complex `ml_collections` configurations.
* **Automated Feature Engineering:** Calculates sequence length and GC content directly from input sequences.
* **3D Sequence Visualization:** Utilizes `matplotlib` to render 3D spatial plots of the RNA backbone (C1' trace) with nucleotide-specific color coding (Adenine, Uracil, Guanine, Cytosine).
* **Competition-Ready Output:** Automatically structures 3D coordinate predictions (x, y, z) into a formatted `submission.csv` file.

## Technical Stack
* **Framework:** PyTorch
* **Data Processing:** Pandas, NumPy
* **Visualization:** Matplotlib
* **Environment:** Python 3.12 (Kaggle Docker base)

## Pipeline Execution Details
1. **Setup:** The pipeline first establishes the offline environment by loading local dependencies.
2. **Model Loading:** Initializes the `Protenix` architecture and loads pre-trained weights to the available device (CPU/CUDA). 
3. **Inference & Chunking:** Processes sequence files (`test_sequences.csv`), handling tokenization and coordinate generation. 
4. **Export:** Iterates through up to 5 predictions per nucleotide residue to finalize spatial mappings before saving the results.
