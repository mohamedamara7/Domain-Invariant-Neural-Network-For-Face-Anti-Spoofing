# Domain-Invariant-Neural-Network-For-Face-Ant-Spoofing

This repository contains a neural network model for face anti-spoofing, trained on the CelebA Spoof for Face-AntiSpoofing dataset. The dataset can be found on Kaggle: [CelebA Spoof for Face-AntiSpoofing](https://www.kaggle.com/datasets/attentionlayer241/celeba-spoof-for-face-antispoofing).

## Project Overview

Face anti-spoofing is a crucial task in ensuring the security of facial recognition systems. The goal of this project is to develop a robust neural network model capable of distinguishing between real and spoofed faces.

## Methodology

### Experimenting with Different Color Spaces

Initially, I experimented with different color spaces on a part of the dataset to determine which one would yield the best accuracy. The results are as follows:

- **YUV**: 63.45%
- **YCBCR**: 63.78%
- **RGB**: 0.74%
- **HSV**: 77.45%

Based on these results, the HSV color space had the highest accuracy, so I decided to proceed with it.

### Combining Color Spaces

I then attempted to train the model on a combination of RGB and HSV color spaces. However, this approach resulted in:

- Accuracy: 76.63%
- Model performance: Slower due to the increased input size (6 channels instead of 3)

Since this approach did not improve accuracy and slowed down the model, I chose to focus on the HSV color space individually.

### Incorporating Fourier Transform

To make the model more general and robust for use with any photo outside our domain (dataset), I decided to train on the HSV color space and the magnitude spectrum from the Fourier transform of each photo. This approach yielded an accuracy of 78.35%.

### Final Model Training

Finally, I trained the model using the HSV color space and the Fourier transform on the complete dataset. This final model achieved an accuracy of 92.78%.

## Results

- **Best Color Space**: HSV with 77.45% accuracy
- **Combination of RGB and HSV**: 76.63% accuracy (slower model performance)
- **HSV + Fourier Transform (Part Dataset)**: 78.35% accuracy
- **HSV + Fourier Transform (Full Dataset)**: 92.78% accuracy

## Conclusion

The final model trained on the HSV color space and the Fourier transform of the complete dataset achieved the best performance, with an accuracy of 92.78%. This model can be used for face anti-spoofing with high accuracy and robustness.

## Future Work

Future improvements can include experimenting with different neural network architectures, further augmenting the dataset, and optimizing the training process to reduce model complexity and training time.

## References

- [CelebA Spoof for Face-AntiSpoofing Dataset](https://www.kaggle.com/datasets/attentionlayer241/celeba-spoof-for-face-antispoofing)

## License

This project is licensed under the MIT License. See the LICENSE file for details.
