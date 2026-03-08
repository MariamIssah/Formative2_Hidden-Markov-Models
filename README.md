# Formative 2 - Hidden Markov Models

This repository contains a Hidden Markov Model (HMM) pipeline for smartphone-based human activity recognition using accelerometer and gyroscope data. The project models four hidden activity states:

- Standing
- Walking
- Jumping
- Still

The implementation is provided in the notebook `HMM_Activity_Recognition.ipynb` and includes data loading, feature extraction, feature normalization, HMM training with Baum-Welch, decoding with Viterbi, evaluation on unseen test data, and result visualizations.

## Repository Contents

- `HMM_Activity_Recognition.ipynb`: Main notebook for preprocessing, model training, evaluation, and visualization.
- `performance_metrics.csv`: Per-activity evaluation metrics.
- `transition_matrices.png`: Heatmaps of learned transition probabilities.
- `emission_distributions.png`: Visualization of learned emission distributions.
- `confusion_matrix.png`: Confusion matrix for test-set classification.
- `state_predictions.png`: Example decoded hidden-state sequences.
- `raw_sensor_data.png`: Example raw accelerometer visualizations.
- `Data/`: Activity recordings organized into training, validation, and test folders.

## Dataset Structure

The dataset is split by activity and by usage stage.

- Training folders: `Standing`, `Walking`, `Jumping`, `Still`
- Validation folders: `Standing_val`, `Walking_val`, `Jumping_val`, `Still_val`
- Test folders: `Standing_test`, `Walking_test`, `Jumping_test`, `Still_test`

Each recording folder contains:

- `Accelerometer.csv`
- `Gyroscope.csv`

Current repository totals:

- 70 accelerometer files
- 70 gyroscope files
- 50 training recordings across the four activities
- 10 validation recordings
- 10 test recordings

## Notebook Workflow

The notebook is structured into the following stages:

1. Import required libraries.
2. Load and merge accelerometer and gyroscope recordings.
3. Extract time-domain and frequency-domain features.
4. Build sliding-window feature sequences.
5. Normalize features using `StandardScaler`.
6. Train Gaussian HMMs using Baum-Welch.
7. Decode sequences with the Viterbi algorithm.
8. Classify unseen sequences with multi-model likelihood scoring.
9. Compute evaluation metrics and generate plots.
10. Summarize findings and analysis.

## Features Used

The notebook extracts a combination of time-domain, frequency-domain, and cross-axis features, including:

- Mean
- Standard deviation
- RMS
- Variance
- Minimum, maximum, and range
- Kurtosis and skewness
- Dominant frequency
- Spectral energy
- Maximum power
- Spectral centroid
- Correlation between sensor axes
- Signal magnitude area (SMA)

Feature windows are generated with a sliding-window approach using:

- Window size: 100 samples
- Overlap: 50%

## Evaluation Outputs

The current metrics file reports the following activities in the test evaluation:

- Standing
- Walking
- Jumping
- Still

The exported metrics are stored in `performance_metrics.csv` with these columns:

- `Activity`
- `Samples`
- `Sensitivity`
- `Specificity`
- `Precision`
- `Accuracy`

## How To Run

1. Open `HMM_Activity_Recognition.ipynb` in Jupyter or VS Code.
2. Install the required Python packages if needed:

```bash
pip install numpy pandas matplotlib seaborn scipy scikit-learn
```

3. Update the dataset path inside the notebook if your local machine path differs from the one currently hardcoded.
4. Run the notebook from top to bottom.

## Notes

- The notebook currently contains a machine-specific `data_dir` path. If you are running this on a different computer, change it to the local `Data` folder path before executing all cells.
- Some plots and CSV outputs are already committed in the repository for reference.
- The notebook includes both model parameter visualizations and evaluation visualizations required for the assignment.

## Objective

The goal of the project is to show how Hidden Markov Models can be used to infer underlying human activity states from noisy smartphone sensor observations, and to evaluate how well the learned models generalize to unseen recordings.
