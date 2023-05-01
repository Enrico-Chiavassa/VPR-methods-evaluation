
# VPR-methods-evaluation

This repo is used to easily evaluate pre-trained Visual Place Recognition methods.
A number of trained models are supported (e.g. NetVLAD, SFRS, CosPlace, MixVPR...) and it uses the weights released by the respective authors.


## How to use

The code is designed to be readily used with our [VPR-datasets-downloader](https://github.com/gmberton/VPR-datasets-downloader) repo, so that using a few simple commands you can download a dataset and test any model on it. The VPR-datasets-downloader code allows you to download multiple VPR datasets that are automatically formatted in the same format as used by this repo.

```
mkdir VPR-codebase
cd vpr-codebase

git clone https://github.com/gmberton/VPR-datasets-downloader
cd VPR-datasets-downloader
python3 download_svox.py

cd ..

git clone https://github.com/gmberton/VPR-methods-evaluation
cd VPR-methods-evaluation
python3 main.py --method cosplace --backbone ResNet18 --descriptors_dimension 512 \
    --database_folder ../VPR-datasets-downloader/datasets/st_lucia/images/test/database \
    --queries_folder ../VPR-datasets-downloader/datasets/st_lucia/images/test/queries
```

You can easily change the paths for different datasets, and you can use any of the following methods: NetVLAD, SFRS, CosPlace, Conv-AP, MixVPR.
Note that each method has weights only for certain architectures. For example NetVLAD only has weights for VGG16 with descriptors_dimension 32768 and 4069 (with PCA).


## Acknowledgements

If you use this repository please cite our benchmark paper
```
@inProceedings{Berton_CVPR_2022_benchmark,
    author    = {Berton, Gabriele and Mereu, Riccardo and Trivigno, Gabriele and Masone, Carlo and
                 Csurka, Gabriela and Sattler, Torsten and Caputo, Barbara},
    title     = {Deep Visual Geo-localization Benchmark},
    booktitle = {CVPR},
    month     = {June},
    year      = {2022},
}
```

Kudos to the authors of [NetVLAD](https://github.com/Relja/netvlad), [SFRS](https://github.com/yxgeee/OpenIBL), [CosPlace](https://github.com/Relja/netvlad), [Conv-AP](https://github.com/amaralibey/gsv-cities) and [MixVPR](https://github.com/amaralibey/mixVPR) for open sourcing their models' weights. The code for each model has been taken from their respective repositories.
Also, the code for NetVLAD has been taken from [hloc](https://github.com/cvg/Hierarchical-Localization)


