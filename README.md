
eitai ki enough sir ke dekhanor moto naki aro kisu kora lagbe

README তৈরি করে দিলাম—PART 17 পর্যন্ত completed workflow, dataset cleaning, leakage control, Baseline vs Improved experiment, training configuration, validation results, final independent test results, statistical analysis, InceptionNet parity correction, final ranking, research integrity, paper workflow, suggested paper structure, output folders, future work—সব একসাথে সুন্দরভাবে সাজানো আছে।

Download the complete README.md

এই README এমনভাবে লেখা হয়েছে যেন নতুন কোনো researcher বা supervisor পড়লেও শুরু থেকে শেষ পর্যন্ত বুঝতে পারে তোমার paper-এ কী করা হয়েছে, কেন করা হয়েছে, এবং final result কী। 


Tomato_Disease_Research_README.md
Document



Pasted markdown(5).md
File
eita to beshi boro hoi gese..


ei rkm kore deuu

হ্যাঁ, বুঝছি। তুমি এই uploaded README-এর মতো concise, section-wise, GitHub-friendly version চাও—যেখানে project overview, objective, dataset, workflow, models, setup, main results, key findings, completed vs planned work, future workflow—সব থাকবে, কিন্তু আগেরটার মতো অত বড় হবে না। Uploaded README-টাও একই ধরনের compact research structure follow করে। 


এটা bounded documentation edit। আমি নতুন short README-টা এভাবে রাখব:

Project overview

Research objectives

Dataset + split

Short workflow

6 models

Baseline vs Improved setup

Final test result table

Final winner

Statistical analysis

Completed PART 17

Next paper workflow: PlantDoc / XAI / domain generalization

Project structure

Reproducibility

Short future work

আর outdated result যেমন 2,400 test images, পুরনো ResNet-selected result, বা old ConvNeXt loss 0.001740 রাখব না; তোমার final PART 17 locked results-ই ব্যবহার করব।

এই short structure-টা approve করলে আমি নতুন concise README.md file বানিয়ে দিচ্ছি।


oky deu and readme te comment use koiro ..thn ami github e upload dibo t oi rkm kore deu jeno sob tik tak thake

Done — README-টা এখন GitHub-ready, concise, clean, এবং commentসহ বানানো হয়েছে। তোমার uploaded README-এর compact research structure follow করেছি, যেখানে project motivation, objectives, dataset, workflow, models, results, future domain-generalization direction—সব clearly organized ছিল। 


এই version-এ আছে
PART 17 পর্যন্ত completed workflow

Final locked results only

Baseline vs Improved comparison

Final winner: Improved ConvNeXt-Tiny

Statistical analysis summary

InceptionNet correction note

Research workflow diagram

Completed vs Next Stage

PlantDoc + XAI future workflow

GitHub-friendly hidden <!-- comments -->

Author / Citation / License sections

GitHub-এ upload করার জন্য এই file-টাই README.md নামে use করবে:

Download GitHub-ready README.md

চাইলে আমি next এ তোমার জন্য পুরো GitHub repository folder structure-ও সাজিয়ে দিতে পারি—কোন folder-এ notebook, results, figures, checkpoints, README রাখবে সেটা। 


README.md
Document



README.md


🍅 Tomato Disease Classification with Domain Generalization
<!-- GitHub README Research status: Completed through PART 17 (internal benchmark + independent test evaluation) Update this header later with paper DOI / journal / repository links if available. -->

A deep learning research project for 10-class tomato leaf disease classification using PlantVillage, with a focus on clean data preparation, leakage-aware evaluation, transfer learning, baseline-vs-improved benchmarking, statistical validation, and future cross-dataset domain generalization.

Current completed stage: PlantVillage internal benchmark through PART 17
Final selected model: Improved ConvNeXt-Tiny
Independent test set: 2,399 unseen images
Primary final selection metric: Macro F1-score

📌 Research Motivation
Plant disease classifiers can achieve very high performance on controlled benchmark datasets, but those results may not always generalize to realistic field conditions.

This research therefore focuses on:

reliable tomato disease classification,

data-quality and leakage control,

class-imbalance-aware training,

fair comparison of multiple pretrained models,

statistical validation of model improvements,

model robustness and efficiency,

future PlantVillage → PlantDoc domain-generalization analysis,

future Explainable AI analysis.

<!-- Important: PlantDoc external evaluation and XAI are planned next stages. Do not present them as completed results until those experiments are run. -->

🎯 Research Objectives
Build a clean and reproducible tomato disease classification pipeline.

Validate image integrity and remove exact duplicates.

Prevent train/validation/test leakage using perceptual-similarity grouping.

Compare six ImageNet-pretrained architectures.

Compare Baseline and Improved training strategies.

Evaluate models using Accuracy, Macro F1, Balanced Accuracy, MCC, Log Loss, ROC-AUC, PR-AUC, and class-wise metrics.

Perform paired statistical comparison between Baseline and Improved models.

Select the final model using a predefined ranking protocol.

Extend the work later to PlantDoc, Explainable AI, robustness, and domain generalization.

📂 Dataset
PlantVillage — Source Domain
The current completed benchmark uses the PlantVillage tomato subset with 10 classes:

Tomato Bacterial Spot

Tomato Early Blight

Tomato Late Blight

Tomato Leaf Mold

Tomato Septoria Leaf Spot

Tomato Spider Mites / Two-Spotted Spider Mite

Tomato Target Spot

Tomato Yellow Leaf Curl Virus

Tomato Mosaic Virus

Tomato Healthy

Dataset Cleaning Summary
Item	Result
Raw images	16,011
Corrupted images	0
Exact duplicate groups	14
Redundant exact duplicates removed	14
Final clean images	15,997
Classes	10
Image resolution	256 × 256 RGB
Final Frozen Split
Split	Images
Training	11,199
Validation	2,399
Independent Test	2,399
Total	15,997
The split was created using a group-aware perceptual-hash strategy so that exact or near-duplicate images could not leak across train, validation, and test partitions.

🧹 Data Integrity & Preprocessing
The completed pipeline includes:

image validation,

MD5 exact-duplicate detection,

pHash near-duplicate analysis,

group-aware stratified splitting,

independent leakage audit,

deterministic validation/test preprocessing,

ImageNet-compatible normalization,

train-only robust data augmentation,

class-imbalance analysis,

weighted cross-entropy for the Improved condition.

Class Imbalance
Majority training class: 2,246

Minority training class: 261

Imbalance ratio: approximately 8.61 : 1

Because of this imbalance, Macro F1-score is used as the primary final ranking metric.

🧠 Deep Learning Models
Six ImageNet-pretrained models were evaluated:

Model	Parameters	Input Size
ResNet50	23,528,522	224 × 224
MobileNetV3-Large	4,214,842	224 × 224
EfficientNet-B0	4,020,358	224 × 224
ConvNeXt-Tiny	27,827,818	224 × 224
VGG16	134,301,514	224 × 224
Inception v3	21,806,058	299 × 299
<!-- Architecture naming used in the paper: MobileNet = torchvision MobileNetV3-Large InceptionNet = torchvision Inception v3 ConvNeXt-Tiny = standard torchvision ConvNeXt-Tiny -->

⚙️ Experimental Design
Baseline
ImageNet-pretrained model

deterministic training preprocessing

unweighted cross-entropy

Improved
ImageNet-pretrained model

robust train-only augmentation

weighted cross-entropy

Common Training Setup
Parameter	Setting
Optimizer	AdamW
Learning rate	1e-4
Weight decay	1e-4
Scheduler	ReduceLROnPlateau
Maximum epochs	30
Early stopping patience	7
Gradient clipping	1.0
Random seed	42
Training AMP	Enabled
Final test inference	FP32
🔬 Research Workflow
flowchart TD

    A[PlantVillage Raw Images<br/>16,011]
    --> B[Image Validation]

    B --> C[Exact Duplicate Audit<br/>MD5]
    C --> D[Remove Redundant Duplicates<br/>15,997 Clean Images]

    D --> E[EDA + Class Imbalance Analysis]
    E --> F[Perceptual Similarity Audit<br/>pHash]
    F --> G[Group-Aware Stratified Split]

    G --> H[Train<br/>11,199]
    G --> I[Validation<br/>2,399]
    G --> J[Test<br/>2,399]

    H --> K[Preprocessing + Train-Only Augmentation]
    I --> L[Deterministic Validation]
    J --> M[Frozen Independent Test]

    K --> N[Six Pretrained Models]
    N --> O[Baseline Training]
    N --> P[Improved Training]

    O --> Q[Validation Comparison]
    P --> Q

    Q --> R[Freeze 12 Best Checkpoints]
    R --> S[SHA-256 Development Lock]

    S --> T[Independent Test Identity Lock]
    T --> U[Baseline Test Predictions]
    U --> V[Improved Test Predictions]

    V --> W[Final Metrics]
    W --> X[McNemar + Holm Correction]
    X --> Y[2,000-Resample Stratified Bootstrap]
    Y --> Z[Final Ranking]

    Z --> AA[Improved ConvNeXt-Tiny<br/>Final Winner]
📊 Final Independent Test Results
<!-- These are the final PART 17 locked results. Do not replace them with older pre-PART-17 experiment numbers. -->

Model	Baseline Accuracy	Improved Accuracy	Baseline Macro F1	Improved Macro F1	Better Version*
ResNet50	99.7082%	99.8749%	99.6439%	99.8555%	Improved
MobileNet	99.5415%	99.6248%	99.5014%	99.5705%	Improved
EfficientNet-B0	99.7499%	99.7916%	99.7310%	99.7004%	Baseline
ConvNeXt-Tiny	99.7916%	99.9583%	99.7331%	99.9490%	Improved
VGG16	98.3743%	99.5832%	98.1193%	99.4848%	Improved
InceptionNet	99.3331%	99.7916%	99.2636%	99.7964%	Improved
*Better Version is determined primarily by Macro F1-score.

Key Observation
The Improved pipeline increased Macro F1 for 5 of the 6 architectures.

EfficientNet-B0 was the only exception: its Improved version had slightly higher Accuracy, Balanced Accuracy, MCC, and lower Log Loss, but its Macro F1 decreased slightly. Since Macro F1 was the predefined primary metric, the Baseline EfficientNet-B0 version remained marginally better within that architecture.

🏆 Final Model Ranking
The ranking protocol was fixed before final model selection:

Macro F1 — higher is better

Balanced Accuracy — higher is better

Accuracy — higher is better

Test Log Loss — lower is better

Top results:

Rank	Condition	Model	Macro F1	Balanced Accuracy	Accuracy	Log Loss
1	Improved	ConvNeXt-Tiny	99.9490%	99.9333%	99.9583%	0.004070
2	Improved	ResNet50	99.8555%	99.8912%	99.8749%	0.005143
3	Improved	InceptionNet	99.7964%	99.8148%	99.7916%	0.011315
✅ Final Selected Model
Improved ConvNeXt-Tiny

Metric	Result
Accuracy	99.9583%
Macro F1	99.9490%
Balanced Accuracy	99.9333%
MCC	0.999526
Test Log Loss	0.004070
📈 Statistical Validation
Baseline and Improved models were compared using a paired test protocol.

Exact two-sided McNemar test

Holm correction across 6 architecture-level comparisons

2,000-resample paired stratified bootstrap

Random seed: 42

95% confidence intervals

Bootstrap analysis for:

Accuracy

Macro F1

Baseline-to-Improved differences

This statistical analysis was performed only after all frozen raw test predictions had been generated.

⚠️ InceptionNet Evaluation-Parity Note
An InceptionNet-specific evaluation mismatch was discovered during final testing.

The trained Inception v3 configuration required:

transform_input=True
A validation-only parity audit showed:

Condition	transform_input=False	transform_input=True	Locked Validation Accuracy
Baseline	41.3506%	99.6248%	99.6248%
Improved	61.1505%	99.7082%	99.7082%
The correct configuration was therefore established using validation data only, not by selecting the better test result.

Only the two InceptionNet prediction sets were regenerated. The other 10 prediction sets remained unchanged.

<!-- Keep this note in the repository. It documents why InceptionNet final test predictions differ from the first superseded evaluation. -->

🔐 Reproducibility & Integrity
The project includes multiple safeguards:

fixed random seed (42),

stored dataset membership,

zero train/validation/test hash overlap,

group-aware near-duplicate isolation,

frozen development checkpoints,

SHA-256 checkpoint verification,

explicit independent-test identity lock,

fixed class-to-index mapping,

sequential test sampling,

raw prediction preservation,

final metric and statistical manifests,

final ranking integrity lock.

Independent Test Hash
a6cc66f6e6829d56a10d5daa91efd8bdcfdcba35480024304d273564ead80b20
📁 Important Result Structure
results/
└── test_evaluation/
    ├── independent_test_identity_lock.json
    ├── evaluation_engine_verification.json
    ├── baseline_prediction_manifest_revised.json
    ├── improved_prediction_manifest_revised.json
    ├── inceptionnet_parity_correction_manifest.json
    │
    ├── predictions/
    │   ├── baseline/
    │   ├── improved/
    │   └── corrected_inceptionnet/
    │
    ├── metrics/
    │   ├── independent_test_metrics_corrected.csv
    │   ├── independent_test_metrics_corrected.json
    │   ├── per_class_corrected/
    │   └── confusion_matrices_corrected/
    │
    ├── statistics/
    │   └── baseline_vs_improved_test_comparison.csv
    │
    └── final/
        ├── final_model_ranking.csv
        ├── part17_final_summary.json
        ├── part17_final_integrity_lock.json
        └── PART17_COMPLETE.txt
✅ Completed Research — Through PART 17
Component	Status
Dataset validation	✅ Completed
Exact duplicate removal	✅ Completed
EDA	✅ Completed
pHash near-duplicate audit	✅ Completed
Leakage-aware split	✅ Completed
Independent leakage audit	✅ Completed
Preprocessing	✅ Completed
Train-only augmentation	✅ Completed
Class-imbalance handling	✅ Completed
Six-model transfer-learning benchmark	✅ Completed
Baseline training	✅ Completed
Improved training	✅ Completed
Validation comparison	✅ Completed
Development checkpoint lock	✅ Completed
Independent test evaluation	✅ Completed
Per-class metrics	✅ Completed
Confusion matrices	✅ Completed
McNemar analysis	✅ Completed
Holm correction	✅ Completed
Stratified bootstrap	✅ Completed
Final ranking	✅ Completed
Final winner	✅ Completed
PART 17 integrity lock	✅ Completed
🌍 Next Research Stage
PlantDoc External Evaluation
PlantDoc is planned as an external target-domain dataset to test whether models trained on controlled PlantVillage images generalize to more realistic images with:

complex backgrounds,

natural lighting variation,

different cameras,

occlusion,

scale variation,

field-like environments.

Planned comparison:

PlantVillage Training
        ↓
Frozen Final Model
        ↓
PlantVillage Independent Test
        VS
PlantDoc External Test
        ↓
Domain Generalization Gap
<!-- Do not merge PlantDoc results into the completed PART 17 internal benchmark. Treat external evaluation as a new experimental stage. -->

🔍 Planned Explainable AI
Planned XAI experiments include:

Grad-CAM

Grad-CAM++

SHAP

Main goals:

identify disease-sensitive image regions,

compare correct and incorrect predictions,

check whether models focus on symptoms rather than background artifacts,

investigate failure cases under domain shift.

🔮 Future Work
Potential next experiments:

PlantDoc external evaluation

cross-dataset domain-gap analysis

Grad-CAM / Grad-CAM++

SHAP

robustness testing

attention mechanisms such as CBAM

preprocessing ablation

augmentation ablation

domain-aware augmentation

domain adaptation

lightweight deployment

real-world field validation

🧰 Technologies
Python

PyTorch

Torchvision

CUDA

NumPy

Pandas

Scikit-learn

Matplotlib

Jupyter Notebook

VS Code

👨‍🔬 Research Status
Status: 🚧 Active Research

Completed
✅ PlantVillage internal benchmark through PART 17

The completed stage includes:

clean dataset preparation,

six-model Baseline/Improved benchmarking,

independent test evaluation,

statistical validation,

final ranking,

final integrity lock.

Next
🚧 Cross-dataset domain generalization and explainability

👨‍💻 Author

<!-- Update affiliation / ORCID / email here before paper submission if needed. -->

📚 Citation
If this repository or associated research is used in academic work, please cite the corresponding research paper once it becomes available.

<!-- Replace this section with BibTeX after publication. -->

📜 License
This project is intended for academic and research purposes.

Please follow the licenses and terms of the original PlantVillage and PlantDoc datasets before redistribution or commercial use.

⭐ Final Result
Improved ConvNeXt-Tiny achieved the best final independent-test performance with 99.9583% Accuracy, 99.9490% Macro F1, 99.9333% Balanced Accuracy, 0.999526 MCC, and 0.004070 Test Log Loss on 2,399 unseen PlantVillage test images.

