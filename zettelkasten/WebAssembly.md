#public
WebAssembly is a w3c standard, that allows to run high performance tasks inside the browser. These high performance tasks are executed by a WebAssembly binary (wasm), which is retrieved from the backend and invoked in a Javascript component. Hence it is not supposed for replacing Javascript, which should still be used for manipulating the DOM. 
For development web-assembly components, code can be written in many programming languages and then be compiled into web-assembly.

### Commonly used languages
Several languages are well suited for WebAssembly. Generally these are languages, that that can compile down to the low-level binary format WASM. Examples for such languages are:
- C and C++
- Rust
- AssemblyScript (AS)
- Go 


### Performance
The performance of the resulting WebAssembly component depends on the language performance of the underlying language. Hence one should choose the right language. Recommended are Rust and C/C++


### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

