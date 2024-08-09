# About task (task_5_1_cnn.ipynb)
---

The project task for Quantum Machine Learning for Conspicuity Detection in Production requires the implementation of a Quantum Machine Learning Model to detect anomalies in production. In this notebook, I will implement a Classical CNN Model to classify all provided classes using all given data. This CNN model is one of my previous implementations used to detect tumors in brain MRI images. In the next notebooks, I will implement the QML model. My contributions to this task include:

- **Dataset:** Downloading the dataset from Kaggle to Colab and importing it with the correct path was a tedious job. The actual dataset contains 6 classes of 22,638 training data and 5,581 testing data. The model was trained with the whole training data, and 10% was used to validate the training process. The final performance was measured using all the testing data.

- **Preprocessing:** Image dimension was reduced and preprocessing was done to make it work within the limited resources.

- **Hyper-Parameter Tuning:** ReduceLROnPlateau was implemented to optimize the learning rate, and CSVLogger was used to record the training process. The best-performing model was saved in keras format and used to measure the performance with testing data.

- **Performance Measurements:** Overall Accuracy (OA), Average Accuracy (AA), Kappa Score, and ROC curve were implemented to measure the model performance.




# About task (task_5_2_hybrid.ipynb)
---

This Notebook is an extension of my previous notebooks: task_3 and task_5.1_cnn. My contributions to this notebook include:

- **Preprocessing**: The actual dataset contains 6 classes of 22,638 training data and 5,581 testing data. This time I choose only two classes: good weld(0), and burn through(1). As resource constraints, the images were resized from 800x974 to 32x32 and, the model was trained with only 100 training data, from which 10% data was used to validate the training process. And lastly 50 data for testing from the testing set for final testing. Furthermore, I trained the model with only 5 epochs, as I chose lower data

- **3x3 kernel:** Implemented a 3x3 kernel for the Quantum Convolutional layer. As the 3x3 kernel has 9 elements. So I needed a 9-qubit system. (from task_3)

- **Ansatz(e):** 4 Strongly Entangling layers(with CZ as imprimitive) are used as ansatze. A 1 layer system could do the work, but as I see in task_4, more layers give access to more Hilbert space, leading to lower cost and better accuracy. (from task_3)

- **Custom hybrid model:** The quantum circuit is used as a convolutional layer and produces 15x15x9 dimensions of features. Which is then fed to the classical CNN. For the classical part, a Convolutional 3x3 kernel with 64 channels, followed by a maxpooling2D 2x2 filter is implemented. A dense layer with 64 nodes is applied before the 2 classifying dense nodes, and a dropout of 50% is imposed in the middle to handle the overfitting issue.

- **Quantum Circuit as a layer**: This time I combined the Quantum Circuit with the Classical CNN model. I used tf.py_function to wrap the output from the quantum circuit to tensorflow and implemented a new layer, QuantumConv2D.  Furthermore, I modified the model to handle data from batch mode.

- **Hyper-Parameter Tuning:** ReduceLROnPlateau was iplemented to optimize the learning rate, and CSVLogger was used to record the training process. The best-performing model was saved in Keras format and used to measure the performance with testing data. (from task_5.1_cnn)

- **Performance Measurements:** Overall Accuracy (OA), Average Accuracy (AA), Kappa, Precision, Recall, Specificity, and F1 Score were implemented to measure the model performance.
