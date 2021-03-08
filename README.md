# Crosslingual-WSD

**AuSemCor:** The datset created from SemCor 3.0 as additional training data for this task.

**EN-EN:** ELECTRA finetuning script can be found in ELECTRA_finetuning_en_en_final.ipynb. This is a model trained all three datasets - AuSemCor, WiC and MCL-EN, and acheieves 90.5% accuracy on the MCL EN Dev set.

**Multilingual Non-English:** See XLMR_finetuning_MCL_MN_final.ipynb, we finetune XLM-R with XL-WiC enriched data, using OOV training split of MCL dev sets.

**Cross-Lingual Translate Test:** See ELECTRA_cls_translate_test_crosslingual. We use back-translated MCL EN dev for development purposes, finetuning ELECTRA using its CLS token embedding.
