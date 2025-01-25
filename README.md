# Audio-Based Detection Using YAMNet  

This project leverages **YAMNet** for audio-based detection to distinguish between a helicopter, a drone, and background noise.  

---

## **Prerequisites**  

Before proceeding, make sure you have the following tools installed on your system:  

- **Miniconda**: You can install Miniconda by following the instructions at [Miniconda Installation Guide](https://docs.anaconda.com/miniconda/install/).  
- **Git**: Ensure Git is installed to clone the repository. You can install Git by following the instructions [here](https://git-scm.com/downloads/).  

---

## **Troubleshooting**  

### 1. **CUDA Errors**  

If you encounter errors related to CUDA, such as missing `nvcc` or library paths, ensure the following:  

1. **Install CUDA and CUDA Toolkit**  
   Follow the official [NVIDIA Installation Guide](https://developer.nvidia.com/cuda-downloads) to install CUDA and the CUDA Toolkit.  

2. **Add CUDA Paths to zshrc (or bashrc)**  
   For GPU acceleration, ensure the CUDA paths are correctly set up in your shell configuration:  

   - Open your `.zshrc` file (use `.bashrc` if you're using Bash):  
     ```bash
     nano ~/.zshrc
     ```

   - Add the following lines:  
     ```bash
     # CUDA paths
     export CUDA_HOME=/usr/local/cuda
     export PATH=$CUDA_HOME/bin:$PATH
     export LD_LIBRARY_PATH=$CUDA_HOME/lib64:$LD_LIBRARY_PATH
     ```

   - Save the file and reload your shell:  
     ```bash
     source ~/.zshrc
     ```

   If you're using Bash, replace `.zshrc` with `.bashrc` in the commands above.

### 2. **Operating System Compatibility**  

This project was developed on **Fedora 41**. If you're using a different operating system, you might encounter package or path differences. Adjust accordingly.

---

## **Repository Setup**  

1. **Clone the Repository**  
   Use Git to clone the repository to your local system:  
   ```bash
   git clone https://github.com/arnavpathak2003/drone_audio_classification.git
   cd drone_audio_classification
   ```

2. **Create and Activate the Environment**  
   Create a Conda environment using the `environment.yml` file and activate it:  
   ```bash
   conda env create -f environment.yml
   conda activate audio
   ```

---

## **Usage**  

1. **Model Options**  

   - You can **directly use the pre-trained model** available in the repository:  
     ```bash
     audio_classifier.keras
     ```  
     This file can be used to perform classification without retraining.  

   - Alternatively, you can **train the model from scratch** by running the provided training notebook.

2. **Adding New Data**  

   If you'd like to include more data for training:  

   - Add the audio files in `.wav` format.  
   - Name the files according to the target class in **uppercase** as follows:  
     - **BACKGROUND** for background noise  
     - **DRONE** for drone sounds  
     - **HELICOPTER** for helicopter sounds  

   After adding new data, retrain the model using the training notebook.

3. **Run the Detection Script**  

   Use the provided script or notebook to classify audio inputs into one of the following classes:  

   - Helicopter  
   - Drone  
   - Background Noise  
