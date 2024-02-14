# Proof producer for the =nil; Proof Market
This repository contains the proof producer for the =nil; [Proof Market](https://proof.market/), which is a part of the =nil; [zkllvm toolchain](https://github.com/NilFoundation/zkLLVM) for zk-enabled applications development.

# How to use

The input for the proof producer is a circified version of the algorithm to be proven. This circified version of the algorithm is generated by the [zkllvm](https://raw.githubusercontent.com/NilFoundation/zkllvm) toolchain.

Typically, you want to use the proof producer to participate in the =nil; Proof Market. In this case, you need to have a valid account on the =nil; Proof Market, which you can create through the [Proof Market web interface](https://proof.market/) or by using the [Proof Market CLI](https://github.com/NilFoundation/proof-market-toolchain/).

# Installation

All parts of the zkLLVM toolchain are distributed in form of deb packages. To install them, you need to add the =nil; repository to your systems package manager:

```bash
echo 'deb [trusted=yes]  http://deb.nil.foundation/ubuntu/ all main' >>/etc/apt/sources.list
apt update
```

Then, you can install the proof producer by running:

```bash
apt install proof-producer
```

# Usage

The proof producer is a command line tool. To see the list of available options, run:

```bash
proof-generator --help
```

To produce a proof, you need to provide the proof producer with the file with the circuit definition and the assignment table with the values of the execution trace. You generate them from the [zkllvm examples](https://github.com/NilFoundation/zkLLVM) or download the existing ones using the [Proof Market CLI](https://github.com/NilFoundation/proof-market-toolchain/).

When you have the circuit definition and the assignment table, you can produce a proof by running:

```bash
proof-generator --circuit <circuit-file> --assignment <assignment-file> --proof <proof-file>
```

# Building from source
1. Install dependencies:
    ```
    sudo apt-get install \
        build-essential \
        libsctp-dev \
        libssl-dev \
        libicu-dev \
        lsb-release \
        gnutls-dev \
        pkg-config
    ```

2. Build with CMake:
    ```mkdir build
    cd build
    cmake ..
    make -j $(nrpoc)
    ```
