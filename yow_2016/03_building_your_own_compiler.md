# Building Your Own Compiler The Slightly Easier Way With LLVM
## Erik Corry

* Background
 * V8 Developer
 * Now Dart developer
* How do we write our own compiler?
 * LLVM open source compiler framework
 * Nice tools, APIs
 * Nice intermediate format
 * Used in XCode
 * GC
 * JIT
* Demo
 * Dart
  * Tries to be nice to programmer
  * Short cycle time
  * Programmer UX
  * Web/IOS/Android
  * Tooling - Jetbrains
 * Compile RegExp
  * Parser
  * AST
  * Graphviz
 * LLVM
  * Bitcode
   * Intermediate rep
    * Can be ascii
    * What is shipped to specific platform
  * clang -emit-llvm
   * outputs LLVM code
   * clang looks at extension and decides what to do
 * Looking at assembler
  * All functions inlined to a single one (f0 
* Printf COmpiler (or use API
* Good Code QUalirt
* Big, friendly community 
* Don't buy the dragon book anymore
* Disadvantages
 * Compile times are slower
  * JIT can be too slow
   * Fine if you're compiling horizontally in the cloud)
   * Not so good if you're stopping and starting a phone app
  * IOS removed JIT compiler as it was too slow
* If developing a new language
 * Interpreted first for iteration
 * Dyanmic scope is *very* hard
  * E.g. eveal in JS
