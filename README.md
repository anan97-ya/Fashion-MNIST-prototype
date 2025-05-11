**👗 Fashion-MNIST Prototype**

This project demonstrates a prototype for retrieving similar fashion-styled clothing items based on an uploaded input image.

---

**🎯 Objective**

The goal is to identify and recommend visually similar clothing items by learning edge-based features, which are more reliable than color or texture in grayscale datasets like Fashion MNIST.

---

**💡 Key Ideas**

* Dataset used: Fashion MNIST (grayscale, 28×28 images)
* Color was found to be an unreliable feature for identifying similar items
* Edge features worked significantly better for similarity detection
* A convolutional autoencoder was used, and only the encoder part was retained
* Cosine similarity outperformed Euclidean distance for comparing image embeddings

---

**⚙️ How It Works**

1. The user inputs a grayscale fashion image (28×28)
2. Optionally, edge detection like Sobel can be applied to enhance contours
3. The image is passed through a trained encoder that extracts a latent feature vector
4. This vector is compared against encoded vectors of all dataset images
5. Top-k most similar fashion items are retrieved based on similarity scores

---

**🧠 Model Architecture**

Encoder

* Conv2D(64, kernel size 3, ReLU) → MaxPooling2D
* Conv2D(32, kernel size 3, ReLU) → MaxPooling2D
* Output: Latent vector representing essential edge features

Decoder (for training only)

* Conv2D(16) → UpSampling2D
* Conv2D(32) → UpSampling2D
* Conv2D(1, sigmoid) → Reconstructed image

---

**🔍 Observations**

* Edges carried more meaningful information for visual similarity than raw pixels
* Cosine similarity gave more accurate results than Euclidean distance in matching
* Edge detection enhanced the model's performance in fetching similar images

---

**🚀 Future Improvements**

* Use a more diverse, higher-resolution dataset like DeepFashion or Fashion Product Images
* Integrate Sobel or Canny edge detection into the preprocessing pipeline
* Build a simple frontend for user input and display of similar results
* Experiment with more advanced architectures like VAEs or Siamese networks

---

**🛠 Technologies Used**

* Python
* TensorFlow / Keras
* NumPy
* Scikit-Image
* Matplotlib

