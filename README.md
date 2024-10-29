# Archer Gesture Recognition Project

This project uses computer vision and gesture recognition to track hand movements and estimate arrow speed in archery. The project captures key hand gestures, such as "open palm" and "closed fist," to calculate elapsed time during an arrow release, allowing for an estimation of arrow speed.

## Requirements

Before running this project, make sure you have installed all dependencies and downloaded the necessary model file.

### Prerequisites

1. **Python**: Make sure you have Python installed (version 3.8 or higher is recommended).
2. **Virtual Environment** (optional but recommended): 
   ```bash
   python -m venv myenv
   source myenv/bin/activate  # On Windows: myenv\Scripts\activate
   ```

### Installation

1. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

2. Download the MediaPipe Gesture Recognizer model file:
   ```bash
   wget -q https://storage.googleapis.com/mediapipe-models/gesture_recognizer/gesture_recognizer/float16/1/gesture_recognizer.task
   ```
   Alternatively, you can download it manually from the URL if `wget` is not available.

3. Place the downloaded `gesture_recognizer.task` file in the root directory of this project.

### Usage

To start the gesture recognition application, run the following command:
```bash
python main.py
```

This will open a camera window where hand gestures can be tracked. Make sure your camera is enabled.

## Features

- Detects hand gestures, such as "open palm" and "closed fist."
- Starts a timer when the hand is in an open palm position and stops it upon detecting a closed fist gesture.
- Calculates the arrow speed based on user input distance and timer data.

## Physics Assumptions, Formula, and Limitations

### Assumptions

1. **Air Resistance and Other Forces**: For simplicity, air resistance and factors such as gravity's effect during short distances are ignored.
2. **Straight Line Motion**: The arrow is assumed to move in a straight line between the archer and the target.
3. **Constant Release Power**: The release power from the archer's hand is considered constant, disregarding minor fluctuations.

### Formula Used

The velocity of the arrow is estimated using the basic physics formula:
\[
\text{velocity} = \frac{\text{distance}}{\text{time}}
\]

where:
- **distance** is the user-provided distance from the archer to the target,
- **time** is measured from the moment of hand release (`open palm`) to the moment the arrow stops (detected by `closed fist`).

### Limitations

This calculation method has some limitations:
- **Accuracy**: The calculation may not be precise due to assumptions made about air resistance, arrow mass, and environmental factors.
- **Simple Motion Assumption**: Real archery motion includes slight curves due to gravity, especially over longer distances.
- **Environmental Variables**: Factors like wind speed, arrow weight, and bow strength, which are not accounted for, may impact the result.

### Additional Guidelines

For more detailed guidance on the assumptions, derivation of the formula, and safety recommendations, please refer to the supplementary PDF documentation:
[Detailed Documentation and Assumptions](https://drive.google.com/drive/folders/1pBqB0eKYWprzli0Fv4QVkCHmrnnqPDS7?usp=sharing)

### Troubleshooting

- **Model Not Found**: If you receive a model file error, verify that `gesture_recognizer.task` is located in the project root directory.
- **Camera Issues**: Ensure that no other applications are using the camera and that your camera drivers are up to date.

### License

This project is open-source and available under the [MIT License](LICENSE).
