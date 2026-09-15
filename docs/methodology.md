# Histology experiment notes

The dataset is NCT-CRC-HE-100K, with nine tissue classes listed in the root README. Download and extract it separately, then set `HE_DATA_DIR` to the folder containing the class directories. The notebook's class discovery, data split and model cells show the exact preprocessing.

The historical notebook used two random stratified image-patch splits. Patches from the same slide/patient may be correlated; patient/slide-independent validation has not been established by this split. The 99.77% accuracy is a result from that experiment, not a claim of clinical or pediatric generalization. Grad-CAM visualizes model attention but does not by itself validate the model's clinical reasoning.

The extensionless file had identical source cells to the named notebook and was removed; the canonical notebook remains. Dependencies, local data override and historical figure exports were added. Training curves, confusion matrix and Grad-CAM figures under this directory come from saved notebook outputs. No new test-set score was generated.

Full reproduction needs the dataset, compatible PyTorch environment and a training run. The notebook saves model weights in its working directory; the previously documented outputs tree was not committed. Keep output paths and resulting model versions together when publishing a new run.
