# About task:
This notebook is an adaptation of the referenced notebook. My contributions include:
- **3x3 kernel**: Implemented a 3x3 kernel for the Quantum Convolutional layer. As the 3x3 kernel has 9 elements. So I needed a 9-qubit system.

- **Ansatz(e):** 4 Strongly Entangling layers(with CZ as imprimitive) are used as ansatze. A 1 layer system could do the work, but as I see in task_4, more layers give access to more Hilbert space, leading to lower cost and better accuracy.

- **Custom hybrid model:** The quantum circuit is used as a convolutional layer and produced 15x15x9 dimension of features. Which is then fed to the classical CNN. For the classical part, a Convolutional 3x3 kernel with 32 channels, followed by a maxpooling2D 2x2 filter is implemented. A dense layer with 64 nodes is applied before the 10 classifying dense nodes, and a dropout of 50% is imposed in the middle to handle the overfitting issue.

- **Dataset:** The actual dataset contains 10 classes of 60,000 training data and 10,000 testing data. As resource constraints, 350 data are used to train the model from the actual training set, and 50 and 100 data for validation and testing, respectively, from the testing set.

- **Hyperparameter tuning:** The model was started to train with a 0.001 learning rate. The ReduceLROnPlateau method is used to reduce the learning rate by 20% if no minimized validation loss is found for 3 consecutive epochs. Also, ImageDataGenerator from tensorflow-preprocessing is used to help the tuning process.

- **Performance comparison:** Performed Overall Accuracy(OA), Average Accuracy(AA), and Kappa Score measurement on the models. For the classical-quantum hybrid model, the overall, average, and kappa score is found to be 88%, 90.25%, and 86.6086% respectively(on 100 testing data). For the classical model, the metrics are 88%, 87.81%, and 86.6012% respectively(on 100 testing data). Though these metrics are almost equal, the hybrid model performed well on validation data.

# References
---

- [Quanvolutional Neural Networks](https://pennylane.ai/qml/demos/tutorial_quanvolution/) by Andrea Mari