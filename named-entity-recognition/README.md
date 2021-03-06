# BioBERT for Named Entity Recognition

To train an NER model with BioBERT-v1.1 (base), run the command below.
Before training, please run `./preprocess.sh` to preprocess the datasets downloaded in `biobert-pytorch` (see [here](https://github.com/jhyuklee/biobert-pytorch)).

## Additional Requirements
- seqeval : Used for NER evaluation (`pip install seqeval`)

## Training
```bash
export SAVE_DIR=./output
export DATA_DIR=../datasets/NER

export MAX_LENGTH=128
export BATCH_SIZE=32
export NUM_EPOCHS=3
export SAVE_STEPS=1000
export ENTITY=NCBI-disease
export SEED=1

python run_ner.py \
    --data_dir ${DATA_DIR}/${ENTITY}/ \
    --labels ${DATA_DIR}/${ENTITY}/labels.txt \
    --model_name_or_path dmis-lab/biobert-base-cased-v1.1 \
    --output_dir ${SAVE_DIR}/${ENTITY} \
    --max_seq_length ${MAX_LENGTH} \
    --num_train_epochs ${NUM_EPOCHS} \
    --per_device_train_batch_size ${BATCH_SIZE} \
    --save_steps ${SAVE_STEPS} \
    --seed ${SEED} \
    --do_train \
    --do_eval \
    --do_predict \
    --overwrite_output_dir
```

## Evaluation Results

### BioBERT

|                |    Test Precision (%)   |    Test Recall (%)   |    Test F1 (%)   |
|----------------|:-----------------------:|:--------------------:|:----------------:|
| NCBI-disease   |         87.4920         |        91.1155       |      89.2670     |
| BC5CDR-disease |         84.0340         |        87.9488       |      85.9468     |
| BC5CDR-chem    |         93.0060         |        93.9625       |      93.4818     |
| BC4CHEMD       |         93.2650         |        92.8223       |      93.0431     |
| JNLPBA         |         76.0107         |        87.0667       |      81.1639     |
| BC2GM          |         85.8633         |        87.9426       |      86.8905     |
| LINNAEUS       |         91.7159         |        82.4468       |      86.8347     |
| S800           |         76.3485         |        84.0822       |      80.0289     |

### BERT

|                |    Test Precision (%)   |    Test Recall (%)   |    Test F1 (%)   |
|----------------|:-----------------------:|:--------------------:|:----------------:|
| NCBI-disease   |         84.4672         |        87.9091       |      86.1538     |
| BC5CDR-disease |         80.3359         |        84.3254       |      82.2823     |
| BC5CDR-chem    |         90.3319         |        92.5194       |      91.4126     |
| BC4CHEMD       |         91.4879         |        90.4094       |      90.9454     |
| JNLPBA         |         74.3715         |        86.2840       |      79.8861     |
| BC2GM          |         82.8529         |        85.3988       |      84.1066     |
| LINNAEUS       |         89.4553         |        82.1276       |      85.6350     |
| S800           |         77.0788         |        81.1881       |      79.0801     |

### RoBERTa

|                |    Test Precision (%)   |    Test Recall (%)   |    Test F1 (%)   |
|----------------|:-----------------------:|:--------------------:|:----------------:|
| NCBI-disease   |         85.6769         |        87.5083       |      86.5829     |
| BC5CDR-disease |         79.7549         |        84.2445       |      81.9383     |
| BC5CDR-chem    |         89.6131         |        91.4413       |      90.5180     |
| BC4CHEMD       |         90.3025         |        90.7504       |      90.5259     |
| JNLPBA         |         73.9772         |        86.7778       |      79.8679     |
| BC2GM          |         80.9399         |        84.9832       |      82.9123     |
| LINNAEUS       |         84.9721         |        73.0851       |      78.5816     |
| S800           |         72.3283         |        77.7777       |      74.9541     |

## Contact
For help or issues using BioBERT-PyTorch, please create an issue and tag [@minstar](https://github.com/minstar).
