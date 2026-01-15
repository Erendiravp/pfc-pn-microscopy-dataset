# pfc-pn-microscopy-dataset
Microscopy images and segmentation masks of live rat prefrontal pyramidal neurons (PFC-PN) acquired by inverted microscopy (40×). Includes JPG images, ground-truth PNG masks, and dilation-derived masks for training.

### File naming convention
Each image must match its mask by filename stem, e.g.:
- 'images_jpg/img_0001.jpg'
- 'masks_gt_png/img_0001.png'
- 'masks_dilated_r5_png/img_0001.png'

## Masks explained
### Ground-truth masks (GT)
'masks_gt_png/' contains **expert-annotated binary masks** used as ground truth for evaluation.

### Dilated masks (derived)
'masks_dilated_r5_png/' contains **derived masks** created by applying morphological dilation to the ground-truth masks using a **disk-shaped structuring element with radius r = 5 pixels**.
These masks are **NOT** ground truth; they were used as *training targets* in the dilation-enhanced setting, while **validation targets remained the original expert-annotated masks**.

## Reproducibility notes (as used in the manuscript)
- The segmentation workflow includes: image acquisition, expert mask annotation, optional mask dilation before training, model training (U-Net / Attention U-Net / Residual U-Net), and evaluation using DSC and qualitative inspection.
- In the experiments reported in the manuscript, the dataset was split 70/30 for train/validation and assessed with K-fold cross-validation (K=5).
