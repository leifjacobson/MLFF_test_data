# MLFF_validation_data
Location to share public data generated at Schrodinger, for validation of MLFF models.

## General Data Format and Units

All structural data is given in json to ease reading into python using the `json` module.  Each test directory has multiple json files that collect structures that are related in some way and error statistics are typically computed over each file and then aggregated over the files.  Each file is structured as a list of dicts and each dict corresponds to a single structure.  Each dict has keys `title`, `smiles`, `coordinates`, `elements` and `charge` which give each structure a title, a smiles string, atomic coordinates in Angstrom, a list of elements corresponding to the coordinates and a net charge.  In addition, if the structure is periodic there is a length 9 list `lattice` which gives the unit cell vectors in Angstrom.  All structures have one or more energy keys, which are formated as `E[<method>](<units>)` where `method` is a string indicating the method and units is either `Ha` or `Ry`, for Hartree or Rydberg.  In this data method is one of `wB97X-D3BJ/def2-TZVPD`, `DLPNO-CCSD(T)/CBS` or `PBE-D3`.  Additional properties are given for some datasets and are detailed below where applicable.

## Datasets

### TorsiononNet500

This dataset contains 500 rotamer scans.  Here we provide wB97X-D3BJ/def2-TZVPD and DLPNO-CCSD(T)/CBS estimates in Hartree.  Please additionally cite the original work when using this dataset.

```
article{
    doi:10.1021/acs.jcim.1c01346,
    author = {Rai, Brajesh K. and Sresht, Vishnu and Yang, Qingyi and Unwalla, Ray and Tu, Meihua and Mathiowetz, Alan M. and Bakken, Gregory A.},
    title = {TorsionNet: A Deep Neural Network to Rapidly Predict Small-Molecule Torsional Energy Profiles with the Accuracy of Quantum Mechanics},
    journal = {Journal of Chemical Information and Modeling},
    volume = {62},
    number = {4},
    pages = {785-800},
    year = {2022},
    doi = {10.1021/acs.jcim.1c01346},
    note ={PMID: 35119861},
    URL = {
        https://doi.org/10.1021/acs.jcim.1c01346
    },
    eprint = {
        https://doi.org/10.1021/acs.jcim.1c01346
    }
}
```

### TorsiononTest2000

This dataset contains 2109 rotamer scans of molecular fragments covering an expanded element set and includes some ionic examples.  The reference energies are wB97X-D3BJ/def2-TZVPD and are given in Hartree. 

### tautobase
This dataset contains a subset of the tautomer pairs in the tautobase set.   The reference energies are wB97X-D3BJ/def2-TZVPD and are given in Hartree.  Please additionally cite the original work when using this dataset. 

```
article{doi:10.1021/acs.jcim.0c00035,
    author = {Wahl, Oya and Sander, Thomas},
    title = {Tautobase: An Open Tautomer Database},
    journal = {Journal of Chemical Information and Modeling},
    volume = {60},
    number = {3},
    pages = {1085-1089},
    year = {2020},
    doi = {10.1021/acs.jcim.0c00035},
        note ={PMID: 31967818},
    URL = {
        https://doi.org/10.1021/acs.jcim.0c00035
    },
    eprint = {
        https://doi.org/10.1021/acs.jcim.0c00035
    }
}
```

### OrganicCrystals_PBE-D3

This dataset is a collection of loose PBE-D3 optimizations of 20 sets of organic crystals.  The 20 systems were selected as challenging molecular systems from a prior study.  Each set spans an energy range of up to 12 kcal/mol and reference PBE-D3 energies are given in Rydberg.  Additionally, the number of molecules is given by the key `number_of_molecules` and it is customary to measure energy normalized to the number of molecules.  For each set, any crystals matching experimental forms are indicated with the key `experimental_match`, whose value gives the name of the CCDC ref code, the RMSD N of this match is given by the key `experimental_match_rmsd_n`.  When using this data please also cite the original work.

```
article{zhou2025CSP,
    title={A robust crystal structure prediction method to support small molecule drug development with large scale validation and blind study.},
    author={Zhou, Dong and Bier, Imanuel and Santra, Biswajit and Jacobson, Leif D. and Wu, Chuanjie and Garaizar Suarez, Adiran and Almaguer, Barbara Ramirez and Yu, Haoyu and Abel, Robert and Friesner, Richard A. and Wang, Lingle},
    journal={Nat. Commun.},
    volume={16},
    number={2210},
    year={2025},
    doi={https://doi.org/10.1038/s41467-025-57479-1}
}
```

### OrganicCrystals_PBE-D3_experimental_structures

This dataset is a collection of tight PBE-D3 optimizations of 20 sets of experimentally observed organic crystals.  The 20 systems were selected as challenging molecular systems from a prior study.  Each set gives known Z'=1 crystal forms and reference PBE-D3 energies are given in Rydberg.  Additionally, the number of molecules is given by the key `number_of_molecules` and it is customary to measure energy normalized to the number of molecules.  When using this data please also cite the original work (given in the previous sectionn).

## Reference

If using any of this data please cite our manuscript describing the data as well as MPNICE MLFF models.

```
@misc{weber2025efficientlongrangemachinelearning,
      title={Efficient Long-Range Machine Learning Force Fields for Liquid and Materials Properties}, 
      author={John L. Weber and Rishabh D. Guha and Garvit Agarwal and Yujing Wei and Aidan A. Fike and Xiaowei Xie and James Stevenson and Karl Leswing and Mathew D. Halls and Robert Abel and Leif D. Jacobson},
      year={2025},
      eprint={2505.06462},
      archivePrefix={arXiv},
      primaryClass={physics.chem-ph},
      url={https://arxiv.org/abs/2505.06462}, 
}
```
