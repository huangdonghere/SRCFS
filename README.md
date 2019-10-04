# SRCFS

## Description

This project provides the MATLAB source code for our SRCFS algorithm, which is an unsupervised feature selection algorithm presented in the following paper:

```
Dong Huang, Xiaosha Cai, and Chang-Dong Wang. “Unsupervised Feature Selection with Multi-Subspace Randomization and Collaboration”, Knowledge-Based Systems, vol.182, pp.104856, 2019.
```

## Main Function

The SRCFS.m is the main function, which has four input parameters, namely, fea, para_K, para_s, and para_m. Please note that para_K, para_s, and para_m must be positive integers.

* fea:      the n*d data matrix with each row being a data sample.
* para_K:   the number of nearest neighobrs.
* para_s:   the number of random subspaces in each basic feature partition.
* para_m:   the number of basic feature partitions.

After performing the SRCFS method on the dataset, we can obtain the weights of all features computed by SRCFS as well as the ranking of all features according to the weights. Specifically, the ouputs of the main function are as follows:

* feaWeights:	the feature weights computed by SRCFS.
* rankings:     the ranking of all features according to their weights.

## How to use?

If you need to select D features from the dataset with a data matrix fea, you can perform SRCFS like this:

```
[rankings,~] = SRCFS(fea);
selectedFeatureIdx = rankings(1:D);
```

Here, selectedFeatureIdx indicates the indices of D selected features. Then you can use these selected features for your specific tasks. For example, if you would like to perform k-means on the dataset with the selected features, you can do it like this:

```
newFea = fea(:,selectedFeatureIdx);
k = 5; % Number of clusters
clsResult = kmeans(newFea,k);
```
