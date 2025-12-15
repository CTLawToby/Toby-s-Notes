
<table>
  <thead>
    <tr>
      <th>Interpreter/Distribution</th>
      <th>partParser（語法解析器）</th>
      <th>Compiler（編譯器）</th>
      <th>PVM（Python Virtual Machine）</th>
      <th>Built-in Libraries（標準庫）</th>
      <th>Garbage Collector（記憶體管理）</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>CPython</td>
      <td>自家 parser 產生 AST；新 PEG-parser；流程 Parse→AST→Bytecode。 [3](https://devguide.python.org/internals/)</td>
      <td>AST→bytecode（pyc/__pycache__）；3.11 有 adaptive bytecode。 [3](https://devguide.python.org/internals/)[4](https://www.abhik.xyz/articles/cpython-internals)</td>
      <td>stack-based bytecode interpreter（PVM）。 [3](https://devguide.python.org/internals/)[5](https://developers-heaven.net/blog/the-cpython-interpreter-loop-how-python-executes-bytecode/)</td>
      <td>完整 Python 標準庫。 [3](https://devguide.python.org/internals/)</td>
      <td>Reference counting + cyclic GC；3.13 有 free-threaded build 的 GC 實作差異。 [6](https://github.com/python/cpython/blob/main/InternalDocs/garbage_collector.md)</td>
    </tr>
    <tr>
      <td>PyPy</td>
      <td>以 RPython 工具鏈，前端不同於 CPython。 [7](http://doc.pypy.org/)</td>
      <td>Tracing JIT 產生 machine code。 [7](http://doc.pypy.org/)[8](https://pypy.org/performance.html)</td>
      <td>PyPy 自身 VM（非 CPython eval loop）。 [7](http://doc.pypy.org/)</td>
      <td>力求相容但有差異與專屬模組。 [7](http://doc.pypy.org/)</td>
      <td>incminimark（incremental, generational, moving GC），可調/可步進。 [9](https://doc.pypy.org/en/latest/gc_info.html)[10](https://stackoverflow.com/questions/33712642/does-pypys-garbage-collector-need-to-stop-the-world)</td>
    </tr>
    <tr>
      <td>Jython</td>
      <td>ANTLR parser 產 AST。 [11](https://jython-devguide.readthedocs.io/en/latest/compiler_jy.html)[12](https://stackoverflow.com/questions/6856010/what-parser-do-jruby-and-jython-use-for-generating-jvm-bytecode)</td>
      <td>編譯為 JVM bytecode。 [12](https://stackoverflow.com/questions/6856010/what-parser-do-jruby-and-jython-use-for-generating-jvm-bytecode)</td>
      <td>執行於 JVM。 [13](https://faculty.kutztown.edu/parson/pubs/JythonPACISE2011.pdf)</td>
      <td>橋接 Java 生態，部分 CPython C 擴充不適用。 [13](https://faculty.kutztown.edu/parson/pubs/JythonPACISE2011.pdf)</td>
      <td>使用 JVM 的 GC。 [13](https://faculty.kutztown.edu/parson/pubs/JythonPACISE2011.pdf)</td>
    </tr>
    <tr>
      <td>IronPython</td>
      <td>DLR/自訂前端解析對映 .NET。 [14](https://learn.microsoft.com/en-us/archive/msdn-magazine/2006/october/clr-inside-out-ironpython)</td>
      <td>動態編譯並可產生 .NET assemblies。 [14](https://learn.microsoft.com/en-us/archive/msdn-magazine/2006/october/clr-inside-out-ironpython)</td>
      <td>執行於 .NET CLR。 [14](https://learn.microsoft.com/en-us/archive/msdn-magazine/2006/october/clr-inside-out-ironpython)</td>
      <td>可用 .NET BCL 與 clr 模組互通。 [15](https://ironpython.net/documentation/dotnet/dotnet.html)</td>
      <td>依賴 .NET GC；有相容 CPython C-API 的混合策略討論。 [16](https://github.com/dotnet/runtime/blob/main/docs/design/coreclr/botr/garbage-collection.md)[17](https://stackoverflow.com/questions/78026944/ironpython-garbage-collection-how-does-it-provides-compatibility-with-c-extens)</td>
    </tr>
    <tr>
      <td>Nuitka</td>
      <td>沿用 CPython 語法/AST。 [18](https://deepwiki.com/Nuitka/Nuitka)</td>
      <td>轉為 C（或早期 C++）並用系統編譯器；standalone 會嵌入 CPython。 [19](https://nuitka.net/user-documentation/user-manual.html)[20](https://en.wikipedia.org/wiki/Nuitka)</td>
      <td>運行時依 CPython VM/ABI。 [20](https://en.wikipedia.org/wiki/Nuitka)</td>
      <td>使用 CPython 標準庫並可打包依賴。 [19](https://nuitka.net/user-documentation/user-manual.html)</td>
      <td>沿用 CPython 的 refcount + cyclic GC。 [20](https://en.wikipedia.org/wiki/Nuitka)</td>
    </tr>
    <tr>
      <td>PyJs</td>
      <td>Python 前端解析後輸出 JS。 [21](https://www.javathinking.com/blog/convert-python-to-java-bytecode/)</td>
      <td>轉譯為 JavaScript。 [21](https://www.javathinking.com/blog/convert-python-to-java-bytecode/)</td>
      <td>執行於 JS 引擎（無 Python PVM）。 [21](https://www.javathinking.com/blog/convert-python-to-java-bytecode/)</td>
      <td>依 JS/瀏覽器環境實作等效庫。 [21](https://www.javathinking.com/blog/convert-python-to-java-bytecode/)</td>
      <td>採用 JS VM 的 GC。 [21](https://www.javathinking.com/blog/convert-python-to-java-bytecode/)</td>
    </tr>
    <tr>
      <td>Stackless Python</td>
      <td>與 CPython 前端相同。 [22](https://github.com/stackless-dev/stackless/wiki)</td>
      <td>同 CPython（bytecode）。 [22](https://github.com/stackless-dev/stackless/wiki)</td>
      <td>移除對 C stack 的依賴，提供 microthreads/tasklets、channels、排程器；專案已存檔。 [23](https://stackless.readthedocs.io/en/3.6-slp/stackless-python.html)[24](https://en.wikipedia.org/wiki/Stackless_Python)</td>
      <td>標準庫等同，另有 stackless 模組。 [23](https://stackless.readthedocs.io/en/3.6-slp/stackless-python.html)</td>
      <td>沿用 CPython 的記憶體管理。 [23](https://stackless.readthedocs.io/en/3.6-slp/stackless-python.html)</td>
    </tr>
    <tr>
      <td>MicroPython</td>
      <td>精簡前端，相容 Python 3 子集。 [25](https://picockpit.com/raspberry-pi/whats-the-difference-between-micropython-circuitpython-cpython-anyway/)</td>
      <td>編譯為 MicroPython bytecode。 [25](https://picockpit.com/raspberry-pi/whats-the-difference-between-micropython-circuitpython-cpython-anyway/)</td>
      <td>輕量 VM 面向 MCU。 [25](https://picockpit.com/raspberry-pi/whats-the-difference-between-micropython-circuitpython-cpython-anyway/)</td>
      <td>精簡標準庫 + 硬體導向模組。 [25](https://picockpit.com/raspberry-pi/whats-the-difference-between-micropython-circuitpython-cpython-anyway/)</td>
      <td>mark‑sweep GC、固定區塊與閾值；提供 gc API。 [26](https://docs.micropython.org/en/latest/library/gc.html)[27](https://deepwiki.com/lvgl/lv_micropython/2.3-memory-management-and-garbage-collection)</td>
    </tr>
    <tr>
      <td>CircuitPython</td>
      <td>MicroPython 分支，教學/板子友善。 [28](https://core-electronics.com.au/videos/circuitpython-vs-micropython-key-differences)</td>
      <td>同 MicroPython；強化 edit‑save‑run 流程。 [29](https://roboticcoding.com/circuitpython-vs-micropython/)</td>
      <td>輕量 VM，統一硬體 API。 [28](https://core-electronics.com.au/videos/circuitpython-vs-micropython-key-differences)</td>
      <td>Adafruit 大量周邊庫與一致 API。 [30](https://www.adafruitdaily.com/2025/02/17/python-on-microcontrollers-newsletter-comparing-python-micropython-and-circuitpython-pi-speed-and-more-circuitpython-python-micropython-thepsf-raspberry_pi/)[28](https://core-electronics.com.au/videos/circuitpython-vs-micropython-key-differences)</td>
      <td>沿用 MicroPython 的 GC。 [25](https://picockpit.com/raspberry-pi/whats-the-difference-between-micropython-circuitpython-cpython-anyway/)</td>
    </tr>
    <tr>
      <td>Anaconda</td>
      <td>Distribution：沿用 CPython parser。 [2](https://www.anaconda.com/topics/choosing-between-anaconda-vs-python)</td>
      <td>Distribution：沿用 CPython compiler。 [2](https://www.anaconda.com/topics/choosing-between-anaconda-vs-python)</td>
      <td>Distribution：沿用 CPython PVM。 [2](https://www.anaconda.com/topics/choosing-between-anaconda-vs-python)</td>
      <td>大量預載科學/AI 套件、conda/Navigator。 [1](https://www.dataschool.io/conda-vs-anaconda-vs-miniconda/)[2](https://www.anaconda.com/topics/choosing-between-anaconda-vs-python)</td>
      <td>Distribution：GC 與 CPython 同。 [1](https://www.dataschool.io/conda-vs-anaconda-vs-miniconda/)</td>
    </tr>
    <tr>
      <td>Miniconda</td>
      <td>同上（最小安裝）。 [31](https://stackoverflow.com/questions/45421163/anaconda-vs-miniconda)</td>
      <td>同上。 [31](https://stackoverflow.com/questions/45421163/anaconda-vs-miniconda)</td>
      <td>同上。 [31](https://stackoverflow.com/questions/45421163/anaconda-vs-miniconda)</td>
      <td>極簡，使用者自行安裝套件。 [31](https://stackoverflow.com/questions/45421163/anaconda-vs-miniconda)</td>
      <td>GC 與 CPython 同。 [31](https://stackoverflow.com/questions/45421163/anaconda-vs-miniconda)</td>
    </tr>
    <tr>
      <td>ActivePython</td>
      <td>商用發行版：沿用 CPython parser。 [32](https://wiki.python.org/moin/ActivePython)</td>
      <td>商用發行版：沿用 CPython compiler。 [32](https://wiki.python.org/moin/ActivePython)</td>
      <td>商用發行版：沿用 CPython PVM。 [33](https://docs.activestate.com/activepython/3.8/)</td>
      <td>預編譯/驗證的多數套件、企業支援。 [34](https://www.componentsource.com/product/activepython/about)[35](https://www.activestate.com/wp-content/uploads/2018/10/datasheet-activepython-v2.pdf)</td>
      <td>GC 與 CPython 同。 [34](https://www.componentsource.com/product/activepython/about)</td>
    </tr>
  </tbody>
</
