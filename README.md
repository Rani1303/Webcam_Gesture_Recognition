# Webcam_Gesture_Recognition

This project demonstrates the integration of a pre-trained gesture recognition model into a Flask backend API. The goal is to classify American Sign Language (ASL) signs from live webcam feeds. This project uses a convolutional neural network (CNN) model trained on ASL datasets, providing an easy-to-use web interface for real-time gesture recognition.

## Repository Overview

The repository used for the pre-trained gesture recognition model is from Kaggle, specifically [Sign Language Recognition using VGG16 and ResNet50](https://www.kaggle.com/code/rahulmakwana/sign-language-recognition-vgg16-resnet50). This repository was chosen based on several factors:

- **Model Accuracy**: The VGG16 and ResNet50 models are renowned for their high accuracy in image classification tasks, making them ideal for gesture recognition.

```
VGG16:
Accuracy for test images: 99.992 %
Accuracy for evaluation images: 100.0 %

RESNET50:
Accuracy for test images: 99.95 %
Accuracy for evaluation images: 100.0 %

```

- **Documentation Quality**: The repository includes well-documented code with explanation, which simplifies the understanding and integration of the models.
- **Ease of Integration**: The modular nature of the code and clear instructions for loading and using the pre-trained models ensure seamless integration into the Flask backend.

## Project Structure

```bash
templates
└── index.html
app.py
model.h5
requirements.txt
edge_image.py
readme.md
```


### File Descriptions

- **`app.py`**: The main Flask application script that sets up the web server, handles live video processing, and returns predictions.
- **`model.h5`**: The pre-trained gesture recognition model file.
- **`requirements.txt`**: A list of Python dependencies required to run the application.
- **`index.html`**: The homepage of the web application where users can start and stop the live camera feed.
- **`edge_image.py`**: A script to process images for edge detection and save them.
- **`readme.md`**: Documentation file for the project.

## Setup and Installation

Follow these steps to set up and run the project on your local machine:

### Prerequisites

- Python 3.6 or higher
- pip (Python package installer)

### Installation

1. **Clone the repository**

    ```bash
    git clone https://github.com/Rani1303/Webcam_Gesture_Recognition
    cd Webcam_Gesture_Recognition
    ```

2. **Create a virtual environment**

    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3. **Install dependencies**

    ```bash
    pip install -r requirements.txt
    ```

4. **Ensure you have the `model.h5` file in the project directory**. If not, download it from the github repository and place it in the project directory.

### Running the Application

1. **Start the Flask server**

    ```bash
    python app.py
    ```

2. **Open your browser and go to**

    ```
    http://127.0.0.1:5000/
    ```

3. **Start the camera**

    - On the homepage, when the "Allow Camera" button is clicked and camera permission is granted successfully, the button becomes disabled, and the "Start Camera" button becomes enabled.
    - Clicking the "Start Camera" button sends a POST request to start the camera, which triggers the camera stream.
    - Clicking the "Stop Camera" button sends a POST request to stop the camera stream.

## Code Explanation

### `app.py`

The main Flask application script handles the core functionalities:

- **Index Route (`/`)**: Renders the homepage (`index.html`).
- **Video Feed Route (`/video_feed`)**: Streams live video frames from the webcam.
- **Set Threshold Route (`/set_threshold`)**: Updates the edge detection thresholds based on user input.
- **Start Camera Route (`/start_camera`)**: Starts the webcam.
- **Stop Camera Route (`/stop_camera`)**: Stops the webcam.

### Image Preprocessing

The `preprocess_image` function converts the captured hand image to grayscale, applies Gaussian blur, performs edge detection, and prepares the image for model prediction.

### Prediction and Results

The model makes a prediction, and the predicted label is displayed on the video feed along with the current sentence being formed.

## Demo

https://vimeo.com/952325330

## Conclusion

This project provides a robust and efficient method to integrate a pre-trained gesture recognition model into a Flask web application for real-time ASL sign recognition. By following the instructions, you can set up the project locally and start recognizing ASL signs from live webcam feeds. The integration of the pre-trained model ensures high accuracy and ease of use, making it a practical solution for gesture recognition tasks.

## License

[MIT](LICENSE) © 2024 Rani
