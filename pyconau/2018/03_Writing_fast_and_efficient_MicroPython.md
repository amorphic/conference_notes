# Writing fast and efficient MicroPython
## Damien George

* Compiler
    * reads input steream char-by-char
	* can leave memory fragmented from parse tree
	* all iedntifiers are left in RAM
		* use short / reuse!
* Micropython Bytecodes
	* Simple 1-byte codes that can implement *all of python*
	* Locals are faster than globals!
		* LOAD_GLOBAL - slow
		* LOAD_FAST 0 (top on stack)
	* Loading methods are slow!
	    * Pre-load
* Memory
    * Try not to allocate memory
	* Core consructs don't allocate on the heap
		* expressions
		* if, while, for etc
		* local vars
		* small int arithmetic
		* in-place ops on *existing* data structures
		* calling functions/methods with positional of keyword args
		* importing 
		* defining functions and classes
	    * assigning globals for the first time
		* creating data structures
	* Optimising
	    * don't use heap!
		* shorter vars names
		* temp buffers: self.buf1 = bytearray(1)
		* user `XXX_into` methods
		* don't use `*` or `**`)
		* script minification
		* use `mpy-cross` to produce `.mpy` (avoid re-compilation - speed + memory usage!)
		* ultimate solution: freeze into firmware (uses zero RAM)
CPU
	* use functions, not global scope
	* cache module functions and objects methods as locals
	* cache self variables as locals
	* perfer long expressions, not split up ones
	* runtime is faster than Python, use it; eg `str.startswith`
	* `from micropython import const; _X = const(1)`
* Blink Example
    * Putting loop into function: 55Khz -> 66Khz (no more globals)
	* Preloading a function (`on=led.on`) -> 182Khz (avoid looking up dicts)
    * Remove loop overhead (unload loop - loops within loops)
	* @micropython.native decorator -> 182Khz -> 288Khz (executes machine instruction directly rather than calling bytecode)
	* @micropython.viper decorator -> 12800Khz (!) (crazy macine code / python hybrid - low level stuff like register access)
	* @micropython.asm_thumb -> 27359Khz (inline assembler in pyton syntax) 
* Read Data Example
    * Stop memory allocating inside the loop: 1.5MB/sec -> 20MB/sec
	* RAM allocation is slow. Avoid it!
* Summary
	* Energy use: faster code sleeps longer
	* Only optimise bottlenecks
		* Programmer time
		* Debugging effort
		* Python is ~100x slower than C
			* But a lot is C under the hood
			* Use runtime methods 
	* Use locals, pre-allocate memory, cache
	* Use bound methods (pre-loaded: `.startswith()` etc) 
