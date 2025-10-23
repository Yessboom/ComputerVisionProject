# ComputerVisionProject
## Overview

This repository contains experiments and utilities for a stereo‑vision exam implemented in the notebook `CodeExam.ipynb`. The notebook covers camera calibration, stereo rectification, dense matching (disparity map), simple depth estimation, and visualization of results on sample stereo pairs.

## Notebook summary (CodeExam.ipynb)

- Camera calibration using chessboard images (intrinsics, distortion).
- Stereo calibration and rectification (rotation/translation between cameras).
- Dense stereo matching (block matching / SGBM) to compute disparity maps.
- Post‑processing: median/weighted filtering, hole filling, and simple depth conversion.
- Visualizations: rectified image pairs, colored disparity map, depth overlays.
- Notes on parameters and qualitative evaluation.

## Requirements

- Python 3.8+
- Jupyter Notebook or JupyterLab
- Packages:
    - numpy
    - opencv-python (cv2)
    - matplotlib
    - scikit-image
    - pandas (optional for logs)
    - tqdm (optional for long loops)

Install with pip:
```
pip install numpy opencv-python matplotlib scikit-image pandas tqdm jupyter
```

## Quick start

1. Create and activate a virtual environment (recommended).
2. Install requirements (see above).
3. Start Jupyter:
```
jupyter notebook
```
4. Open `CodeExam.ipynb` and run cells top to bottom. Use the provided sample data (see Data section) or point the notebook to your own stereo pairs.

## Data

Place datasets in the `data/` directory (or update paths in the notebook):

- `calibration/` — chessboard images for camera calibration.
- `stereo/left/` and `stereo/right/` — stereo image pairs for rectification and matching.

Expected file formats: PNG or JPG. Filenames should match across left/right folders (e.g., `0001_left.png` / `0001_right.png`) or adjust pairing logic in the notebook.

## Output

The notebook produces:

- Camera matrices and distortion coefficients (saved as .npz or .yaml if enabled).
- Rectified image pairs for visual verification.
- Disparity maps (raw and filtered) and optional colored visualizations.
- Simple depth maps computed from disparity and baseline/focal length.

Modify saving flags in the notebook to persist results to `outputs/`.

## Code layout

- Code is contained in `CodeExam.ipynb` (executable, documented).
- Auxiliary scripts or helper functions (if present) live in `src/` or are embedded as notebook cells.
- Data and outputs separated under `data/` and `outputs/`.

## Reproducibility tips

- Fix random seeds where applicable.
- Record OpenCV version (some stereo algorithms vary by version).
- Use the same calibration images and marker sizes to reproduce intrinsics.

## Troubleshooting

- Poor disparity quality: tune block size, number of disparities, and pre/post filters in SGBM/BM.
- Misaligned rectification: ensure correct chessboard size and adequate calibration images that cover the field of view.
- Runtime errors: verify OpenCV installation and that images are read correctly (check paths).

## License

Specify a license (e.g., MIT) in `LICENSE` if you plan to reuse or share the code.

## Contact

Open an issue or submit a PR with reproducible steps if you find bugs or want to improve the notebook.

