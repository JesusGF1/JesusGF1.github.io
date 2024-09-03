
Convert your model to https://onnxruntime.ai/pytorch

Read in the provided h5ad file browser side using https://onnxruntime.ai/pytorch (this is the h5 lib as WASM)
 
If the cell x gene is located at the same place most of the time in an h5ad file then it may be possible to read the sample data into js/typescript and then hand it to ONNX
If we got all that to work then it looks like there are umap in js libraries, or that could just be a separate independant WASM on its own.

Or we can try going the pyodide route. I theory ONNX will utilize any client GPU (seems to support apple silicon as well)

