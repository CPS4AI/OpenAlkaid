# ALKAID: Accelerating Three-Party Boolean Circuits by Mixing Correlations and Redundancy

We propose a round-efficient 3PC framework ALKAID for Boolean circuits through improved multi-input AND gate. By mixing correlations and redundancy, we propose a concretely efficient correlation generation approach for small input bits $N\le 4$ and shift the correlation generation to the preprocessing phase. Building on this, we create a round-efficient AND protocol for general cases with $N>4$. Exploiting the improved multi-input AND gates, we design fast depth-optimized parallel prefix adder and share conversion primitives in 3PC, achieved with new techniques and optimizations for better concrete efficiency.  We further apply these optimized primitives to enhance the efficiency of secure non-linear functions in machine learning. 

This repo contains a proof-of-concept implementation for our paper [ALKAID](https://eprint.iacr.org/2025/2298).

## 1. Setup
Follow the [README of SecretFlow-SPU](https://github.com/secretflow/spu) to set up the backend.

## 2. Benchmarking Alkaid

```shell
# microbenchmark from cpp side.
bazel build //examples/alkaid/benchmark:microbm --jobs 32
./bazel-bin/examples/alkaid/benchmark/microbm

# activation function benchmark from python side.
bazel build //examples/alkaid/utils:nodectl --jobs 32
bazel build //examples/alkaid/benchmark:actbm --jobs 32
./bazel-bin/examples/alkaid/utils/nodectl -c examples/alkaid/conf/alkaid.json up
./bazel-bin/examples/alkaid/benchmark/actbm -c examples/alkaid/conf/3pc.json
./bazel-bin/examples/alkaid/benchmark/actbm -c examples/alkaid/conf/alkaid.json

# gpt2 inference benchmark from python side.
bazel build //examples/alkaid/utils:nodectl --jobs 32
bazel build //examples/alkaid/benchmark:pumabm --jobs 32
./bazel-bin/examples/alkaid/utils/nodectl -c examples/alkaid/conf/alkaid.json up
./bazel-bin/examples/alkaid/benchmark/pumabm -c examples/alkaid/conf/3pc.json
./bazel-bin/examples/alkaid/benchmark/pumabm -c examples/alkaid/conf/alkaid.json
```

## 3. Citing
```text
@ARTICLE{11314596,
  author={Dong, Ye and Chen, Xudong and Song, Xiangfu and Yang, Yaxi and Lu, Wen-jie and Zhang, Tianwei and Zhou, Jianying and Dong, Jin-Song},
  journal={IEEE Transactions on Information Forensics and Security}, 
  title={ALKAID: Accelerating Three-Party Boolean Circuits by Mixing Correlations and Redundancy}, 
  year={2025},
  doi={10.1109/TIFS.2025.3648188}
}
```
