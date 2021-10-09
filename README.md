# Crosslingual-WSD

**AuSemCor:** The datset created from SemCor 3.0 as additional training data for this task.

**EN-EN:** ELECTRA finetuning script can be found in ELECTRA_finetuning_en_en_final.ipynb. This is a model trained all three datasets - AuSemCor, WiC and MCL-EN, and acheieves 90.5% accuracy on the MCL EN Dev set.

**Multilingual Non-English:** See XLMR_finetuning_MCL_MN_final.ipynb, we finetune XLM-R with XL-WiC enriched data, using OOV training split of MCL dev sets.

**Cross-Lingual Translate Test:** See ELECTRA_cls_translate_test_crosslingual. We use back-translated MCL EN dev for development purposes, finetuning ELECTRA using its CLS token embedding.


**Training the model:**  For training the models for probability sum, you can use the file  ELECTRA_finetuning_en_en_final.ipynb in our github repository. This file is training the model Electra-large. To train other models for ensembling as mentioned in the paper, you can change the model easily. You can search for "electra" in that file and replace it with the appropriate model and tokenizer name which you can obtain from the official sites of the models. 
You will also need to replace the data paths provided in the code. We uploaded the dataset on google drive and the paths are relative to that. We have provided the AuSemCor dataset that we tagged as mentioned in the paper. You can convert the MCL and other data that you want to use for training in that format. While training, our code also saves the model weights of the model which performs best on the validation data. 

**Ensembling:** For ensembling, no further training is required. First, you have to load the saved weights of the models and prepare the data accordingly. Then you can pass the input to each model and rather than predicting the output as binary, just take the softmax over the output of the last layer so that the number is between 0-1 and can be treated as the probability of the context being similar. Once you obtain the output from all the models, we just take the average of all these probabilities from different models and use this to predict whether the context is similar or not.
