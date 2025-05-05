# VAE-for-Smiling-vs.-Non-Smiling-Face-Generation
Implementation of VAE and Beta-VAE , Generation of new facial images,Smile intensity manipulation using latent vector arithmetic

---

##  Project Level

Graduate-level deep learning project focused on generative modeling using a Variational Autoencoder (VAE).
---

##  Project Highlights

* Implementation of VAE and Beta-VAE with different hyperparameters.
* Generation of new facial images based on learned latent representations.
* Comparison of models trained with normalized and unnormalized data.
* Smile intensity manipulation using latent vector arithmetic.

Sure! Here’s a concise and professional **Project Description** section that you can place right after the title in your `README.md`:

---

##  Project Description

This project implements a **Variational Autoencoder (VAE)** to learn and generate facial images, specifically focusing on distinguishing and manipulating **smiling vs. non-smiling** expressions. By training on a labeled facial image dataset, the model learns a compressed latent representation of faces that can be used for **reconstruction, generation, and expression control**. The project explores different network architectures, training strategies, and hyperparameter settings—such as batch size, normalization, and learning rate scheduling—to optimize the model's performance. Additionally, latent space manipulation is applied to smoothly adjust the **intensity of a smile**, showcasing the model's ability to capture semantically meaningful features.

---

##  Objective

To train a VAE model on facial images (smiling and non-smiling) and evaluate its performance in reconstructing and generating realistic images. The project also explores how latent space manipulation can be used to control smile intensity.

##  Data Collection

* **Source**: Google Drive
* **Dataset Structure**:

  * `train/`: 600 smiling + 603 non-smiling images
  * `test/`: used for visualization and final evaluation

##  Preprocessing & Feature Extraction

* Images converted to RGB and resized from `[3, 64, 64]` to `[3, 128, 128]`.
* Normalization with mean `[0.5, 0.5, 0.5]` and std `[0.5, 0.5, 0.5]`.
* Dataset shuffled and split into 80% training, 20% validation/test.
* Batching applied for memory efficiency and training stability.

##  Model Architecture

* Custom **VAE** implemented with:

  * `Conv2D` layers followed by `BatchNorm2D` and `Dropout2D`
  * Latent space dimension: 120 (also tested with 200)
  * ReLU activation
  * Reparameterization using mean and log variance
* **Beta-VAE**: tested with β = 10, 50
* Loss Function:

  * `MSELoss` for reconstruction
  * `KL Divergence` as regularization term

##  Training & Evaluation

* Optimizer: Adam with initial learning rate 0.0005
* Scheduler: `ReduceLROnPlateau` for dynamic LR adjustment
* Batch Sizes: Tested with 32, 64, 128
* Epochs: 125–200
* Validation used to select top 2 models

###  Best Models

**Model 1**

* 150 Epochs
* Batch size: 128
* Data: Unnormalized

**Model 2**

* 200 Epochs
* Batch size: 32
* Data: Unnormalized

##  Results

* Gradual reduction of combined loss from \~20,000 to \~4,000
* KL Loss and Reconstruction Loss in competitive trade-off
* Model stability observed after \~80 epochs
* Beta-VAE showed less effective reconstruction due to KL penalty

##  Sample Outputs

* **Reconstruction from Real Images**:
  Both models produced realistic outputs resembling the input.

![image](https://github.com/user-attachments/assets/8e06659b-674a-4fcb-89ec-ff1d5457cd10)
![image](https://github.com/user-attachments/assets/c421139b-a5ca-4e30-8ce3-a89d8619c3d1)
![image](https://github.com/user-attachments/assets/89426e83-ecb5-4100-8b14-718ab29d4b27)

* **Generation from Noise**:
  Latent space sampled to generate novel faces.
  ![image](https://github.com/user-attachments/assets/1cf9e892-d6b5-4c80-861f-51968c2b5e7d)

* **Smile Manipulation**:
  By subtracting latent vectors of non-smiling/smiling classes and applying to test images, different smile intensities were synthesized. (Note teeth emerge in big smiles :) )
![image](https://github.com/user-attachments/assets/e2858e84-3807-4e8a-b370-341510c9ff48)

##  Conclusion

The project successfully demonstrated the ability of VAE to learn meaningful facial representations. Latent space arithmetic enabled smile control, showing the model's interpretability. Beta-VAE introduced regularization but hindered image fidelity, making standard VAE (β=1) a better choice for this task.

---
