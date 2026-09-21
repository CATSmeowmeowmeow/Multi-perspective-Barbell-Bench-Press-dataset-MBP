# 📘 Multi-perspective Barbell Bench Press dataset (MBP)

## 1. Overview
This dataset contains **multi-view video recordings** of the barbell bench press exercise.  
It is designed for **motion analysis, error detection, and biomechanics research**, with three synchronized camera views:  
- **Lateral view (side)**  
- **Top view (overhead)**  
- **Rear view (behind the bench)**  

The dataset includes **correct** and **incorrect** bench press techniques, annotated with barbell coordinates, joint coordinates and joint angles.

---

## 2. Dataset Structure
The dataset is organized by class → subject → video_dataset/coordinate_dataset/angle_dataset → lateral_view/top_view/rear_view → repetition.  
Each subject folder contains three main parts: **video_dataset**, **coordinate_dataset**, and **angle_dataset**.

```
correct/
└── subject_1_exp1/
    ├── video_dataset/
    │   ├── lateral_view/
    │   │   └── *.avi
    │   ├── top_view/
    │   │   └── *.avi
    │   └── rear_view/
    │       └── *.avi
    ├── coordinate_dataset/
    │   ├── lateral_view/
    │   │   └── *.txt
    │   ├── top_view/
    │   │   └── *.txt
    │   └── rear_view/
    │       └── *.txt
    └── angle_dataset/
        ├── top_view/
        │   ├── left_torso_arm/
        │   │   └── *.txt
        │   └── right_torso_arm/
        │       └── *.txt
        └── rear_view/
            ├── left_shoulder/
            │   └── *.txt
            ├── right_shoulder/
            │   └── *.txt
            ├── left_elbow/
            │   └── *.txt
            └── right_elbow/
                └── *.txt
```

### 🔹 Special Notes
- **Multi-error samples** (e.g., right_low + wrist_bending) are listed in the file **`multierror.csv`** at the dataset root.  
- This file maps each subject repetition to multiple error labels.  

---

## 3. Classes
The dataset contains **6 primary classes**:  
1. correct  
2. wrist_bending_backward  
3. tilting_to_the_left  
4. tilting_to_the_right  
5. elbows_flaring  
6. scapular_protraction  


---

## 4. Data Modalities
- **Video data**: `.avi` format, three camera views.  

- **Coordinate data**: `.txt` files with 2D coordinates of barbell and joints.  
  Each `.txt` file contains **frame-wise measurements** depending on the camera view:

  - **lateral_view** (barbell bounding box)  
    Format: `frame, x_center, y_center, width, height`  

  - **rear_view** (6 keypoints, each line stores all x,y pairs in order)  
    IDs:  
    ```
    0: left shoulder  
    1: right shoulder  
    2: left elbow  
    3: right elbow  
    4: left wrist  
    5: right wrist
    ```

  - **top_view** (8 keypoints, each line stores all x,y pairs in order)  
    IDs:  
    ```
    0: right shoulder  
    1: left shoulder  
    2: right hip  
    3: left hip  
    4: right elbow  
    5: left elbow  
    6: right wrist  
    7: left wrist
    ```

- **Angle data**: Computed joint angles for biomechanical analysis.  

- **Pre-extracted Feature Data**: `.json` format containing wrist/barbell trajectories and body postures for efficient feature analysis and model training.  
👉 **Note**: All coordinate, feature, and angle data were generated using our own **YOLO-based pose estimation models**, which were trained specifically on this dataset for detecting the barbell and upper-body keypoints.

---

## 5. Statistics
- **Total samples**: ~7,700 repetitions  
- **Participants**: >100 subjects (male & female)  
- **Views per repetition**: 3 synchronized videos  
- **Annotations**: Barbell endpoint coordinates, joint coordinates, joint angles  

---


## 6. Download
- 📦 **Download Dataset**: [BenchpressDataset.zip](https://catslab.ee.ncku.edu.tw/public/BenchpressDataset.zip)  
  *(Includes JSON-formatted pre-extracted feature data tracking wrist/barbell trajectories and body postures, raw video recordings, coordinate annotations, and angle data)*

---

## 7. License
This dataset is provided for **academic research purposes only**.  
For commercial use, please contact the dataset authors.

---

## 8. Citation
If you use this dataset, please cite:

```
@dataset{benchpress_multiview_2025,
  title     = {Multi-perspective Barbell Bench Press dataset (MBP)},
  author    = {Hsiao-Ching Lin and Collaborators},
  year      = {2025},
  publisher = {National Cheng Kung University}
}
```


