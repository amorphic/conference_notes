# Asyncio in (Micro)Python
## Matt Trentini 

* Background
	* A lot of experience on embedded devices
	* C toolchains are usually *terrible*
	* Tried a lot - settle don Micropython as it's perfect!
	* Talk is about *coroutines* - the ability to run code concurrently
* Coroutines
    * Minimal overhead, high performance
	* WHen we have control we have *complete control* (no locks to shared resources)
	* More closesly represents synchronous code
	* Better fit for commonly *blocking* tasks
* In Python
    * `async`/`await` keywords (Python 3.5+)
	* Built on generators
	* Event loop implemented in `asyncio` module
	* Decorate coroutine with `async` keyword
* In MicroPython
    * Technically some differences
	* Implementation is the same
	* Exciting
	    * Many embedded opeartions concurrent in nature
		* Different focus: more about expressing concurrent tasks than performance
		* Better power use is possible - event loop knows when it can sleep
* Examples
	* Debounce
		* Classic issue
		* Handling:
			* Block for debounce
			* Build handling
		* Micropython:
			* Loop waiting for button press
			* When pressed, sleep - yield control!
			* `micropython-async` lib has
				* Resource from Peter Hinch
				* `fast_io` - coming async replacement which is more efficient!
	* uPTV (train time display)
		* ntp (UTC only)
		* requests (blocking!)
		* led display driver (async)
		* `get_event_loop(), ``loop.create_task(X)``, ``loop.run_forever()`
	* Async LED fader
		* Two routines
			* One to query rotary encoder for level
			* One to set LEDs to level
* Picowebs
	* Async micropython server framework
	* https://github.com/pfalcon/picoweb
