# Kidney Glomeruli Segmentation - Project Requirements

## Model Architecture
- **ConvNeXt V2** with UperNet decoder for segmentation
- **Input**: 512×512 RGB images (medical imaging optimized)
- **Training**: AdamW optimizer, 0.001 lr, batch size 8-32
- **Variants**: Atto (3.7M) to Base (89M) parameters

## Data Pipeline
- **Source**: QuPath annotated kidney slides with polygon annotations
- **Format**: Export QuPath annotations as GeoJSON
- **Processing**: Convert polygons to segmentation masks using `paquo` library
- **Training Strategy**: 
  1. Train on QuPath polygon annotations
  2. Generate Grad-CAM heatmaps for glomeruli detection
  3. Create pseudo-masks from heatmaps
  4. Retrain with expanded dataset (original + pseudo-masks)

## Key Libraries
- `paquo` - QuPath annotation reading
- `torch` with segmentation models
- `albumentations` - medical image augmentation
- `shapely` - polygon to mask conversion

## Training Commands
```bash
# Install dependencies
pip install -r requirements.txt

# Train model
python -m kidney_segmentation.train --config configs/train_config.yaml

# Generate heatmaps
python -m kidney_segmentation.generate_heatmaps --model_path models/trained_model.pth

# Retrain with pseudo-masks
python -m kidney_segmentation.retrain --config configs/retrain_config.yaml
```

## Project Structure
```
kidney_segmentation/        # Main package
├── data/                  # QuPath data processing
├── models/                # ConvNeXt V2 + UperNet
├── training/              # Training pipeline
├── heatmaps/              # Grad-CAM generation
└── utils/                 # Helper functions
```