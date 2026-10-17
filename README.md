# Blur, Bokeh & Normal Image Classification

**Bangkit Academy 2024 Capstone Project**

## Project Overview

This project focuses on an image-quality classification model that identifies product photos as **blur**, **bokeh**, or **normal**. The model supports automated image review and feedback for sellers in a marketplace application.

Our team integrated the model through cloud services into **web and mobile applications**. This repository documents the machine learning development and experiments behind that feature.

## My Contribution

I contributed to **model development, training, and experimentation** as part of the Machine Learning team. Other team members were responsible for web development, mobile development, and cloud deployment.

## Research Approach

We started with a Laplacian-based proof of concept, then explored convolutional neural networks, transfer learning, and image-processing features. We compared model architectures and training strategies, investigated unsuccessful approaches, and evaluated the results using recorded accuracy, training curves, and confusion matrices.

The initial proof of concept is available in the [Project Proposal](Project_Proposal.ipynb).

### Dataset Composition

All model-experiment notebooks used the same dataset split, containing **3,417 images across three classes**.

| Dataset split | Images | Percentage |
| --- | ---: | ---: |
| Training | 2,910 | 85.2% |
| Train-validation | 328 | 9.6% |
| Validation | 114 | 3.3% |
| Test | 65 | 1.9% |
| **Total** | **3,417** | **100.0%** |

These values describe the split sizes, not the distribution of images among the three classes.

## Experiment Results

We explored nine approaches. The accuracies below are **historical results reported in the project notebooks**, not independently revalidated production metrics. See the [Model Performance Summary](%5B0%5D_Model_Performance_Summary.ipynb) for the original comparison.

| Approach | Description | Best reported accuracy |
| --- | --- | ---: |
| [InceptionV3 fine-tuning](TL_with_InceptionV3.ipynb) | Fine-tuned the full pretrained InceptionV3 model. | **95.61%** ✴️ |
| [InceptionV3 + Laplacian variance](TL_with_Variance.ipynb) | Combined InceptionV3 features up to `mixed3` with Laplacian variance. | 90.35% |
| [InceptionV3 (`mixed3`)](TL_with_InceptionV3_%28mixed3%29.ipynb) | Used pretrained InceptionV3 up to the `mixed3` layer. | 85.96% |
| [InceptionV3 + custom weighted loss](TL_with_Custom_Weighted_Loss.ipynb) | Assigned a higher penalty to blur-class misclassifications. | 83.30% |
| [InceptionV3 + FFT](TL_with_FFT.ipynb) | Explored Fast Fourier Transform preprocessing. | 80.70% |
| [Basic CNN](Plain_Deep_Learning_Approach.ipynb) | Trained a CNN without pretrained features. | 77.08% |
| [End-to-end deep learning](End_to_End_Deep_Learning_Approach.ipynb) | Integrated object detection into a larger model. | 65.79% |
| [InceptionV3 + FFT + variance](TL_with_FFT_and_Variance.ipynb) | Combined FFT preprocessing with Laplacian-variance features. | 54.39% |
| [Hand-designed classification](Hand_Designed_Approach.ipynb) | Tested manually selected thresholds; discontinued because the classes were not sufficiently separated. | Not reported |

**Key finding:** Full InceptionV3 fine-tuning achieved the highest reported accuracy. Adding handcrafted features did not consistently improve performance. Although the dataset split was shared, training configurations differed across experiments, so the table should not be interpreted as a fully controlled benchmark.

## Additional Trials

Further experiments explored initialization and retraining:

- [Transfer learning + variance: random initialization](Transfer_Learning_%2B_Variance_Approach_Test_Random_Initialization.ipynb)
- [InceptionV3 (`mixed3`): retraining](TL_with_InceptionV3_%28mixed3%29_Retrained.ipynb)

## Evaluation Visuals

**Training accuracy and loss**

![Training accuracy and loss](Images/Accuracy%20and%20Loss.png)

**Test-set confusion matrix**

![Test-set confusion matrix](Images/Confusion%20Matrix%20on%20Test%20Set.png)

**Validation-set confusion matrix**

![Validation-set confusion matrix](Images/Confusion%20Matrix%20on%20Validation%20Set.png)

## Data Availability and Reproducibility

The experiments were performed in Google Colab using a dataset provided by **Braincore**. This repository preserves selected notebooks and evaluation figures, but does not contain the original dataset or complete execution environment.

The original Google Drive links are no longer accessible and have been omitted. Reproducing the experiments may require authorized dataset access, compatible dependencies, and updated file paths. The reported results have not been independently reproduced for this README update.

## Original Project and Credits

This project was developed collaboratively during **Bangkit Academy 2024**. The original team organization also contains the broader web, mobile, and cloud components.

- [Original Machine Learning repository](https://github.com/Bangkit-Capstone-C241-BB01/BlurOrBokeh_ML_All)
- [Bangkit Capstone team organization](https://github.com/Bangkit-Capstone-C241-BB01)
