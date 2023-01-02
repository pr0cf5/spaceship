# Source Directory Layout

The source directory consists of 3 directories: **core**, **cosmwasm**, and **python-bindings**. The **core** directory is a library crate that contains most of the implementations, and is used heavily by **python-bindings**, which exposes those implementations to Python scripters. **cosmwasm** is a minor fork of [cosmwasm](https://github.com/CosmWasm/cosmwasm/tree/v1.1.5). The reason for forking cosmwasm is to expose the `call_raw` API in `cosmwasm_vm` that is not public to external crates.

# Building and Installing

It is highly unlikely that users will use the **core** library directly, because doing so will make them write tests in pure rust. Instead, users are encouraged to write their tests in Python using the python bindings. We also encourage to use `virtualenv` instead of installing packages as root.

Thus, we initialize our virtualenv.

```bash
virtualenv env
source env/bin/activate
```

Before doing anything, the `maturin` tool must be installed.

```bash
pip install maturin
```

Then, traverse to the **python-bindings** directory and execute the following command:

```bash
maturin develop
```

This will install `spacecraft` to the current virtualenv. We can check if spacecraft is installed properly by importing it.

```python
import spacecraft
```
