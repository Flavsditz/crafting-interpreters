# Study Notes 

## Steps involved in the process:

### Front End
- **Scanning/Lexing** 
    - taking a stream of characters (let's say a line) and chunking together into **tokens** 
    - white spaces and comments are discarded at this step
- **Parsing**
    - the parser takes the sequence of tokens and builds a tree structure that follows the language grammar
    - This tree is called **parse tree** or **abstract syntax tree** (AST).
    - the parser will report **syntax errors**
- **Static Analysis**
    - **Binding/Resolution** happens here. Each identifier found gets enhanced with more context:
        - Where the name is defined (scope comes into play here)
        - IFF the language is statically typed here is where we figure the types out and report **type errors** if necessary
    - This data gets stored either as attibutes of the AST or in a lookup table where the keys are the indentifiers (the table is then called "Symbol Table")


### Middle End
Obs.: "middle end" exist as a term since in the old days when compilers were simple you only had FE and BE but as more things got added the term "middle end" got coined.

- **Intermediate Representation (IR)**
    - Here the code may be stored in some intermediate representation (IR). 
    - Having an IR allows you to support multiple source languages and target platforms with less effort.
- **Optimization**
    - If we understand the program that was handed to su and we know a more efficient way of doing the same thing we can swap these - that is optimization.

### Back end
- **Code generation**
    - The last step is to convert the code into a form a machine can run.
    - Here is the choice to generate machine code (which is very tied to an architecture) or bytecode for a virtual machine.

- **Virtual Machine**
    - If you chose this route you still have to "translate" your code into a machine specific language. This can be done in two ways
        - Mini-compiler - where you basically target each supported architecture (but reuse all steps before), the bytecode si almost an IR.
        - Virtual Machine (VM) - which emulates a hypothetical chip and supports your virtual architecture at runtime. You get simplicity and portability at the cost of speed of simulating at runtime these "virtual-chip" and its instructions.
            - If you implement your VM in, say C, you can run your language on any platform that has a C compiler.
- **Runtime**
    - If we decided to compile directly to machine code we just have to tell the OS to run the executable.
    - If we went for bytecode we need to startup the VM and load the program into it.
    - In both cases we need to provide services like garbage collection, "instance of" tests, etc. This collection of functionality is usually called **the runtime** of the language.
    - In a fully compiled language the runtime is inserted directly into the resulting executable.
    - In a language with a interpreter or VM the runtime lives inside those.(Java, Python, JS, etc)


## Shortcuts
Some languages don't do all the above. One can also:

- **Single-pass compilers**
    - No ASTs or IRs here. Directly taking parsing, analysis and code generation in one go.
    - These restrict the design of the language a bit since as soon as you see an expression you have to know enough to correcttly compile it. (e.g. Pascal and C)
- **Tree-walk interpreters**
    - You can executing code right after parsing it to an AST
    - The parser traverses the tree one branch and leaf at a time.
    - Not widely used for general purpose languages since it tends to be slow.
- **Transpilers**
    - Writing all the BE can be a lot so you can piggy back on someone else's work by translating your code into a valid version of the target language and let that pipeline take on the work. 
    - If the languages are similar enough this might be less work than if you need to do analysis and even optimization of your representation before generating the target representation.
- ** Just-in-time compilation**
    - This is a very advanced technique where profiling hooks are attached to the generated code and the type of data going through is analyzed so through time a region can be optimized and recompiled to be more efficient.

## Compiler vs Interpreter
Compiler takes code input and produces another (usually a lower-level) form. (transpilation falls under this too).
Interpreting means we take in source code and execute it immediately.
