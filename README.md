# rare_cell_diffusion

# Rare Cell Synthesis with Diffusion Models

This project uses a denoising diffusion probabilistic model (DDPM) to generate synthetic single-cell gene expression data, focusing on rare cell types such as hepatocytes. The model is trained on a subset of the Tabula Sapiens v2 dataset and compared with a simple Gaussian generator baseline.

## Project Structure

- `FinalProject_Simple_diffusion_model.ipynb` — Main notebook implementing training, generation, and evaluation
- `models/` — Contains saved model weights
- `plots/` — Output visualizations (UMAPs, loss curves)
- `data/` — Preprocessed subset from Tabula Sapiens (e.g. liver cells)

##  How It Works

### 1. Dataset

- **Source:** Tabula Sapiens v2  
- **Subset used:** Liver cells  
- **Target cell type:** Hepatocyte

### 2. Diffusion Model

- **Architecture:** MLP with time embedding
- **Noise schedule:** Linear beta schedule over 1,000 steps
- **Loss:** Mean Squared Error (MSE) between predicted and actual noise
- **Training:** Uses forward diffusion to corrupt real cells and trains model to reverse the noise

### 3. Synthetic Generation

- 200 synthetic cells are sampled using reverse diffusion from random noise
- A Gaussian generator baseline is also implemented for comparison

### 4. Evaluation

- **Metric:** Jensen–Shannon Divergence (JSD)
- **Visualization:** UMAP projections comparing real vs synthetic data
- **Result:** The Gaussian generator outperforms the DDPM under current setup
