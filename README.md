<img width="1078" height="307" alt="image" src="https://github.com/user-attachments/assets/e50a685e-2b73-4c56-a6f3-f7ed118639c8" />


---

### The Challenge 🤔

Traditional bioacoustic monitoring with Convolutional Neural Networks (CNNs) often requires:
*   Large, complex models.
*   Computationally expensive preprocessing (like filtering and downsampling).
*   This makes real-time analysis on low-resource edge devices difficult. 🐢⏳

### Our Solution: ESO ✨

ESO (Evolutionary Spectrogram Optimisation) tackles this by using a **Genetic Algorithm (GA)** to intelligently select the most informative frequency bands directly from the original spectrogram.

Instead of processing the *entire* spectrogram, ESO:
1.  🧬 **Encodes** horizontal spectrogram bands (defined by position `Pₜ` and height `h`) as "genes".
2.  📜 **Combines** genes into "chromosomes", representing a specific selection of bands.
3.  💪 **Evolves** a population of chromosomes using selection, crossover, and mutation.
4.  📈 **Optimizes** for a fitness function balancing classification performance (F1-score) and model simplicity (trainable parameters).
5.  📉 **Outputs** the best chromosome, which defines narrow bands to be extracted and stacked, creating a highly compressed input for a much simpler CNN.



<img width="1751" height="817" alt="eso gene chromosome" src="https://github.com/user-attachments/assets/4318f530-4aba-49d7-bf6d-c78636131e6a" />


<p align="center">
  <br/><em>Concept from Figure 1: Genes define bands, chromosomes collect genes, bands are stacked for the CNN.</em>
</p>

### Key Benefits & Features 🚀

*   ✅ **Drastically Reduced Model Size:** ~91% fewer trainable parameters compared to the baseline.
*   ✅ **Faster Inference:** ~70% reduction in processing time for raw audio.
*   ✅ **Efficient:** Minimizes need for heavy preprocessing like downsampling.
*   ✅ **Effective:** Achieves comparable performance with only a minor (~4%) trade-off in F1-score.
*   🐍 Usable as a **Python package**.
*   🖥️ Includes an easy-to-use **Graphical User Interface (GUI)**.
*   📊 **TensorBoard** integration for monitoring training progress.

### Example Applications 🔍



<img width="1920" height="1080" alt="eso result" src="https://github.com/user-attachments/assets/ad65bc95-016a-4436-ab3c-8b441267198f" />


### Getting Started 🛠️

⚠️ **Warning:** ESO requires Python **< 3.13**. Please use Python 3.12 or earlier.

<<<<<<< HEAD
=======
#### Data Structure 

Organize your data in a folder named `Data`, containing the acoustic recordings in a subfolder `Audio` and the corresponding annotations in a subfolder `Annotations`.  
Each annotation file must have the **same name** as its associated audio file.

```
Data/
├── Audio/
│     ├──HGSM3AB_0+1_20160303_060100
│     ├──HGSM3AB_0+1_20160304_060000
│     ├──HGSM3AB_0+1_20160305_055900
│     └── ...
└── Annotations/
      ├──HGSM3AB_0+1_20160303_060100
      ├──HGSM3AB_0+1_20160304_060000
      ├──HGSM3AB_0+1_20160305_055900
      └── ...
```
#### Install Eso from the github 
>>>>>>> 8405179310318c6c8065cb85c9b7a7aabb2575c5
1. **Clone the repository**
    ```bash
    git clone https://github.com/***/ESO.git
    cd ESO
    ```

2. **Set up a virtual environment** (recommended)
    ```bash
    # On Linux/macOS
    python3.12 -m venv myenv
    source venv/bin/activate
    # On Windows : make sure your venv uses the correct Python version executable (3.12).
    python -m venv myenv
    venv\Scripts\activate
    ```

    Or with conda
    ```bash
    conda create --name myenv python==3.12 pip
    conda activate myenv
    ```

4. **Install PyTorch** based on your system configuration  
   (see [PyTorch](https://pytorch.org/get-started/locally/) to choose the correct version for your machine)
    ```bash
    pip install torch --index-url https://download.pytorch.org/whl/cu126
    ```

5. **Install other dependencies**
    ```bash
    pip install -r requirements.txt
    ```

#### Install Eso from pip 
1. **Set up a virtual environment** (recommended)
    ```bash
    python -m venv myenv
    # On Linux/macOS
    source venv/bin/activate
    # On Windows
    venv\Scripts\activate
    ```

    Or with conda
    ```bash
    conda create --name myenv python==3.12 pip
    conda activate myenv
    ```

2. **Install PyTorch** based on your system configuration  
   (see [PyTorch](https://pytorch.org/get-started/locally/) to choose the correct version for your machine)
    ```bash
    pip install torch --index-url https://download.pytorch.org/whl/cu126
    ```

3. **Install ESO with pip**
    ```bash
    pip install eso
    ```


### Running ESO 🏃

*   **Using the GUI:**
    ```bash
    python path/to/your/repository/eso_app.py 
    ```
    The GUI provides options to select data, configure hyperparameters, run ESO, and monitor progress (including TensorBoard).

*   **As a Python Package:**
    Import the necessary modules from the `eso` package in your Python scripts. (Refer to the documentation or notebook within the repository for specific usage details).
