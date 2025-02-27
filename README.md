# go-faiss

1. build faiss

```sh
brew install libomp
export OpenMP_ROOT=$(brew --prefix)/opt/libomp
brew install swig

cd faiss

cmake \
-DFAISS_ENABLE_GPU=OFF \
-DFAISS_ENABLE_C_API=ON \
-DFAISS_ENABLE_PYTHON=OFF \
-DBUILD_SHARED_LIBS=ON \
-B build .

make -C build

```

2. when run test or use

```sh
export DYLD_LIBRARY_PATH="${PWD}/faiss/build/c_api:$DYLD_LIBRARY_PATH"
```

# the below came from original repo

[![Go Reference](https://pkg.go.dev/badge/github.com/DataIntelligenceCrew/go-faiss.svg)](https://pkg.go.dev/github.com/DataIntelligenceCrew/go-faiss)

Go bindings for [Faiss](https://github.com/facebookresearch/faiss), a library for vector similarity search.

## Install

First you will need to build and install Faiss:

```
git clone https://github.com/facebookresearch/faiss.git
cd faiss
cmake -B build -DFAISS_ENABLE_GPU=OFF -DFAISS_ENABLE_C_API=ON -DBUILD_SHARED_LIBS=ON .
make -C build
sudo make -C build install
```

Building will produce the dynamic library `faiss_c`.
You will need to install it in a place where your system will find it (e.g. `/usr/lib` on Linux).
You can do this with:

    sudo cp build/c_api/libfaiss_c.so /usr/lib

Now you can install the Go module:

    go get github.com/DataIntelligenceCrew/go-faiss

## Usage

API documentation is available at <https://pkg.go.dev/github.com/DataIntelligenceCrew/go-faiss>.
See the [Faiss wiki](https://github.com/facebookresearch/faiss/wiki) for more information.

Examples can be found in the [\_example](_example) directory.
