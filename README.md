#  Dermoscopic Image Analysis for Lesion Detection using Few-Shot Learning

Model building, experiments, references, and source code for research w theork on skin image analysis that draws on meta-learning to improve performance in low data and imbalanced data regimes. 

> This research was carried out in collaboration with the [Machine Learning Research Group (MLRG)](https://www.researchgate.net/lab/Machine-Learning-Research-Group-Chandrabose-Aravindan) and the Departments of [Computer Science](https://www.ssn.edu.in/college-of-engineering/computer-science-and-engineering-department-ssn-institutions/) and [Information Technology](https://www.ssn.edu.in/college-of-engineering/information-technology-department-ssn-institutions/) at **SSN College of Engineering, Anna University**, India.

## Quick Links

The following references will aid in reproducing this implementation, and to extend the experiments presented in the paper for further analyses.

- [Research Paper Preprint [arXiv]](https://arxiv.org/abs/2210.16954).
- [Brief Instructional on running Training & Testing Experiments [Markdown]](./experiments/README.md).
- [Dataset Sources, Splitting Phases, and Experiment Descriptions [Markdown]](./experiments/data/README.md).

## Cite Us

[Link to the Research Paper (preprint version)](https://arxiv.org/abs/2210.16954).

If you find our work useful in your research, please cite us:

```
@article{https://doi.org/10.48550/arxiv.2210.16954,
  doi = {10.48550/ARXIV.2210.16954},  
  url = {https://arxiv.org/abs/2210.16954},  
  author = {Desingu, Karthik and P., Mirunalini and Chandrabose, Aravindan},  
  keywords = {Computer Vision and Pattern Recognition (cs.CV), Artificial Intelligence (cs.AI), Machine Learning (cs.LG), FOS: Computer and information sciences, FOS: Computer and information sciences},  
  title = {Few-Shot Classification of Skin Lesions from Dermoscopic Images by Meta-Learning Representative Embeddings},  
  publisher = {arXiv},  
  year = {2022},  
  copyright = {Creative Commons Attribution 4.0 International}
}
```

## Open-source datasets used for evaluation.
- [Derm7pt Dataset](https://derm.cs.sfu.ca/Welcome.html).
- [ISIC 2018, Task 3 Skin Lesions Dataset](https://challenge.isic-archive.com/data/#2018).
- [PH2 dataset](https://ieeexplore.ieee.org/document/6610779).

## Motivation

- Annotated images and ground truth for the **diagnosis of rare and novel diseases** are scarce. This is expected to prevail, considering the small number of affected patient population and limited specialized clinical expertise to annotate images. 
- Further, the frequently occurring **long-tailed class dataset distributions** in skin lesion and other disease classification datasets cause conventional training approaches to lead to **poor generalization** due to **biased class priors**. 
- Few-shot learning, and meta-learning in general, aim to overcome these issues by **attempting to perform well in low data regimes**. 

## Proposed Embedding Network & Base-Learner Approach for Meta-Learning

This work focuses on improving meta-learning for the **characterization of lesion types** from dermoscopic images.   
Specifically, it proposes a two-stage training and inference approach,
- A **baseline supervised learner** on the meta-training set that allows a network to learn highly representative and generalizable feature embeddings for images, that are readily transferable to new few-shot learning tasks.
- Positing that a representative feature embedding can be more effective than complex meta-learning algorithms, a **simple classifier** is trained atop these representations for downstream classification into lesion types.

  <img src="./docs/assets/figures/embedding-metaleaning-flow-padded.png" width="600">

## Key References

### [[CVPR-2020] Meta-DermDiagnosis Few-Shot Skin Disease Identification using Meta-Learning.pdf](./docs/literature/%5BCVPR-2020%5D%20Meta-DermDiagnosis%20Few-Shot%20Skin%20Disease%20Identification%20using%20Meta-Learning.pdf)

- Proposes the use of meta-learning techniques for efficient model adaptation for extremely low-data scenarios
- Applies Group equivariant convolutions (G-convolutions) in place of the normal spatial convolution filters
- Two network implementations: 
    - Reptile: Gradient-based meta-learning
    - Prototypical networks using Euclidean Distance
- Evaluated on ISIC 2018, Derm7pt and SD-198 datasets
- Outperforms DAML on ISIC 2018
- Implementation Code NOT available

### [[CVPR-2018] Learning to Compare Relation Network for Few-Shot Learning](./docs/literature/%5BCVPR-2018%5D%20Learning%20to%20Compare%20Relation%20Network%20for%20Few-Shot%20Learning.pdf)

- The paper that proposed Relation Networks for Few-Shot Learning.

### [[NeurIPS-2017] Prototypical Networks for Few-shot Learning](./docs/literature/%5BNeurIPS-2017%5D%20Prototypical%20Networks%20for%20Few-shot%20Learning.pdf)

- The paper that proposed Protoypical Networks for Few-Shot Learning.

### [[Elsevier-PR-2020] Temperature network for few-shot learning with distribution-aware large-margin metric](./docs/literature/%5BElsevier-PR-2020%5D%20Temperature%20network%20for%20few-shot%20learning%20with%20distribution-aware.pdf)

- An improvement of Prototypical Networks, by generating query-specific prototypes and thus results in local
and distribution-aware metric 
- Sets different temperature for different categories to penalize query samples that are not close enough to their belonging categories.
