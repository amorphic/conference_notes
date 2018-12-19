Chris Ford - Functional Composition

* Musical notation
    * Designed for a particular finite state machine: a musician
    * Limited to one note at a time
        * No subroutine
* Harmonics
    * Same note can be a:
        * standing wave
        * split in 2, half height
        * split in 4, quarter height
        * etc
* Psycho-acoustics
    * Brian does "error correction"
    * Even if earlier harmonics are skipped, we hear the "correct note"
* Music as code
    * When the music is code, you separate concerns:
        * You can apply the timing separately (faster/slower)
        * You can apply the pitch separately (C major, D minor)
    * Use a base an intervals rather than specific notes
    * It's *not* expensive to create new abstractions (changing pitch, speed, etc)
    * A small change in the domain maps to a small change in the code
