


## AI Yoga Coach

The AI Yoga Coach is a project that combines the power of deep learning and React.js to create an interactive yoga coaching application. It utilizes TensorFlow's PoseNet library to extract key data points from users' yoga poses, allowing for real-time feedback and guidance.

## Project Structure

### Overview
```
AI-yoga-coach/
├── frontend/                    # React.js web application
├── classification model/         # Python ML model training and data processing
└── README.md                   # Project documentation
```

### Frontend Structure (`/frontend`)
The frontend is a React.js application that provides the user interface for the AI Yoga Coach.

#### Core Files
- **`package.json`** - Dependencies and npm scripts configuration
- **`src/App.js`** - Main application component with routing setup
- **`src/index.js`** - React DOM entry point
- **`src/utilities.js`** - Utility functions for pose detection and canvas drawing
- **`src/model.json`** - TensorFlow.js model configuration
- **`src/group1-shard1of1.bin`** - Model weights binary file

#### Pages (`/src/pages`)
- **`Home/Home.js`** - Landing page with navigation
- **`Yoga/Yoga.js`** - Main yoga pose detection and coaching interface
- **`About/About.js`** - Information about the project
- **`Test/Test.js`** - Testing interface for pose detection
- **`Tutorials/Tutorials.js`** - Yoga tutorials (commented out in routing)

#### Components (`/src/components`)
- **`DropDown/DropDown.js`** - Yoga pose selection dropdown
- **`Instrctions/Instructions.js`** - Pose instructions display
- **`PoseStart/PoseStart.js`** - Pose starting component

#### Utils (`/src/utils`)
- **`data/`** - Pose detection data structures and constants
- **`helper/`** - Helper functions for pose detection
- **`images/`** - Static image assets
- **`music/`** - Audio files for pose feedback
- **`pose_images/`** - Reference images for yoga poses

#### Key Features in Frontend
- Real-time pose detection using MoveNet model
- Webcam integration for live pose tracking
- Canvas overlay for skeleton visualization
- Pose accuracy calculation and feedback
- Timer and performance tracking
- Audio feedback for correct poses

### Classification Model Structure (`/classification model`)
The classification model directory contains Python scripts for training the yoga pose classification model.

#### Core Python Files
- **`training.py`** - Main training script for the pose classification model
  - Loads training/test data from CSV files
  - Defines neural network architecture (128→64→output layers)
  - Trains model with Adam optimizer and categorical crossentropy
  - Converts trained model to TensorFlow.js format
  - Includes callbacks for model checkpointing and early stopping

- **`data.py`** - Data structures and utilities for pose estimation
  - `BodyPart` enum defining 17 body keypoints
  - `Point`, `Rectangle`, `KeyPoint`, `Person` classes
  - Functions for converting model output to structured data

- **`proprocessing.py`** - Data preprocessing pipeline
  - Downloads MoveNet Thunder model if not present
  - Processes yoga pose images to extract keypoints
  - Generates CSV files with landmark coordinates
  - Combines per-class CSVs into training/test datasets
  - Applies detection thresholds for quality control

#### Model Files
- **`movenet_thunder.tflite`** - MoveNet Thunder model for pose detection (12.5MB)
- **`weights.best.hdf5`** - Best trained model weights
- **`model/`** - Directory for TensorFlow.js converted model

#### Data Files
- **`train_data.csv`** - Training dataset with pose landmarks (623KB)
- **`test_data.csv`** - Test dataset with pose landmarks (361KB)
- **`csv_per_pose/`** - Individual CSV files per yoga pose class

#### Yoga Poses Data (`/yoga_poses`)
- **`train/`** - Training images organized by pose classes
- **`test/`** - Test images for model evaluation

#### Supported Yoga Poses
The system recognizes 7 different yoga poses:
1. **Vrukshasana** (Tree Pose)
2. **Utkasana** (Chair Pose)
3. **Bhujangasana** (Cobra Pose)
4. **Veerabhadrasana** (Warrior Pose)
5. **Adhomukasana** (Downward Facing Dog)
6. **Sarvangasana** (Shoulderstand)
7. **Trikonasana** (Triangle Pose)

#### Model Architecture
- **Input**: 34-dimensional pose embedding (17 keypoints × 2 coordinates)
- **Hidden Layers**: 
  - Dense layer with 128 neurons (ReLU6 activation)
  - Dropout layer (50% dropout rate)
  - Dense layer with 64 neurons (ReLU6 activation)
  - Dropout layer (50% dropout rate)
- **Output**: Dense layer with softmax activation for 7 pose classes
- **Training**: 200 epochs, batch size 16, early stopping with patience 20

#### Key Technologies
- **TensorFlow/Keras**: Model training and neural network implementation
- **TensorFlow.js**: Model conversion for web deployment
- **Pandas**: Data manipulation and CSV handling
- **NumPy**: Numerical computations
- **MoveNet**: Google's pose detection model
- **tqdm**: Progress bars for data processing

## Features

- Real-time Pose Detection: The AI Yoga Coach uses TensorFlow's PoseNet model to accurately detect and track users' yoga poses in real-time. This allows for precise analysis of posture and alignment.

- Interactive Feedback: With the help of deep learning algorithms, the AI Yoga Coach provides instant feedback on users' yoga poses. It identifies common mistakes and suggests corrections, helping users improve their form and technique.

- Personalized Training: The application adapts to individual users by leveraging deep learning techniques. It learns from each user's movements and progress, tailoring future coaching sessions to their specific needs and goals.

- User-Friendly Interface: The AI Yoga Coach features a sleek and intuitive user interface built with React.js. The interface provides a seamless experience for users to interact with the application, view their progress, and access instructional resources.

## Technologies Used

- React.js: The frontend of the AI Yoga Coach is developed using React.js, a popular JavaScript library for building user interfaces. React.js enables the creation of interactive and dynamic components that enhance the user experience.

- TensorFlow: TensorFlow, an open-source machine learning framework, powers the deep learning capabilities of the AI Yoga Coach. It enables training and testing of the pose estimation model using PoseNet, allowing for accurate detection of yoga poses.

- PoseNet: The AI Yoga Coach utilizes TensorFlow's PoseNet, a pre-trained deep learning model specifically designed for pose estimation. It accurately estimates the locations of key body joints and provides valuable data points for analysis.

## Installation

To run the AI Yoga Coach locally, follow these steps:

1. Clone the repository:

   ```bash
   git clone https://github.com/24vishwas/AI-yoga-coach.git
   ```

2. Install dependencies:

   ```bash
   cd AI-yoga-coach/frontend
   npm install
   ```

3. Run the application:

   ```bash
   npm start
   ```

4. Open your web browser and visit `http://localhost:3000` to access the AI Yoga Coach.

## Contributing

Contributions to the AI Yoga Coach project are welcome! If you would like to contribute, please follow these steps:

1. Fork the repository on GitHub.

2. Create a new branch with a descriptive name:

   ```bash
   git checkout -b feature/my-feature
   ```

3. Make your changes and ensure the code follows the project's style guide.

4. Test your changes thoroughly.

5. Commit your changes with a clear and descriptive message:

   ```bash
   git commit -m "Add my feature"
   ```

6. Push your changes to your forked repository.

   ```bash
   git push origin feature/my-feature
   ```

7. Open a pull request on the main repository, describing your changes and why they should be merged.

## License

The AI Yoga Coach project is licensed under the [MIT License](LICENSE). Feel free to modify and distribute the application according to the terms of this license.

## Acknowledgements

The development of the AI Yoga Coach was made possible by various open-source projects and libraries. We would like to express our gratitude to the developers and contributors of the following:

- React.js
- TensorFlow
- PoseNet

We also extend our appreciation to the yoga community for their valuable input and feedback during the development process.
#   y o g a - p o s e  
 