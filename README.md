# DeepQuest -- Framework for neural-based Quality Estimation

Developed at the [University of Sheffield][1], DeepQuest provides state-of-the-art models for multi-level Quality Estimation.

If you use this, please cite:

<b>[DeepQuest: a framework for neural-based Quality Estimation][7]</b>. [Julia Ive][2], [Frédéric Blain][3], [Lucia Specia][4] (2018).

    @article{ive2018deepquest,
      title={DeepQuest: a framework for neural-based Quality Estimation},
      author={Julia Ive and Frédéric Blain and Lucia Specia},
      journal={In the Proceedings of COLING 2018, the 27th International Conference on Computational Linguistics, Sante Fe, New Mexico, USA},
      year={2018}
    }

## Documentation:

[![Build Status](https://travis-ci.com/sheffieldnlp/deepQuest.svg?token=qYYGdPigTUsvKkbqCAu8&branch=master)](https://travis-ci.com/sheffieldnlp/deepQuest)

More information on https://sheffieldnlp.github.io/deepQuest

## Acknowledgements

The development of DeepQuest received funding from the [European Association for Machine Translation][5] and the [Amazon Academic Research Awards][6] program.


[1]: https://www.sheffield.ac.uk
[2]: https://github.com/julia-ive
[3]: https://fredblain.org/
[4]: http://www.dcs.shef.ac.uk/~lucia/
[5]: http://eamt.org/
[6]: https://ara.amazon-ml.com/
[7]: http://aclweb.org/anthology/C18-1266

## How to Use Example
### Requirement
- python 2.7

### Clone
```bash
cd
git clone https://github.com/takatsugu-kato/deepQuest.git
```
This repository contains qe-2017 exapmle data.
### Training
```bash
cd deepQuest/quest
./train-test-sentQEbRNN.sh --task qe-2017 --source src --target mt --score hter --activation sigmoid --device cpu
```
### Scoring
```
rm -rf config.py
ln -s ../configs/config-sentQEbRNNEval.py config.py
THEANO_FLAGS=device=cpu python main.py
```
### Memo
1. train.srcとtrain.mtを用意する
1. train.mtをPEしてtrain.peをつくる
1. train.mtとtrain.peの間の[TER][9]([git][8])を出し、train.hterとして保存する
1. 上記を適当なフォルダに配置し、config-sentQEbRNN.pyをそれに合わせて編集する
1. train-test-sentQEbRNN.shをたたいてTrainingする
1. Trainingがおわったらconfig-sentQEbRNNEval.pyを適宜編集する
1. test.mtとtest.srcを用意してScoringを出す

#### TERの出し方
train.mtとtrain.peを用意し、それぞれの行末にカッコ書きでIDをいれる。
IDのフォーマットはなんでもよくて、ユニークかつ両ファイル間で対応がとれていればなんでもいい。
```
$> cat data/train.mt
i am nice (hoge1)
i am good (hoge2)
i am bad (foo3)

$> cat data/train.pe
i am nice (hoge1)
i am good (hoge2)
i am wild (foo3)
```
で、以下をたたくとdataフォルダにter_data.*がいろいろでてくる。
-rと-hのファイルは逆にしても結果は同じ。
```
cd data/
java -jar ../tercom.jar -r train.pe -h train.mt -n ter_data
```

[8]: https://github.com/jhclark/tercom
[9]: http://www.cs.umd.edu/~snover/tercom/