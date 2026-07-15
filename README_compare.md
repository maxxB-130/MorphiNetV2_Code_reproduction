## Environment Preparation

Set up the required environment same as README.md.

## Path Configuration

Project-specific paths will be set in the inference stage, there is nothing need to change here.

## Dataset Preparation

No modification need. Just prepare a folder named `Dataset021_ACDC_SINGLE_LABEL` under folder `dataset`. 
Put `acdc_anchor_image.nii.gz` into `Dataset021_ACDC_SINGLE_LABEL/imagesTs` and `acdc_anchor_label.nii.gz` into `Dataset021_ACDC_SINGLE_LABEL/labelsTs` respectively.
Note: I renamed `acdc_anchor_image.nii.gz` as `acdc_anchor_0000.nii.gz` and `acdc_anchor_label.nii.gz` as `acdc_anchor.nii.gz`
The corresponding JSON file is `dataset_task21_f0_single_label.json`.

## Usage

Using the preparated dataset for the inference of MorphiNetV2.

### Testing / Inference

To test the model on the dataset (`Dataset021_ACDC_SINGLE_LABEL`), run:

```bash
  MORPHINET_ACDC_JSON=./dataset/dataset_task21_f0_single_label.json \
  MORPHINET_ACDC_DATA_DIR=./dataset/Dataset021_ACDC_SINGLE_LABEL \
  WANDB_MODE=disabled \
  python main.py \
    --inference_only \
    --test_dataset acdc \
    --use_ckpt ./pretrained \
    --output_root ./results_acdc_single_label \
    --max_samples 0 \
    --mode disabled \
    --mesh_only
```
And the mesh result will be saved as .obj file in the folder `./results_acdc_single_label`.
