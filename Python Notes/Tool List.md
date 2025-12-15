
<table border="1" style="border-collapse: collapse; width: 100%; font-family: Arial, sans-serif;">
  <thead style="background-color: #f2f2f2;">
    <tr>
      <th>Interpreter</th>
      <th>Parser</th>
      <th>Compiler</th>
      <th>PVM / Execution Engine</th>
      <th>Built-in Libraries</th>
      <th>Garbage Collector</th>
      <th>Changed vs CPython</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>CPython</td>
      <td>PEG-based parser</td>
      <td>AST → Bytecode compiler</td>
      <td>CPython Virtual Machine</td>
      <td>Full Python Standard Library</td>
      <td>Reference counting + cyclic GC</td>
      <td>Baseline</td>
    </tr>
    <tr>
      <td>PyPy</td>
      <td>Python syntax parser</td>
      <td>Tracing JIT compiler</td>
      <td>PyPy VM with JIT</td>
      <td>Mostly compatible with stdlib</td>
      <td>Incremental generational moving GC</td>
      <td>JIT + different GC</td>
    </tr>
    <tr>
      <td>Jython</td>
      <td>Python parser</td>
      <td>Compiles to JVM bytecode</td>
      <td>JVM (Java Virtual Machine)</td>
      <td>Java libraries + Python stdlib subset</td>
      <td>JVM GC (depends on JVM)</td>
      <td>Runs on JVM</td>
    </tr>
    <tr>
      <td>IronPython</td>
      <td>Python parser</td>
      <td>Compiles to .NET IL</td>
      <td>.NET CLR</td>
      <td>.NET libraries + Python stdlib subset</td>
      <td>CLR GC (generational)</td>
      <td>Runs on .NET</td>
    </tr>
    <tr>
      <td>Nuitka</td>
      <td>CPython parser</td>
      <td>Translates to C/C++ → native binary</td>
      <td>Uses CPython runtime (libpython)</td>
      <td>Full Python Standard Library</td>
      <td>Same as CPython (via libpython)</td>
      <td>Deployment change</td>
    </tr>
    <tr>
      <td>PyJs</td>
      <td>Python parser</td>
      <td>Transpiles to JavaScript</td>
      <td>JavaScript engine (V8, etc.)</td>
      <td>Emulated Python libs in JS</td>
      <td>JS engine GC</td>
      <td>Target is JS</td>
    </tr>
    <tr>
      <td>Stackless Python</td>
      <td>CPython parser</td>
      <td>Same as CPython</td>
      <td>Modified CPython VM (stackless)</td>
      <td>Full Python Standard Library</td>
      <td>Same as CPython</td>
      <td>Adds microthreads</td>
    </tr>
    <tr>
      <td>MicroPython</td>
      <td>Lightweight parser</td>
      <td>Compiles to minimal bytecode</td>
      <td>Embedded lightweight VM</td>
      <td>Minimal stdlib + u* micro-libraries</td>
      <td>Generational GC with thresholds</td>
      <td>Embedded-focused</td>
    </tr>
    <tr>
      <td>Anaconda</td>
      <td>CPython parser</td>
      <td>Same as CPython</td>
      <td>CPython VM</td>
      <td>Full stdlib + scientific packages</td>
      <td>Same as CPython</td>
      <td>Distribution only</td>
    </tr>
    <tr>
      <td>Miniconda</td>
      <td>CPython parser</td>
      <td>Same as CPython</td>
      <td>CPython VM</td>
      <td>Minimal stdlib (expandable via conda)</td>
      <td>Same as CPython</td>
      <td>Distribution only</td>
    </tr>
    <tr>
      <td>CircuitPython</td>
      <td>MicroPython-based</td>
      <td>Minimal bytecode compiler</td>
      <td>Embedded VM (MicroPython fork)</td>
      <td>Hardware-focused libraries (Adafruit)</td>
      <td>Same as MicroPython GC</td>
      <td>Hardware-focused</td>
    </tr>
    <tr>
      <td>ActivePython</td>
      <td>CPython parser</td>
      <td>Same as CPython</td>
      <td>CPython VM</td>
      <td>Full stdlib + curated packages</td>
           <td>Same as CPython</td>
      <td>Commercial distro</td>
    </tr>
  </tbody>


