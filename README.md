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

## How to Use
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
```
