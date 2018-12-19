# Cancel All My Appointments
## Kyle Simpson

* Cancellation Happens 
    * Cancel/Quite/Terminate: Final
    * Pause/Undo: Recover/Rollback
* Events are expected
    * But States are expected
    * Cancellation should be a predictable state
    * If not we introduce uncertainty
* Halting problem
    * Mathematically proven that we cannot determine if a program will run forever
    * Often we use timeouts to approximate the halting problem
        * Wait a certain amount of time before *assuming* that it is going to run forever
        * But don't do anything to *stop* the task from running (and potentially completing)
    * Uncertainty is unacceptable in the system
        * Schrodinger: can the system be in 2 x states at once? No.
        * E.g. JS promises
            * should not be cancelable
            * if one part of the system decides it should be cancelled, other parts are hard to maintain
* Examples
    * Users
        * Cancellation should be a first-class citizen
        * At every touch point we should expect users to cancel things if they're not prepared to wait
    * Developers
        * Some things already have cancellation (AJAX `fetch`) but not many
        * Filesystem, I/O, Database operations: generally not
* Events vs State
    * Events
        * Edge Triggered
        * Can be missed
    * States
        * Level Triggered
        * Can always be polled
* Timeouts vs Deadlines
    * Timeouts are at the wrong layer of abstraction. Non-deterministic.
    * Deadlines are deterministic
* Further reading
    * https://vorpus.org/blog/timeouts-and-cancellation-for-humans/
