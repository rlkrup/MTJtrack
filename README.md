# MTJtrack
Trained networks for tracking MTJ position in B-mode ultrasound images using DeepLabCut

## Introduction
Each of the zip files contains a complete DeepLabCut project which has been trained for tracking the medial gastrocnemius MTJ in cine-B ultrasound video. Each contains a trained neural network ready for use to predict MTJ location in ultrasound video. The 5 projects titled "IterationRun33_X" have been trained with 480 manually tracked MTJ images (40 frames each from five different combinations of 12 subjects from a pool of 15 subjects) collected during walking. The project titled "Production2" has been trained with 3482 manually tracked MTJ images from all 15 subjects across walking and maximal voluntary isometric plantarflexion tasks.

## Setup
### Step 1: Install DeepLabCut
To get started, install DeepLabCut according to the instructions at (https://deeplabcut.org).

### Step 2: Choose Project and Extract
Choose one of the zip files from this GitHub and extract it to a location on your machine.

### Step 3: Edit Config File
Open the project folder you extracted and open the file "config.yaml" in a text editor. Update the "project_path: ..." line to reflect where you have extracted the project on your machine. NOTE FOR WINDOWS USERS: Your file path cannot contain single backslashes (\). Replace all of the backslashes (\) with forwardslashes (/) or double-backslashes (\\) in your path to prevent errors.

Example for Linux/Mac: 
```
project_path: /User/Desktop/IterationRun33_5-CallumFunk-2020-06-19
```

Example for Windows:
```
project_path: C:\\User\\user\\Desktop\\Production2-CallumFunk-2020-12-18
```
### Step 4: Analyze Videos with DeepLabCut
After activating your conda environment in command prompt or terminal (see DeepLabCut GitHub for more details), open ipython:
```
ipython
```
Import the DeepLabCut package:
```python
import deeplabcut
```
Define the path to the "config.yaml" file you edited earlier in Step 3. NOTE FOR WINDOWS USERS: Your file path cannot contain single backslashes (\). Replace all of the backslashes (\) with forwardslashes (/) or double-backslashes (\\) in your path to prevent errors.
```python
config_path = "C:/path/to/importedProjectFolder/config.yaml"
```
Define the path to a folder containing ultrasound videos you wish to track:
```python
videos = ["C:/path/to/folderOfVideosToBeAnalyzed"]
```
Analyze the videos using the pretrained model. This will produce .csv files containing the predicted MTJ location for each frame.
```python
deeplabcut.analyze_videos(config_path, videos)
```
Create a labeled video using the predictions:
```python
deeplabcut.create_labeled_videos(config_path, videos)
```
