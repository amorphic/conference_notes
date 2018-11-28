# A Web without JavaScript
## Russell Keith-Magee 

* bit.ly/web-without-js
* Luhn Algorithm
	* Last CC digit 
* Options
	* Transpilation
        * CoffeeSCript
			* Source is more terse
		* Output Javascript is more verbose: slightly larger
	* Transcrypt
		* Python's scoping and paradigms are very different to Javascript
		* Output
			* *huge* - mostly providing builtins
			* All the DOM
			* All the builtins
			* Source level debugging
			* No REPL
			* None of the standard lib (no pip)
	* Javascript Python Interpreter
		* Brython
			* All the DOM
			* All the builtins
			* No source maps/debugging
			* Full REPL
			* Some of the stdlib
		* 646Kb download before anything works
			* Parser
			* Compiler
			* Eval loop
			* Standard Library
	* Javascript Python Bytecode Machine
		* Batavia
			* Ships code that provides a runtime
			* Removes the need for client-side compilation
			* Heavy: Byterun is a lightweight alternative
	* JIT Compilation	
		* ASM asm.js (JIT Javascript assembler)
		* Emscripten (emscripten.org)
			* C Code -> Clang -> Emscripten -> ASM
			* Still requires memory management
			* No access to DOM
			* Access to graphics/opengl
		* asm.js: still js code (source), parsed, interpreted, JIT'd, not small
	* Web Assembly (WASM)
		* Pre-compiled
		* C code -> Emscripten -> WAT -> WASM
		* Supported in all major browsers since 2017
	* Pyodide
		* Python -> CPython -> Clang -> Emscripten -> WASM
		* Big (3M)
		* No REPL, debug etc
	* Compile -> Webassembly
		* Rust compiles to Webassembly
		* RustPython
		* pythonvm-rust
* Missing
	* WASM support for the DOM
		* Right now only good for self-contained apps (eg games)
	* WASM support for GC
	* Stdlib implementation
	* Debugging
