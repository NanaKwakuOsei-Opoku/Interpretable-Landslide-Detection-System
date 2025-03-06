# [Landslide4Sense](https://www.iarai.ac.at/landslide4sense/): Interpretable Multi-sensor landslide detection project

## Contents

Landslides are a natural phenomenon with devastating consequences, frequent in many parts of the world. Thousands of small and medium-sized ground movements follow earthquakes or heavy rain falls. Landslides have become more damaging in recent years due to climate change, population growth, and unplanned urbanization in unstable mountain areas. Early landslide detection is critical for quick response and management of the consequences. Accurate detection provides information on the landslide exact location and extent, which is necessary for landslide susceptibility modeling and risk assessment. 
Recent advances in machine learning and computer vision combined with a growing availability of satellite imagery and computational resources have facilitated rapid progress in landslide detection. Landslide4Sense aims to promote research in this direction and challenges participants to detect landslides around the globe using multi-sensor satellite images. The images are collected from diverse geographical regions offering an important resource for remote sensing, computer vision, and machine learning communities. 

## Data Description

The Landslide4Sense dataset has three splits, training/validation/test, consisting of 3799, 245, and 800 image patches, respectively. Each image patch is a composite of 14 bands that include:

- **Multispectral data** from [Sentinel-2](https://sentinel.esa.int/web/sentinel/missions/sentinel-2): B1, B2, B3, B4, B5, B6, B7, B8, B9, B10, B11, B12.

- **Slope data** from [ALOS PALSAR](https://www.usgs.gov/centers/eros/science/usgs-eros-archive-radar-alos-palsar-radar-processing-system): B13.       

- **Digital elevation model (DEM)** from [ALOS PALSAR](https://www.usgs.gov/centers/eros/science/usgs-eros-archive-radar-alos-palsar-radar-processing-system): B14.

All bands in the competition dataset are resized to the resolution of ~10m per pixel. The image patches have the size of 128 x 128 pixels and are labeled pixel-wise.

**Download links:** [training](https://cloud.iarai.ac.at/index.php/s/KrwKngeXN7KjkFm) and [validation](https://cloud.iarai.ac.at/index.php/s/N6TacGsfr5nRNWr).   


![Logo](/image/Data_figure.png?raw=true "landslide_detection")

The _Landslide4Sense_ dataset is structured as follows:
```
├── TrainData/
│   ├── img/     
|   |   ├── image_1.h5
|   |   ├── ...
|   |   ├── image_3799.h5
│   ├── mask/
|   |   ├── mask_1.h5
|   |   ├── ...
|   |   ├── mask_3799.h5
├── ValidData/
|   ├── img/     
|   |   ├── image_1.h5
|   |   ├── ...
|   |   ├── image_245.h5
├── TestData/
    ├── img/     
        ├── image_1.h5
        ├── ...
        ├── image_800.h5
```

Note that the label files (mask files) are only accessible in the training set.

**Required packages and libraries:**

- Pytorch 1.10
- CUDA 10.2
- h5py


Alternatively, a **pretrained model** is available at    [here](https://cloud.iarai.ac.at/index.php/s/CgbjDRK6B5KYaLE).

## Evaluation Metric

The F1 score of the landslide category is adopted as the evaluation metric for the leaderboard:

![](https://latex.codecogs.com/svg.image?F_1=&space;2\cdot&space;\frac{precision\cdot&space;recall}{precision&plus;recall})

With the provided baseline method and the pretrained model, you can achieve the following result on the validation set:

| Validation Set | Precision | Recall | F1 Score |
| :--: | :--: | :--: | :--: |
| U-Net Baseline | 51.75 | 65.50 | 57.82 |

Note that the evaluation ranking is **ONLY** based on the **F1 score of the landslide category** in both validation and test phases.


