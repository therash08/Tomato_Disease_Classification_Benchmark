## Limitations

This study has several limitations that should be considered when
interpreting the results.

1. **External sample size and coverage.** The independent PlantDoc tomato
   test subset contained only 79 images representing
   8 mapped ground-truth classes, whereas
   the frozen classifier retained 10 output classes.
   The small external sample limits the precision of class-specific
   estimates and does not represent the full range of disease,
   acquisition, geographic, seasonal, or device variation that may occur
   in practical use.

2. **Cross-dataset label mapping.** PlantDoc folder labels were mapped to
   the nearest corresponding PlantVillage tomato classes. Although the
   mapping was locked before external inference, class definitions and
   visual presentation can differ between datasets. Such semantic and
   acquisition differences are part of the real cross-dataset challenge,
   but they also complicate attribution of the performance loss to any
   single source of domain shift.

3. **Only the frozen final model was externally evaluated.** External
   testing was deliberately restricted to the previously selected
   Improved ConvNeXt-Tiny to prevent external-test-driven model
   selection. This strengthens the validity of the final external test
   but means the study does not establish whether every alternative
   architecture would exhibit the same magnitude or pattern of external
   degradation.

4. **No external adaptation or calibration.** The PlantDoc evaluation was
   intentionally zero-shot. No external fine-tuning, threshold tuning,
   temperature scaling, probability calibration, or domain adaptation
   was performed. The results therefore characterize frozen
   generalization rather than the best performance that might be
   achievable after a separately validated adaptation procedure.

5. **Deterministically selected XAI cohort.** Grad-CAM++ interpretation
   used 40 pre-selected cases, including
   40 primary predicted-class maps and
   18 true-class maps for errors, for a total of
   58 explanation maps. The case-selection protocol was
   deterministic and designed to cover specific correct, incorrect,
   high-confidence, and low-confidence behaviors. Consequently, XAI
   percentages are descriptive of this cohort and must not be interpreted
   as unbiased population-level PlantDoc rates.

6. **No expert lesion-localization ground truth.** Semantic attention
   labels were based on structured visual review rather than
   pixel-level lesion masks or independent expert plant-pathologist
   annotation. Terms such as symptom alignment and background concern
   therefore describe visible attention patterns and not validated
   pathological localization accuracy.

7. **Grad-CAM++ is post-hoc.** Grad-CAM++ visualizes spatial sensitivity
   associated with a target class but does not reveal a complete causal
   decision process. Attention to a region does not demonstrate that the
   region alone caused a prediction, and apparently plausible
   localization does not guarantee correct disease discrimination.

8. **Confidence is model-derived rather than clinical uncertainty.**
   Softmax confidence and calibration metrics quantify statistical model
   behavior. They should not be interpreted as clinical certainty or as
   a direct measure of diagnostic risk without prospective validation.

9. **No prospective or multi-site deployment study.** The present work is
   a retrospective image-classification study. Performance under
   prospective image acquisition, different devices, field conditions,
   user behavior, and real diagnostic workflows remains unknown.

These limitations do not invalidate the external failure observed here;
instead, they define the scope of the conclusions and identify the
experimental evidence required before considering broader practical
generalization.
