# Kidney Glomeruli Segmentation for Banff Classification

A commercial-grade machine learning product for automated kidney glomeruli segmentation and Banff classification from histopathological images.

## Features

- Automated glomeruli segmentation from kidney biopsy slides
- Banff classification scoring
- REST API for integration
- Batch processing capabilities
- Docker deployment ready

## Quick Start

```bash
# Install dependencies
pip install -r requirements.txt

# Train model
python -m kidney_segmentation.train --config configs/train_config.yaml

# Run inference
python -m kidney_segmentation.predict --image path/to/image.tif
```

## Project Structure

```
kidney_analaysis_banff/
├── kidney_segmentation/        # Main package
├── configs/                   # Configuration files
├── data/                     # Data directory
├── models/                   # Trained models
├── tests/                    # Unit tests
├── scripts/                  # Utility scripts
├── api/                      # REST API
└── docs/                     # Documentation
```

## License

MIT License - see LICENSE file for details.