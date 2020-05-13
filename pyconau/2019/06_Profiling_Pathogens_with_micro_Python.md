# Profiling Pathogens with (micro) Python
## Andrew Leech 

* Hardware: blood test reader
    * Previous
    * High-res cam
    * Built-in Image Processing
    * Battery
    * Bluetooth
    * Runs Python (algos already written for PC)
    * OpenMV
        * Low cost machine image device but not battery or medial grade
    * Created Lucos Camera Reader (custom)
* Software
    * Must report anything wrong as *error* (not produce invalid result)
    * Software of Unknown Providence
        * Most Open Source libs are not independently medically certified
        * ISO Framework for this: Black Box
            * Create tests that prove the Black Box works as expected
        * It is better to submit changes back to the SOUP layer projects than fork them
    * Debugging
        * Python: Code/Copy (no compile)
        * Jupyter works well on MicroPython!
            * jupyter remote kernel (PyPI)
            * Use this for early prototyping.
            * Use the `%local`  flag to do things on the local PC
            * E.g. crunch some numbers locally and do the IO on the micropython board
    * TDD
        * `micropython-unittest`
            * Run tests locally, in CI or on the board and they always work.
        * REPL
            * Fake breakpoints
            * Singelton drivers
            * Restartable app
            * Get a good serial terminal helps! (tyr tinycom)
    * Protect REPL
        * `uos.dupterm` can add multiple repls or remove them altogether
    * The ability to re-use standard Python code hugely speeds up development!
* Custom Board Dirs
    * Board
        * You can customise the board type for your build
    * Filesystem
        * Can remove defaults, add custom files etc
    * USB
        * Add branding, IDs etc
        * http://pid.codes (or buy a commerical code)
* Deployemnt
    * Freeze the code
    * Upgrade with `mboot`
