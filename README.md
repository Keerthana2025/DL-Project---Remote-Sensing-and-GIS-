🛰️ Deep Learning-Based Object Detection from High-Resolution Satellite Imagery

Internship project completed under the Winter Training Program on Space Science Technology, India Space Academy — Department of Space Education, India Space Week.

Subject: Remote Sensing and GIS Author: Keerthana S, Ethiraj College Supervisor: Ms. Alisha Sinha

📌 Objective

To detect, localize, and map objects such as buildings, roads, water bodies, and burned areas from high-resolution satellite imagery using Deep Learning techniques. The project combines AI-based classification with GIS workflows to support urban planning, disaster management, environmental monitoring, and resource management.

🌍 Study Area

Location: Hyderabad, India

Hyderabad was chosen for its diverse land cover — urban settlements, water bodies, roads, and vegetation — making it well suited for testing object detection on satellite imagery. The Area of Interest (AOI) was delineated using QGIS and Google Earth Engine (GEE).

🗂️ Data Used
Item	Details
Satellite	Sentinel-2 (2A / 2B)
Sensor	Multispectral Instrument (MSI)
Spatial Resolution	10 m (Visible & NIR), 20 m (Red Edge & SWIR), 60 m (Atmospheric bands)
Temporal Resolution	5-day revisit
Date Range	01 Jan 2023 – 31 Dec 2023
Cloud Filter	< 10% cloud cover

Data Sources

Copernicus Open Access Hub
Google Earth Pro (reference & interpretation)

Preprocessing: resizing, normalization, cloud masking, and augmentation, followed by manual/semi-automated annotation of object classes.

🧭 Methodology

The workflow integrates cloud-based processing in Google Earth Engine (GEE) with local GIS refinement in QGIS:

Define AOI — polygon drawn/imported in GEE.
Load & Filter Imagery — Sentinel-2 SR, filtered by AOI, date range, and cloud cover; median composite generated.
Spectral Indices — NDVI and NDWI computed to separate vegetation, water, and built-up areas.
Texture Features — GLCM (Gray Level Co-occurrence Matrix) used to improve detection of structured objects like buildings and roads.
Training Samples — polygons digitized per class and merged into a labeled FeatureCollection.
Classification — Random Forest classifier trained on spectral + texture bands and applied to the full AOI.
Object Mask Extraction — specific classes (e.g., buildings) isolated using logical operations.
Export — classified rasters/masks exported to Google Drive as GeoTIFFs.
GIS Integration — outputs imported into QGIS for vectorization, validation, statistics (counts, area, density), and final map layout.
Spectral Indices Used
NDVI = (B8 - B4) / (B8 + B4)   # Normalized Difference Vegetation Index
NDWI = (B3 - B8) / (B3 + B8)   # Normalized Difference Water Index

💻 Tech Stack

Google Earth Engine (JavaScript API) — imagery loading, filtering, spectral index computation, Random Forest classification
Python — numpy, matplotlib, scikit-learn, scikit-image for classification, confusion matrix evaluation, and visualization
QGIS — vector conversion, spatial statistics, thematic map production
Models referenced: Random Forest, U-Net, YOLOv3, Mask R-CNN

📊 Results

Integration of DL-based classification with GIS workflows enabled accurate identification, vectorization, and spatial analysis of thematic features.
NDVI and NDWI improved class separability between vegetation, water, and built-up land.
A confusion matrix was used to evaluate classification accuracy across Buildings, Roads, Water, and Burned classes, showing strong diagonal accuracy (e.g., Water: 99/100, Buildings: 95/100).
Classified rasters were converted to vector layers with symbology (buildings – red, roads – blue, vegetation – green, water – yellow) for final thematic maps.

⚠️ Limitations
Data limitations — cloud cover, shadows, and seasonal variation can reduce accuracy.
Model dependency — performance relies heavily on quality/quantity of training samples.
Resolution constraints — very fine-scale features may be missed at the given spatial resolution.
Computational cost — training deep models (U-Net, YOLO) at scale requires significant compute.

✅ Conclusion

The integration of GEE-based deep learning workflows with QGIS post-processing proved effective for automated object detection and mapping. Built-up areas and roads were detected with high accuracy in dense urban zones, while NDVI/NDWI cleanly separated vegetation and water classes. The approach produces both accurate classification maps and quantitative metrics useful for spatial planning and environmental monitoring.

📚 References

Ronneberger, O., Fischer, P., & Brox, T. (2015). U-Net: Convolutional Networks for Biomedical Image Segmentation. MICCAI, Vol. 9351, pp. 234–241.
Redmon, J., & Farhadi, A. (2018). YOLOv3: An Incremental Improvement. arXiv:1804.02767.
Breiman, L. (2001). Random Forests. Machine Learning Journal, Vol. 45, pp. 5–32.
Sentinel-2 Data · Landsat-8 Data · Google Earth Engine · QGIS

🙏 Acknowledgment

This project was completed as part of the Winter Training Program on Space Science Technology at India Space Academy, under the guidance of Ms. Alisha Sinha.
