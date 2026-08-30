## Discussion

The principal finding of this study is the large discrepancy between
near-ceiling internal performance and substantially weaker independent
external performance. The final Improved ConvNeXt-Tiny achieved
99.96% accuracy, 99.95% Macro F1,
99.93% balanced accuracy, and an MCC of
0.9995 on the locked internal PlantVillage test partition.
In contrast, evaluation of the same frozen model on the independent
PlantDoc tomato subset produced only 37.97% accuracy,
30.10% Macro F1, 34.90% balanced
accuracy, and an MCC of 0.3099. No external fine-tuning,
threshold optimization, calibration, or model reselection was performed.
The magnitude of this divergence demonstrates that excellent performance
on an internal benchmark cannot by itself be interpreted as evidence of
robust cross-dataset generalization.

The strict shared-class analysis further indicates that the external
degradation was not simply an artifact of comparing different label
inventories. When analysis was restricted to the eight ground-truth
classes common to PlantVillage and PlantDoc while preserving the original
10-way output space, every shared class showed a reduction in F1.
Bacterial Spot and Mosaic Virus each declined by
100.00 and
100.00 percentage points, respectively,
reaching 0% external F1. Leaf Mold declined by
83.33 points and Healthy by
77.78 points. Even the least degraded
shared class, Yellow Leaf Curl Virus, lost
33.33 percentage points of F1. The
heterogeneous class-wise degradation suggests that cross-domain transfer
difficulty is disease dependent rather than a uniform scaling of model
performance.

Calibration analysis revealed an additional and practically important
failure mode. Mean confidence remained high at
92.83% on PlantDoc despite the external accuracy
of only 37.97%. The confidence-accuracy gap increased
from 0.0234 percentage points internally to
54.8602 percentage points externally. Expected
calibration error rose from 0.000558 to
0.548602, the multiclass Brier score increased from
0.001101 to 1.140233, and negative
log-likelihood increased from 0.005038 to
5.455558. Thus, the external failure involved not only reduced
discrimination at the final class-decision level but also severe
overconfidence. This distinction matters because a model that is
frequently wrong yet highly confident can be more problematic in an
operational decision-support setting than a model whose uncertainty
increases appropriately when confronted with unfamiliar data.

Interestingly, the external macro ROC-AUC remained
0.7620 and macro PR-AUC was
0.4672, despite the much lower Macro F1 of
30.10%. This divergence is informative rather than
contradictory. ROC-AUC and PR-AUC characterize class-score ranking,
whereas Macro F1 reflects the final discrete class assignments. The
observed pattern suggests that some class-discriminative ranking
information remained under domain shift even though the transferred
decision structure was insufficient for reliable multiclass
classification. Consequently, reporting only AUC-based metrics would
have obscured the severity of the practical external classification
failure.

The Grad-CAM++ analysis provided complementary evidence about the spatial
behavior of the frozen model. Within the deterministically selected
external XAI cohort, symptom-region alignment among alignment-applicable
cases was 80.00% for correct predictions but
40.00% for incorrect predictions. Conversely,
moderate or dominant background/context concern was observed in
27.27% of selected external correct cases and
70.59% of selected external wrong cases. This
pattern is consistent with greater context sensitivity in a substantial
subset of external errors. The interpretation must remain descriptive,
however, because the XAI cohort was intentionally stratified and the
semantic review was not based on lesion-segmentation ground truth or
expert plant-pathologist annotations.

Importantly, external errors cannot be reduced to a single explanation
based on background attention or spatial mislocalization. Among selected
alignment-applicable external wrong cases, 40.00%
still showed strong or partial alignment with visible symptomatic tissue.
The model could therefore attend to a plausible diseased region while
assigning the wrong disease class. This observation supports a
multi-mechanism interpretation of the domain-generalization failure:
some errors are associated with attention outside the most relevant
symptomatic tissue, whereas other errors appear to involve inadequate
disease-class discrimination despite spatially plausible attention.

Predicted-class and ground-truth-class Grad-CAM++ maps also differed
substantially in many misclassified cases. The mean weighted overlap was
only 0.2740 across all 18 selected wrong cases and
0.2888 across the 17 external wrong cases. Changing
the CAM target from the erroneous predicted class to the true class
improved semantic disease-region alignment in
5 of 14 alignment-comparable external
errors and reduced background/context attention in
8 of 17 external errors. These target
dependent changes indicate that competing disease classes can be
associated with different spatial evidence inside the same frozen
network. The effect was not universal, so the result should not be
interpreted as evidence that true-class targeting necessarily recovers a
correct lesion representation.

High-confidence error analysis reinforces the calibration findings.
Among the five selected high-confidence correct external cases,
symptom-region alignment was 80.00% and
background concern was 20.00%. Among the five
selected high-confidence wrong cases, symptom alignment was only
40.00% and background concern was
40.00%. These examples show that high softmax
confidence is not sufficient evidence of either correct disease
classification or semantically plausible attention under cross-dataset
domain shift.

Taken together, the results support three broader methodological
implications. First, external validation should be treated as a core
component of plant-disease model assessment rather than an optional final
demonstration. Second, probability calibration and confidence behavior
should be evaluated alongside discrimination metrics, especially when
models are intended for decision support. Third, explainability is most
informative when it is used to investigate both correct and incorrect
predictions under domain shift rather than only to illustrate successful
examples. The combination of independent testing, class-matched domain
analysis, calibration assessment, and structured Grad-CAM++ review
exposed failure modes that would have remained largely hidden if the
study had stopped at internal accuracy.

Future work should evaluate whether these weaknesses can be reduced using
broader multi-domain training data, domain-generalization methods,
carefully separated external calibration data, uncertainty-aware
prediction, lesion-informed supervision, and additional independent
datasets. Any such adaptation should be assessed in a new experimental
phase rather than applied retrospectively to the PlantDoc test set used
here, so that the current external evaluation remains a valid estimate of
frozen zero-shot cross-dataset generalization.
