# hyperbolic-floquet-data

This repository contains Stim circuits and parameters for the hyperbolic and semi-hyperbolic Floquet codes constructed for the paper "[Constructions and performance of hyperbolic and semi-hyperbolic Floquet codes](https://arxiv.org/abs/2308.03750)".

### Stim circuits

Each directory `circuits/r.g.b/k=X_Y` contains a family of semi-hyperbolic Floquet codes encoding `k=X` logical qubits,
constructed using a uniform `r.g.b` tiling as a seed tiling. The suffix `Y` in the
subdirectory is an 8-character unique id used to label the seed tiling for the family of semi-hyperbolic codes (since
there can be more than one family of
semi-hyperbolic codes with a given `k`).
Each Stim circuit has a filename with this structure of key-value
pairs: `semi_hyperbolic_floquet_l=1_n=16_k=4_d=2_basis=Z_num_sub_rounds=96_noise_model=SDEM3_p=0.0.stim`.
Here `l` is the fine-graining parameter, `n` is the number of data qubits, `k` is the number of logical qubis, `d` is
the embedded distance and
`basis` is the basis of logical observables prepared or measured (`X` or `Z`). `num_sub_rounds` is the number of
sub-rounds, `noise_model` is a string specifying the noise model
and `p` is the noise strength. The vast majority of the circuits have `noise_model=SDEM3_p=0.0` which is simply a
circuit with no noise instructions at all.
However, the [[16,4,2]] Bolza code in the 8.8.8 directory also has circuits for EM3, SD6 and DP1 noise models, all
at `p=0.001`. 
The EM3 and SD6 noise models are described in our paper.
The DP1 noise model is a simple noise model where a single layer of single-qubit depolarising noise 
is applied to all the data qubits after twelve sub-rounds, while all other operations (including measurements)
are implemented perfectly without noise.
DP1 is therefore essentially a "code capacity" noise model.
Note that the representatives of the logical operators used for the
Bolza code in this repository is not the same as shown in the figures in the paper (in the paper we give a symplectic
basis, whereas the logicals here are not symplectic).

### Parameters CSV

We also provide two CSV files in the `parameters` directory: `hyperbolic_parameters.csv` and 
`semi_hyperbolic_parameters.csv`.
The `semi_hyperbolic_parameters.csv` file gives all the parameters we computed for all the hyperbolic 
Floquet codes we constructed.
The `hyperbolic_parameters.csv` file gives the parameters for the subset constructed from purely 
hyperbolic (rather than semi-hyperbolic) tilings.
The column headers `em3_distance`, `sd6_distance` and `dp1_distance` give the circuit distance 
for the EM3, SD6 and DP1 noise models, respectively.

### Attribution

When using this repository for research, please cite the [paper](https://arxiv.org/abs/2308.03750):

```
@article{higgott2023constructions,
      title={Constructions and performance of hyperbolic and semi-hyperbolic Floquet codes}, 
      author={Oscar Higgott and Nikolas P. Breuckmann},
      year={2023},
      eprint={2308.03750},
      archivePrefix={arXiv},
      primaryClass={quant-ph}
}
```
