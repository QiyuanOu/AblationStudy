# AblationStudy
One-Step Late Fusion Multi-view Clustering with Compressed Subspace (OS-LFMVC- CS)

# AblationStudy
One-Step Late Fusion Multi-view Clustering with Compressed Subspace (OS-LFMVC- CS)

This model is a one-step late-fusion multi-view clustering based compressed subspace learning method with 3 parts - late fusion, sampling matrix $\mathbf{P}$, and bipartite graph $\mathbf{S}$ for reconstruction, which can be explored separately to perform ablation experiments by removing the late fusion and sampling (corresponding to obtaining the full graph $\mathbf{Z}^*$) parts each. 2 ablation studies are needed to compare the clustering effect and clustering time to further recognize the effectiveness of both fusion, compression and their interaction schemes.

Specifically, Ablation1 removes the updating of the sampling $\mathbf{P}$ part, and the corresponding $\mathbf{S}$ to use the global graph $\mathbf{Z}$. Ablation2 removes the late fusion learning weights and the transformation matrix $\mathbf{W}$ (permutation) part, and directly fuses with the average weights of each view to obtain the clustering results. Performance are analyzed in time and clustering results from the table below. 

| Dateset     |    proposed    |  Ablation1 |  Ablation2 |
|-------------|:--------------:|:----------:|:----------:|
|     ACC     |                |            |            |
| Citeseer    | **56.6 ± 0.0** | 55.2 ± 0.4 | 43.8 ± 0.5 |
| Cora        | **60.8 ± 0.0** | 58.9 ± 0.9 | 51.3 ± 1.8 |
| ProteinFold | **35.3 ± 0.0** | 34.1 ± 1.2 | 25.3 ± 1.3 |
| NUSWIDE     | **14.7 ± 0.0** | 13.7 ± 0.6 | 12.8 ± 0.6 |
| Reuters     | **53.7 ± 0.0** |      -     | 42.3 ± 0.1 |
|   Time(s)   |                |            |            |
| Citeseer    |      2.27      |     8.4    |     3.6    |
| Cora        |      3.46      |    17.7    |    2.29    |
| ProteinFold |      5.68      |    7.29    |     2.3    |
| NUSWIDE     |      23.50     |   439.37   |    30.53   |
| Reuters     |      36.62     |      -     |    17.48   |

Result analysis: The comparison of Ablation1(using global graph) and the proposed algorithm are discussed in three cases, when Ablation1 uses the complete similarity graph $\mathbf{Z}$ to align with the kernel fusion, the clustering results are basically comparable with our fast clustering method based on compressed subspace, which indicates that the compression process of our algorithm has no obvious impact on the clustering effect; On the other hand, the time cost of Ablation1 is significantly higher than that of our proposed algorithm, which indicates that our proposed compression scheme can improve the clustering efficiency. Moreover, the Reuters dataset is not applicable in Ablation1 as it encounters out-of-memory problem in our 64G memory setting. 

The comparison of Ablation2(neglecting late fusion) and the proposed algorithm shows the significant impact on the late-fusion mechanism in aligning the subspace. Our framework assists in aligning the clustering structure of each view and improving the clustering performance of the fused clustering partition matrix by sharing consistent subspace of multiple views through learning.
