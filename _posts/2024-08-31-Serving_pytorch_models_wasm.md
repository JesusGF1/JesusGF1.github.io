---
layout: post
title: "Serving PyTorch models in the browser with WebAssembly"
date: 2024-08-31
tags: [Deep Learning, Web]
excerpt: "Exploratory notes on running single-cell models client-side with ONNX Runtime and WebAssembly, with no server required."
---

These are some exploratory notes on running models entirely in the browser, so that a user can drop in their own data and get predictions without anything leaving their machine.

The rough plan:

- Convert the model to ONNX and run it with [ONNX Runtime Web](https://onnxruntime.ai/), which ships as WebAssembly.
- Read the provided `.h5ad` file on the client side using an HDF5 library compiled to WASM.
- If the cell-by-gene matrix sits in a predictable place inside the `.h5ad` file, it should be possible to read the sample data in JavaScript or TypeScript and hand it straight to ONNX.
- Once that works, there are UMAP implementations in JavaScript, or that step could run as its own separate WASM module.

An alternative is the Pyodide route (CPython compiled to WASM). In theory ONNX Runtime will use any client GPU it can find, and it seems to support Apple Silicon as well.

This is still a sketch, but the appeal is clear: a fully client-side, privacy-preserving way to serve models.
