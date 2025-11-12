# Linked-Generative-Adversarial-Networks-for-Vector-Map-Generation-using-Remote-Sensing-Images-
 This project proposes Linked Generative Adversarial Networks (LGANs) to generate accurate vector maps from remote sensing images across different domains. LGANs extract global (polygons), local (lines), and sub-local (points) features, improving accuracy compared to existing GAN-based mapping models. This repository contains the implementaion, training and testing code for this network.

## Pretrained Weights
The pretrained weights for this model can be downloaded from [here](https://www.kaggle.com/datasets/adityataparia/hpix-weights).
I. INTRODUCTION
The recently developed deep learning models like convolu
tion neural networks (CNNs) are used to classify patch/scene
images. The CNN models like Resnet-50 [1] has deep layers
to extract informative feature vector from the input image.
The feature vector is processed by a classifier in the classifi
cation stage to label it. The feature vectors extracted from
the patch/scene images have uncertainty. Data granulation
is one of the methods to deal with the uncertainty in the
data. Granulation is defined as grouping the objects based the
properties like similarity and connectivity [2]. Pal and Mitra
[3], suggested class-independent (CI) granulation method to
deal with the uncertainty in the feature vectors. In CI, the data
is granulated to three fuzzy granules, namely, low, medium,
and high. CI granulation do not consider the class-belonging
information of the granules. A better data granulation method,
namely, class dependent (CD) granulation was suggested by
Pal et. al [4]. In CD granulation, a feature in the feature vector
is represented with its membership to c number of classes.
CI and CD granulations are confined to overall information
of the data and these two data granulation methods do not
consider the domain-level granulation within a class. With this
motivation, we introduce evolving domain granulation (EDG)
method to deal with the uncertainty in the feature vectors at the
domain level within a class. In EDG, a feature in the feature
vector is represented by its membership to the domain granules
with in a class.
The feature vector obtained by using reset-50 feature ex
tractor is processed by a classifier and it is labeled in the
classification stage of CNN. Different type of classifiers like
neural networks, support vector machines, etc., are used in
the classification stage of CNN to label the feature vectors.
Among these classifiers, GNN is known for its better domain
adaptability due to its non-grid based method of processing
the data [5]. In the case of un-supervised domain adaptation,
where, the class label of an image is not available, the concept
of co-teaching is introduced to generate the pseudo label of an
unknown feature vector, after which, based on the co-teaching,
GCN is used to label the feature vector [6] and [7]. In [6]
and [7], a single classifier, namely, multi-layer perceptron is
used to generate pseudo labels of unsupervised data. A single
classifier cannot consider the overall information to generate a
better pseudo label. Motivated with this, we propose ensemble
of classifiers based pseudo labeling in GCN for un-supervised
domain adaptation. The novelty of the present work is three
fold, i.e., (i) Evolving domain granulation to deal with the
uncertainty in the data at the domain-level within a class, (ii)
Ensemble of classifiers based co-teaching in GCN to generate
pseudo labels for unsupervised DA, and (iii) Applicability
of the proposed model to implement domain adaptation for
patch/scence based RS images. Here, the proposed model is
named as evolving domain granulation based graph convo
lutional neural network with co-teaching for remote sensing
image classification.
II. PROPOSED MODEL FOR RS IMAGE DA
The flow diagram of EDG-GCN is shown in Fig. 1. In
the first step, a Resnet-50 feature extractor with the series
of fifty convolutional and pooling layers is applied on input
image to obtain the informative features. EDG is applied on
the feature vector and each feature vector is represented with
its membership to the domain granule within a class. These
domain granulated features are passed through the ensemble of
classifiers to generate pseudo label of the feature vector. Based
on this pseudo label, the elements of affinity matrix in GCN
are defined and furthermore, GCN is used to label the feature
vector. The detailed architecture of EDG-GCN is shown in Fig.
2. In Fig. 2, a Resnet-50 feature extractor with three layers of



