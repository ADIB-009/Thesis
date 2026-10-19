Abstract
Underwater images require semantic segmentation to support marine debris monitoring and the inspection of submerged infrastructure. However, the progress is hard to evaluate when the benchmark itself is unreliable. This study began with a survey and built a four-class underwater image dataset (Aquatic Animal, Artifacts
and Metals, Human Activity, Marine Trash and Plastic). The initial benchmark
reported a YOLO–U-Net hybrid as the best segmentation model (74.12% mIoU,
1.75 points above DeepLabv3+). Then the focus of the study shifted to whether
this result could be trusted and what actually improves segmentation performance
on this dataset. Later benchmarking did not support the previous claim. Upon
further inspection, out of the 347 original test images, 143 (41.2%) contained a
near-duplicate image in the training split, implying data leakage. After re-scoring
the models on uncontaminated dataset, mean IoU dropped between 3.6 to 4.5 points
across different models. Following that, we rebuilt the data splits using two independent methods, defined a single evaluation protocol for each of the models, and
reported bootstrap confidence intervals. Furthermore, two-seed replication was performed on each model with matched controls. Using this protocol, the initial hybrid
model achieved (68.80%) mIoU, a (5.2%) drop in performance. Additionally, a blind
human review with random decoys estimated about 770 unlabelled objects in the
training split and confirmed 158 unlabelled objects in the test split. We then moved
on to evaluating six different modeling ideas. Replacing ResNet backbones with
SegFromer-B2 resulted in the largest reliable gain (+0.08 to 0.11 mIoU). Frozen
CLIP features (CoGS) improved a weak backbone by +0.071 (95% CI +0.053 to
+0.093) but a stronger backbone such as Segformer saw a much smaller gain (+0.004
mIoU), which is well within seed-to-seed variation. Our proposed TAM-net, which
combines a stride-2 detail path, flip and zoom-in augmentation, and the masking
of background pixels that an exponential-moving average teacher confidently labels
as foreground during training period, is the best performing model overall (0.7468
over two seeds, against 0.7361 for the tuned baseline). Pooled over two backbones
(Segformer-B2 and DeepLabv3+), it improved the original model by 0.0126 mIoU
(95% CI +0.0025 to +0.0225), with the same sign in all four seed pairs and an
interval that stays above zero (+0.0007) when a third SegFormer-B2 seed is added;
the pooling was chosen after the results, and on SegFormer-B2 alone the margin
(+0.0108, CI −0.0013 to +0.0247) does not exclude zero. The background masking by itself adds +0.0077 mIoU (CI −0.0032 to +0.0192), and the detail path
and augmentation contributes to gains in external SUIM images. Physics-based
restoration (PADS-Net), scale-aware design (Aquascale), and missing-annotationaware-training failed to beat their matched controls, and therefore, are retracted
from the results. The primary contributions from this thesis are a corrected and audited benchmark, a reproducible evaluation protocol, a decoy-calibrated label audit,
and proposed design that is the best-performing model in this comparison.
Keywords: Underwater Semantic Segmentation; Benchmark Contamination; NearDuplicate Detection; Missing Annotations; SegFormer; CLIP; Evaluation Reliability; Bootstrap Confidence Intervals; Marine Debris; Deep Learning.
