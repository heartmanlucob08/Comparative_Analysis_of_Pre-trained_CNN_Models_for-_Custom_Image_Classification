## 🔗 Google Colab Notebook

You can view and run the full implementation of this project using Google Colab:

[Open in Google Colab](https://colab.research.google.com/drive/1sksPynyNkg9_owNiF2kEBj1Bgf85tiMh?usp=sharing)

# 🌿 Laboratory Work 5 Reflection  
## Comparative Analysis of Pre-trained CNN Models for Custom Image Classification

---

## 📌 Project Overview

This laboratory activity focused on comparing different **pre-trained CNN models** for a custom plant image classification dataset. The goal was to evaluate how well each model performs using transfer learning and compare their results using different evaluation metrics.

The three main pre-trained models used were:

- **MobileNetV2**
- **EfficientNetB0**
- **ResNet50**

The models were evaluated using:

- Accuracy and Loss
- Precision, Recall, and F1-score
- Confusion Matrix
- ROC Curve
- AUC Score
- Grad-CAM Explainability

---

## 📊 Model Performance Summary

| Model | Validation Accuracy | Validation Loss | F1-score | ROC AUC |
|---|---:|---:|---:|---:|
| **MobileNetV2** | **77.97%** | **0.7949** | **77.96%** | **0.9854** |
| **EfficientNetB0** | **83.96%** | **0.6400** | **84.06%** | **0.9908** |
| **ResNet50** | **81.84%** | **0.6064** | **81.96%** | **0.9907** |
| **Good Model** | **85.31%** | **0.4573** | **85.02%** | **0.9946** |

> Among the three LW5 pre-trained models, **EfficientNetB0 achieved the highest validation accuracy**.  
> Overall, the ** Good Model** had the best performance when previous saved models were included in the comparison.

---

# A. Model Performance

---

## 1. Which pre-trained model achieved the highest accuracy? Why?

Among the three pre-trained models used in LW5, **EfficientNetB0 achieved the highest validation accuracy** with **83.96%**.

I think EfficientNetB0 performed best because it is designed to balance model depth, width, and image resolution efficiently. This helped it learn more useful plant features compared to the other models. Since the dataset contains 20 plant species with visually similar leaves, flowers, and backgrounds, EfficientNetB0’s feature extraction helped it distinguish the classes better.

---

## 2. Which model had the lowest performance? What could be the reason?

Among the three pre-trained models, **MobileNetV2 had the lowest validation accuracy** with **77.97%**.

This does not mean MobileNetV2 performed badly. It still reached the acceptable range, but compared to EfficientNetB0 and ResNet50, it had lower accuracy. One possible reason is that MobileNetV2 is designed to be lightweight and efficient, so it may have fewer feature extraction capabilities compared to larger models. Since my dataset has fine-grained plant classes, a lighter model may struggle more with very similar visual patterns.

---

## 3. How did loss values compare across models?

The validation loss values showed that the models performed differently in terms of prediction confidence.

| Model | Validation Loss |
|---|---:|
| MobileNetV2 | **0.7949** |
| EfficientNetB0 | **0.6400** |
| ResNet50 | **0.6064** |
| Good Model | **0.4573** |

Among the three LW5 models, **ResNet50 had the lowest validation loss**, which means it made more confident and stable predictions compared to MobileNetV2 and EfficientNetB0. However, EfficientNetB0 still had the highest validation accuracy among the three.

Overall, the Fine-tuned MobileNetV2 Good Model had the lowest loss among all compared models, showing better confidence and generalization.

---

# B. Evaluation Metrics

---

## 4. Why is accuracy not enough to evaluate a model?

Accuracy is not enough because it only shows the overall percentage of correct predictions. It does not show which specific classes were classified well or poorly.

For example, a model can have high accuracy but still perform poorly on some minority or visually similar classes. That is why Precision, Recall, F1-score, Confusion Matrix, ROC Curve, and AUC are also important. These metrics help us understand the model’s class-level performance and whether it is making balanced predictions across all 20 plant classes.

---

## 5. Which model had the best F1-score? What does it indicate?

Among the three LW5 pre-trained models, **EfficientNetB0 had the best F1-score** with around **84.06%**.

This means EfficientNetB0 had the best balance between Precision and Recall among the three pre-trained models. A high F1-score indicates that the model was not only making correct predictions but also identifying the actual classes more consistently.

Overall, the Fine-tuned MobileNetV2 Good Model had the best F1-score overall with **85.02%**, which shows that it performed well across most classes.

---

## 6. How did Precision and Recall differ across models?

Precision and Recall varied depending on how each model handled class predictions.

- **Precision** shows how correct the model was when it predicted a certain class.
- **Recall** shows how many actual samples of a class the model correctly found.

EfficientNetB0 had strong Precision and Recall, which explains why it achieved the highest accuracy among the three pre-trained models. ResNet50 also performed closely, while MobileNetV2 had slightly lower scores.

Some models were better at avoiding wrong predictions, while others were better at detecting more actual samples. This difference is important because plant classes can be visually similar, and a model may confuse one plant species with another.

---

# C. Confusion Matrix Analysis

---

## 7. Which classes were frequently misclassified?

The frequently misclassified classes were usually the plant species that had similar leaves, colors, flowers, or backgrounds.

Some examples of classes that may be harder to distinguish include:

- `Vigna marina`
- `Suriana maritima`
- `Ipomoea_pes-caprae`
- `pandanus_tectorius`
- `Solidago sempervirens`

These classes can have similar green leaves, yellow flowers, or beach/coastal backgrounds. Because of this, the model sometimes confused them with each other.

---

## 8. What patterns did you observe in the confusion matrix?

The confusion matrix showed that the models performed well on classes with more distinct visual features. Classes with unique flowers, leaf shapes, or textures were classified more correctly.

The common pattern was that misclassifications happened between visually similar plant species. This means the models sometimes learned general plant features but struggled with small differences between species. This is expected because the dataset is a fine-grained plant classification task, which is more difficult than classifying very different objects.

---

# D. ROC and AUC

---

## 9. Which model had the highest AUC score?

Among the three LW5 pre-trained models, **EfficientNetB0 and ResNet50 had very high AUC scores**, with EfficientNetB0 around **0.9908** and ResNet50 around **0.9907**.

Overall, the **Fine-tuned MobileNetV2 Good Model** had the highest AUC score with **0.9946**.

This shows that the final fine-tuned model had the strongest class separation ability.

---

## 10. What does AUC tell us about model performance?

AUC tells us how well the model separates one class from the others using prediction probabilities. It is useful because it gives a deeper understanding of the model’s performance beyond accuracy.

A high AUC means the model is good at ranking the correct class higher than incorrect classes. In my results, all pre-trained models had high AUC scores, which means they learned strong class-discriminative features even if some individual predictions were still wrong.

---

# E. Explainability: Grad-CAM

---

## 11. What did Grad-CAM reveal about model decision-making?

Grad-CAM showed which parts of the image influenced the model’s prediction. It helped reveal whether the model was focusing on important plant regions such as leaves, flowers, stems, or plant texture.

This is useful because it allows us to understand the model’s decision-making process instead of only looking at the predicted label.

---

## 12. Did the model focus on relevant image regions?

Yes, based on the Grad-CAM results, the models generally focused on relevant plant regions. The heatmaps often highlighted the leaves, flower areas, or plant body.

However, in some cases, the models also focused on background areas or general leaf clusters. This suggests that some predictions may still be affected by background patterns, lighting, or visually similar plant features.

---

## 13. Which model produced the most meaningful heatmaps?

The most meaningful heatmaps were produced by the better-performing models, especially **EfficientNetB0** and the **Fine-tuned MobileNetV2 Good Model**.

These models were more likely to focus on the actual plant regions instead of irrelevant background areas. This supports their higher accuracy, F1-score, and AUC values.

---

# F. Model Comparison & Improvement

---

## 14. Which model would you recommend for deployment? Why?

For deployment, I would recommend the **My Good Model** overall because it achieved the best performance:

- **85.31% validation accuracy**
- **85.02% F1-score**
- **0.9946 AUC score**

It also has a good balance between accuracy and efficiency. MobileNetV2 is lightweight compared to larger CNN architectures, which makes it more suitable for real-world deployment, especially in mobile or web applications.

If I only consider the three LW5 pre-trained models, I would recommend **EfficientNetB0** because it achieved the highest validation accuracy among them.

---

## 15. How can you further improve your best-performing model?

The best-performing model can still be improved by:

- Cleaning the dataset and removing blurry or incorrect images
- Adding more high-quality images per class
- Balancing the number of images per class
- Fine-tuning more layers carefully
- Improving data augmentation
- Testing more training epochs with EarlyStopping
- Reducing background noise in images
- Using better image cropping so the plant occupies more of the image

The validation loss is still slightly above the ideal target, so improving dataset quality and reducing confusion between similar plant species may help the model generalize better.

---

# G. Real-World Application

---

## 16. How can your model be applied in real-world scenarios?

This model can be applied in real-world scenarios such as:

- Plant species identification
- Educational plant learning applications
- Biodiversity monitoring
- Coastal plant classification
- Environmental research tools
- Mobile plant recognition apps
- Web-based plant classifier systems

For example, a user can upload or capture a plant image, and the system can predict the plant species using the trained model.

---

## 17. What are the risks of deploying an inaccurate model?

Deploying an inaccurate model can lead to wrong plant identification. This can be risky if the system is used for research, environmental monitoring, or decision-making.

Some risks include:

- Misidentifying plant species
- Confusing visually similar plants
- Giving users incorrect information
- Reducing trust in the system
- Possible errors in biodiversity records
- Wrong decisions if the model is used in fieldwork

Because of this, the model should include confidence scores and should not be treated as a replacement for expert verification.

---

## 18. How can this system be integrated into a mobile/web app?

The system can be integrated into a mobile or web app by saving the trained model and loading it into an application backend or mobile environment.

A possible flow is:

1. The user uploads or captures a plant image.
2. The app preprocesses the image to the required input size.
3. The trained model predicts the plant class.
4. The app displays the predicted class, confidence score, and possibly a Grad-CAM visualization.
5. The result can be stored or used for plant identification records.

For mobile apps, the model can be converted to TensorFlow Lite. For web apps, the model can be used with a backend API or TensorFlow.js.

---

# Final Reflection

This laboratory activity helped me understand the importance of comparing different pre-trained CNN models. Each model had different strengths and weaknesses.

Among the three LW5 pre-trained models, **EfficientNetB0 achieved the highest validation accuracy**, while **ResNet50 had the lowest validation loss**. Overall, the **Good Model** performed best when all previous models were included in the comparison.

The activity also showed that accuracy alone is not enough. Metrics such as Precision, Recall, F1-score, AUC, Confusion Matrix, and Grad-CAM are important for understanding how the model performs and why it makes certain predictions.

Overall, the best model achieved strong performance and can be considered useful for plant classification, but it can still be improved by cleaning the dataset and adding more high-quality training images.
