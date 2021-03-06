# Char RNN Poet
Simple two-layer LSTM network to generate Tang poems（七绝）

# Environment

PyTorch 1.8.1
TorchText 0.9.0

## Model

Two-layer uni-directional LSTM network with word embedding size 300 and hidden size 1024.

The model is very simple, and no pre-trained word embeddings are utilized. 

## TO-DOs

- Transform the model into a VAE model
- Apply attention
- Apply pre-trained word-embeddings

# Dataset

The corpus was downloaded from [https://github.com/chinese-poetry/chinese-poetry](https://github.com/chinese-poetry/chinese-poetry) and the training data was created by filtering Qi Jue poems from Tang poems, resulting in 10922 poems. Each poem begins with `<SOP>` token and ends with `<EOP>` token, and each hanzi is considered a word. You can create your own dataset by `Data Preprocess.ipynb`

# Examples

The model was trained on a single Nvidia GTX Titan X with batch size 2048 for 2 days (~15000 epochs) which consumed ~11GB RAM.

```
Epoch 15729 Loss: 1.304158
君不到山無處物，一生無事與身閑。人間盡說逢花雨，不是一生一覺塵。
如中百歲曾留得，遙看還鄉夢覺看。不知日夜東山遠，獨照紅塵滿地花。
Epoch 15739 Loss: 1.304422
興不見君心不知，空留一鶴到山邊。莫言花重船應沒，自有人間不不知。
看花莫羨新條在，花裏人呼萬古同。聞道不堪猶自異，兩頭分上一枝梅。
Epoch 15749 Loss: 1.305263
興不見君來未歸，今朝同向五湖中。相逢一宿最高寺，半夜不知何處去。
今年閑向人中見，已見臨川五月月。青山山下何日期，西林宿竹獨相思。
```

The first line is generated by taking argmax, while the second line by sampling according to the probabilities.
