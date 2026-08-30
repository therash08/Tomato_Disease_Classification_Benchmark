## Conclusion

The Improved ConvNeXt-Tiny achieved near-perfect performance on the
locked internal PlantVillage test set, with 99.96%
accuracy and 99.95% Macro F1, but its performance
decreased sharply on the independent PlantDoc tomato subset to
37.97% accuracy and 30.10% Macro F1.
The strict shared-class analysis confirmed that this degradation was
strongly class dependent, while calibration analysis showed that the
external errors were accompanied by pronounced overconfidence, including
an ECE of 0.548602 and a confidence-accuracy gap of
54.86 percentage points.

Structured Grad-CAM++ analysis further showed that selected external
errors were associated with multiple attention behaviors rather than a
single failure mechanism. Incorrect cases displayed lower
symptom-region alignment and greater background/context concern than
selected correct cases, yet some errors remained symptom focused and
still produced the wrong disease label. Predicted-class and
ground-truth-class explanation maps also frequently relied on different
spatial evidence.

Overall, the study demonstrates that high internal benchmark accuracy is
insufficient evidence of robust real-domain performance. Reliable
plant-disease recognition requires independent external validation,
class-wise generalization analysis, calibration assessment, and careful
interpretation of model explanations before claims of practical
robustness are justified.
