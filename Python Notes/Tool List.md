
<table border="1" style="border-collapse: collapse; width: 100%; font-family: Arial, sans-serif;">
  <thead style="background: #f2f2f2;">
    <tr>
      <th>Interpreter</th>
      <th>Language</th>
      <th>Engine / VM</th>
      <th>Compilation Strategy</th>
      <th>Concurrency Model</th>
      <th>Performance (Typical)</th>
      <th>FFI / Extension Support</th>
      <th>Platform Support</th>
      <th>License</th>
      <th>Typical Use Cases</th>
      <th>Notes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>CPython</td>
      <td>Python</td>
      <td>CPython VM (bytecode)</td>
      <td>Bytecode interpretation</td>
      <td>GIL; multi-process for parallel CPU</td>
      <td>Moderate</td>
      <td>Strong C-API; C/C++ extensions</td>
      <td>Cross-platform</td>
      <td>PSF License</td>
      <td>General Python, ecosystem default</td>
      <td>Most widely used Python interpreter</td>
    </tr>
    <tr>
      <td>PyPy</td>
      <td>Python</td>
      <td>RPython-based VM</td>
      <td>Tracing JIT compilation</td>
      <td>GIL (varies); multi-process for parallel CPU</td>
      <td>High (often faster than CPython)</td>
      <td>CPython C-API via cpyext (compat varies)</td>
      <td>Cross-platform</td>
      <td>MIT</td>
      <td>Long-running Python services, numeric</td>
      <td>Best for pure-Python code; JIT benefits</td>
    </tr>
    <tr>
      <td>Jython</td>
      <td>Python</td>
      <td>JVM (Java)</td>
      <td>Bytecode compiled to JVM classes</td>
      <td>JVM threads; no GIL</td>
      <td>Moderate to High (depends on JVM)</td>
      <td>Access Java libraries; no native CPython C-API</td>
      <td>Cross-platform (JVM)</td>
      <td>Apache License</td>
      <td>Java interop, enterprise environments</td>
      <td>Limited support for C-extension modules</td>
    </tr>
    <tr>
      <td>IronPython</td>
      <td>Python</td>
      <td>.NET CLR</td>
      <td>IL generation (CLR)</td>
      <td>.NET threads; no GIL</td>
      <td>Moderate to High (depends on CLR)</td>
      <td>Access .NET libraries; limited CPython C-API</td>
      <td>Windows/Linux/macOS (.NET)</td>
      <td>Apache License</td>
      <td>.NET interop, enterprise tooling</td>
      <td>Good for .NET ecosystems</td>
    </tr>
    <tr>
      <td>Node.js</td>
      <td>JavaScript</td>
      <td>V8</td>
      <td>JIT compilation (TurboFan, Ignition)</td>
      <td>Event loop, async I/O; single-threaded JS</td>
      <td>High for I/O workloads</td>
      <td>N-API; native addons (C/C++)</td>
      <td>Cross-platform</td>
      <td>MIT</td>
      <td>Web servers, tooling, microservices</td>
      <td>Strong ecosystem; vast package registry</td>
    </tr>
    <tr>
      <td>Deno</td>
      <td>JavaScript / TypeScript</td>
      <td>V8 + Rust runtime</td>
      <td>JIT (JS), TS transpilation</td>
      <td>Event loop, async I/O</td>
      <td>High for I/O workloads</td>
      <td>Foreign Function via FFI (unstable areas vary)</td>
      <td>Cross-platform</td>
      <td>MIT</td>
      <td>Secure-by-default server-side JS/TS</td>
      <td>Bundled tooling; permissions model</td>
    </tr>
    <tr>
      <td>Ruby MRI</td>
      <td>Ruby</td>
      <td>YARV (bytecode VM)</td>
      <td>Bytecode interpretation (some opt JIT)</td>
      <td>GIL-like (GVL); threads for I/O</td>
      <td>Moderate</td>
      <td>C extensions via Ruby C-API</td>
      <td>Cross-platform</td>
      <td>BSD-2-Clause</td>
      <td>Rails, scripting, web apps</td>
      <td>Default Ruby interpreter</td>
    </tr>
    <tr>
      <td>JRuby</td>
      <td>Ruby</td>
      <td>JVM</td>
      <td>JIT/HotSpot via JVM</td>
      <td>True parallel threads; no GVL</td>
      <td>High (JIT + JVM optimizations)</td>
      <td>Java interop; some C-ext via bridging</td>
      <td>Cross-platform (JVM)</td>
      <td>GPL/LGPL/Ruby (dual-licensing components)</td>
      <td>Enterprise Ruby, concurrency</td>
      <td>Excellent for multi-threaded Ruby</td>
    </tr>
    <tr>
      <td>TruffleRuby</td>
      <td>Ruby</td>
      <td>GraalVM</td>
      <td>Partial evaluation + JIT (Graal)</td>
      <td>True parallel threads</td>
      <td>High (often fastest Ruby)</td>
      <td>GraalVM polyglot; native interop</td>
      <td>Cross-platform (GraalVM)</td>
      <td>Universal Permissive License</td>
      <td>High-performance Ruby, polyglot</td>
      <td>Best with GraalVM ecosystem</td>
    </tr>
    <tr>
      <td>PHP (Zend Engine)</td>
      <td>PHP</td>
      <td>Zend Engine</td>
      <td>Opcode compilation + interpreter</td>
      <td>Multi-thread/process per SAPI; async via extensions</td>
      <td>Moderate to High with OPcache</td>
      <td>Extensions via C; FFI in modern versions</td>
      <td>Cross-platform</td>
      <td>PHP License</td>
      <td>Web apps, CMS, APIs</td>
      <td>OPcache greatly improves performance</td>
    </tr>
    <tr>
      <td>HHVM</td>
      <td>Hack / PHP (legacy)</td>
      <td>HHVM (JIT)</td>
      <td>JIT compilation</td>
      <td>Threaded; async primitives (Hack)</td>
      <td>High</td>
      <td>Extensions (C++); limited PHP compat today</td>
      <td>Linux (primary)</td>
      <td>PHP License</td>
      <td>Large-scale Hack services</td>
      <td>Optimized for Hack language</td>
    </tr>
    <tr>
      <td>Lua</td>
      <td>Lua</td>
      <td>Lua VM</td>
      <td>Bytecode interpretation</td>
      <td>Cooperative coroutines; single-threaded core</td>
      <td>High for embedding</td>
      <td>Simple C API for embedding</td>
      <td>Cross-platform</td>
      <td>MIT</td>
      <td>Game scripting, embedded systems</td>
      <td>Small footprint; easy to embed</td>
    </tr>
    <tr>
      <td>LuaJIT</td>
      <td>Lua</td>
      <td>LuaJIT</td>
      <td>JIT compilation</td>
      <td>Coroutines; single-threaded core</td>
      <td>Very High</td>
      <td>FFI for C; easy embedding</td>
      <td>Cross-platform</td>
      <td>MIT</td>
      <td>High-performance Lua scripting</td>
      <td>One of the fastest dynamic language JITs</td>
    </tr>
    <tr>
      <td>Perl</td>
      <td>Perl</td>
      <td>Perl interpreter</td>
      <td>Direct interpretation</td>
      <td>Threads via ithreads; processes common</td>
      <td>Moderate</td>
      <td>XS for C extensions</td>
      <td>Cross-platform</td>
      <td>Artistic License</td>
      <td>Text processing, sysadmin scripts</td>
      <td>Strong regex and text manipulation</td>
    </tr>
    <tr>
      <td>R</td>
      <td>R</td>
      <td>R interpreter</td>
      <td>Bytecode / interpretation (varies)</td>
      <td>Single-threaded R; parallel via packages</td>
      <td>Moderate</td>
      <td>Native C/C++/Fortran via .Call/.C</td>
      <td>Cross-platform</td>
      <td>GPL</td>
      <td>Statistical computing, data science</td>
      <td>Rich package ecosystem (CRAN)</td>
    </tr>
    <tr>
      <td>MATLAB</td>
      <td>MATLAB</td>
      <td>MATLAB engine</td>
      <td>Bytecode/JIT (proprietary)</td>
      <td>Multi-threaded math libs; parfor, toolbox APIs</td>
      <td>High for numeric workloads</td>
      <td>MEX interfaces (C/C++/Fortran)</td>
      <td>Windows/Linux/macOS</td>
      <td>Proprietary</td>
      <td>Numerical analysis, engineering</td>
      <td>Optimized BLAS/LAPACK; rich toolboxes</td>
    </tr>
    <tr>
      <td>GNU Octave</td>
      <td>Octave</td>
      <td>Octave interpreter</td>
      <td>Bytecode/interpretation</td>
      <td>Multi-threaded math via libraries</td>
      <td>Moderate to High</td>
      <td>Oct/MEX interfaces</td>
      <td>Cross-platform</td>
      <td>GPL</td>
      <td>Scientific computing (MATLAB-like)</td>
      <td>Open-source MATLAB alternative</td>
    </tr>
    <tr>
      <td>Bash</td>
      <td>Shell (Bash)</td>
      <td>Bash interpreter</td>
      <td>Direct interpretation</td>
      <td>Process-based concurrency (pipes, jobs)</td>
      <td>Varies by external commands</td>
      <td>POSIX utilities, shared libs</td>
      <td>Unix-like systems, Windows via WSL</td>
      <td>GPL</td>
      <td>Shell scripting, automation</td>
      <td>Excellent for orchestration of tools</td>
    </tr>
    <tr>
      <td>PHP-FPM (runtime mode)</td>
      <td>PHP</td>
      <td>Zend Engine + FPM</td>
      <td>Opcode + interpreter (precompiled cache)</td>
      <td>Process manager; isolated workers</td>
      <td>High for web workloads</td>
      <td>Extensions via C; FFI</td>
      <td>Cross-platform</td>
      <td>PHP License</td>
      <td>High-throughput web hosting</td>
      <td>Common deployment for PHP sites</td>
    </tr>
  </tbody>
</

