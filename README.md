# Panoramic Image Stitching (MATLAB)

Stitches overlapping photos into a single panorama using classical feature-based image registration (2023). The code follows MathWorks' *Feature Based Panoramic Image Stitching* example, adapted to use SIFT features, and is applied to four scenes.

## Pipeline

1. Detect **SIFT** keypoints and descriptors in each grayscale image.
2. Match descriptors between consecutive images (`matchFeatures`, unique matches).
3. Estimate a **projective homography** for each pair with RANSAC (`estgeotform2d`, 99.9% confidence, up to 2,000 trials).
4. Chain the pairwise transforms, then re-reference them to the central image to limit distortion at the edges.
5. Warp every image onto a shared canvas (`imwarp`), combine them with binary-mask alpha blending, and crop the center.

## Scenes

| Folder | Images |
|---|---|
| `Building Scene 1 (with 6 images)` | 6 |
| `Building Scene 1 (with 9 images)` | 9 |
| `Building Scene 2` | 6 |
| `Whiteboard Scene` | 7 |

## Run

Open a scene folder in MATLAB (with the Image Processing and Computer Vision Toolboxes) and run `code.m`.
