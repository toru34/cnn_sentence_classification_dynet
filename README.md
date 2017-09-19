## Convolutional Neural Networks for Sentence Classification

DyNet implementation for the paper Convolutional Neural Networks for Sentence Classification (EMNLP 2014)[1].

### Requirements
- Python 3.6.0+
- DyNet 2.0+
- NumPy 1.12.1+
- scikit-learn 0.19.0+
- tqdm 4.15.0+

### Prepare dataset
To get movie review data[2] and pretrained word embeddings[3], run
```
sh data_download.sh
```

### Arguments for training
- `--gpu`: GPU ID to use. For cpu, set -1 [default: -1]
- `--n_epochs`: Number of epochs [default: 25]
- `--batch_size`: Mini batch size [default: 32]
- `--num_filters`: Number of filters in each window size [default: 100]
- `--vocab_size`: Vocabulary size [default: 10000]
- `--dropout_prob`: Dropout probability [default: 0.5]
- `--embedding_strategy`: Embeding strategy. [default: rand]
    - `rand`: Random initialization.
    - `static`: Load pretrained embeddings and do not update during the training.
    - `non-static`: Load pretrained embeddings and update during the training.
- `--emb_dim`: Word embedding size. (Only applied to rand option) [default: 300]
- `--alloc_mem`: Amount of memory to allocate [mb] [default: 4096]

### How to train (example)
```
python train_manualbatch.py --num_epochs 20
```
Replace `train_manualbatch.py` with `train_autobatch.py` to use autobatching.

### Arguments for testing
- `--gpu`: GPU ID to use. For cpu, set -1 [default: -1]
- `--model_file`: Model to use for prediction [default: ./model]
- `--input_file`: Input file path [default: ./data/rt-polaritydata/rt-polarity.neg]
- `--output_file`: Output file paht [default: ./pred.txt]
- `--w2i_file`: Word2Index file path [default: ./w2i.dump]
- `--i2w_file`: Index2Word file path [default: ./i2w.dump]
- `--alloc_mem`: Amount of memory to allocate [mb] [default: 1024]

### How to test (example)
```
python test.py
```

### Results
Work in progress

### Reference
- [1] Y. Kim. 2014. Convolutional Neural Networks for Sentence Classification. In Proceedings of EMNLP 2014 \[[pdf\]](https://arxiv.org/pdf/1408.5882.pdf)
- [2] B. Peng and L. Lee. 2005. Seeing stars: Exploiting class relationships for sentiment categorization with respect to rating scales. In Proceedings of the ACL \[[pdf\]](http://www.cs.cornell.edu/home/llee/papers/pang-lee-stars.pdf)
- [3] Google News corpus word vector \[[link\]](https://code.google.com/archive/p/word2vec/)
