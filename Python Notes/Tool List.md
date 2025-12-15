
<!DOCTYPE html>
<body>

<h1>Python Interpreters 概覽（依與 CPython 相似度排序）</h1>

<!-- 表格置頂 -->
<table>
  <thead>
    <tr>
      <th>Interpreter</th>
      <th>Parser</th>
      <th>Difference vs CPython</th>
      <th>Compiler</th>
      <th>Difference vs CPython</th>
      <th>Virtual Machine</th>
      <th>Difference vs CPython</th>
      <th>Built-in Libraries</th>
      <th>Difference vs CPython</th>
      <th>Garbage Collector</th>
      <th>Difference vs CPython</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>CPython</td>
      <td>PEG parser</td>
      <td>None</td>
      <td>Compiles to Python bytecode</td>
      <td>None</td>
      <td>CPython Virtual Machine</td>
      <td>None</td>
      <td>Full Python standard library</td>
      <td>None</td>
      <td>Reference counting and cyclic garbage collection</td>
      <td>None</td>
    </tr>
    <tr>
      <td>Stackless Python</td>
      <td>CPython parser</td>
      <td>Same</td>
      <td>Compiles to Python bytecode</td>
      <td>Same</td>
      <td>Modified CPython Virtual Machine</td>
      <td>Removes C call stack, adds microthreads</td>
      <td>Python standard library</td>
      <td>Same</td>
      <td>Reference counting and cyclic garbage collection</td>
      <td>Same</td>
    </tr>
    <tr>
      <td>Nuitka</td>
      <td>CPython Abstract Syntax Tree</td>
      <td>Same</td>
      <td>Converts Python to C source code and compiles</td>
      <td>Native compilation instead of bytecode</td>
      <td>Embeds CPython Virtual Machine</td>
      <td>Same</td>
      <td>CPython standard library</td>
      <td>Same</td>
      <td>Reference counting and cyclic garbage collection</td>
      <td>Same</td>
    </tr>
    <tr>
      <td>Anaconda</td>
      <td>CPython parser</td>
      <td>Same</td>
      <td>CPython compiler</td>
      <td>Same</td>
      <td>CPython Virtual Machine</td>
      <td>Same</td>
      <td>Includes many pre-installed scientific and AI packages</td>
      <td>Adds extra libraries</td>
      <td>Reference counting and cyclic garbage collection</td>
      <td>Same</td>
    </tr>
    <tr>
      <td>Miniconda</td>
      <td>CPython parser</td>
      <td>Same</td>
      <td>CPython compiler</td>
      <td>Same</td>
      <td>CPython Virtual Machine</td>
      <td>Same</td>
      <td>Minimal pre-installed packages</td>
      <td>Reduced libraries</td>
      <td>Reference counting and cyclic garbage collection</td>
      <td>Same</td>
    </tr>
    <tr>
      <td>ActivePython</td>
      <td>CPython parser</td>
      <td>Same</td>
      <td>CPython compiler</td>
      <td>Same</td>
      <td>CPython Virtual Machine</td>
      <td>Same</td>
      <td>Includes verified and enterprise packages</td>
      <td>Adds enterprise support</td>
      <td>Reference counting and cyclic garbage collection</td>
      <td>Same</td>
    </tr>
    <tr>
      <td>PyPy</td>
      <td>Custom parser</td>
      <td>Different front-end</td>
      <td>Just-In-Time compilation to machine code</td>
      <td>Does not use Python bytecode</td>
      <td>PyPy Virtual Machine</td>
      <td>Not CPython evaluation loop</td>
      <td>Mostly Python standard library</td>
      <td>Some modules differ</td>
      <td>Incremental generational moving garbage collection</td>
      <td>Does not use reference counting</td>
    </tr>
    <tr>
      <td>MicroPython</td>
      <td>Minimal parser for Python subset</td>
      <td>Reduced syntax</td>
      <td>Compiles to MicroPython bytecode</td>
      <td>Different</td>
      <td>Lightweight Virtual Machine for microcontrollers</td>
      <td>Simplified execution model</td>
      <td>Minimal Python standard library plus hardware modules</td>
      <td>Reduced</td>
      <td>Mark-and-sweep garbage collection</td>
      <td>Different</td>
    </tr>
    <tr>
      <td>CircuitPython</td>
      <td>Same as MicroPython</td>
      <td>Same</td>
      <td>Same as MicroPython</td>
      <td>Same</td>
      <td>Same as MicroPython</td>
      <td>Same</td>
      <td>Adds Adafruit hardware libraries</td>
      <td>Expanded hardware support</td>
      <td>Mark-and-sweep garbage collection</td>
      <td>Same as MicroPython</td>
    </tr>
    <tr>
      <td>Jython</td>
      <td>ANTLR-based parser</td>
      <td>Different parser</td>
      <td>Compiles to Java Virtual Machine bytecode</td>
      <td>Does not use Python bytecode</td>
      <td>Runs on Java Virtual Machine</td>
      <td>No Python Virtual Machine</td>
      <td>Java-based libraries</td>
      <td>No CPython C extensions</td>
      <td>Java Virtual Machine garbage collection</td>
      <td>Does not use reference counting</td>
    </tr>
    <tr>
      <td>IronPython</td>
      <td>Dynamic Language Runtime parser</td>
      <td>Different parser</td>
      <td>Compiles to .NET Intermediate Language</td>
      <td>Does not use Python bytecode</td>
      <td>Runs on .NET Common Language Runtime</td>
      <td>No Python Virtual Machine</td>
      <td>.NET Base Class Library</td>
      <td>No CPython C extensions</td>
      <td>.NET garbage collection</td>
      <td>Does not use reference counting</td>
    </tr>
    <tr>
      <td>PyJs</td>
      <td>Python to JavaScript transpiler</td>
      <td>Different parser</td>
      <td>Converts to JavaScript code</td>
      <td>Does not use Python bytecode</td>
      <td>Runs on JavaScript engine</td>
      <td>No Python Virtual Machine</td>
      <td>JavaScript-based libraries</td>
      <td>Different</td>
      <td>JavaScript engine garbage collection</td>
      <td>Different</td>
    </tr>
  </tbody>
</table>

<!-- 每個欄位分行呈現：Description / Pros / Cons / Use case -->
<section>
  <h2>1) CPython</h2>
  <p class="line"><span class="label">Description：</span>CPython 是官方參考實作，整體流程為 <span class="tag">PEG parser</span> 解析原始碼、建立 <span class="tag">AST</span>，編譯為 <span class="tag">Python bytecode</span>，最後由以堆疊為核心的 <span class="tag">CPython Virtual Machine</span> 逐條執行；記憶體管理採 <span class="tag">reference counting</span> 搭配 <span class="tag">cyclic garbage collection</span> 清除循環參考；並提供完整 <span class="tag">Python standard library</span> 與大量 C 擴充。此設計的核心目標是語義穩定與可預期，讓除錯、相容與教學都很可靠，初學者易懂、工程師好維運。</p>
  <p class="line"><span class="label">Pros：</span>相容性最佳、標準庫完整、生態龐大、除錯容易。</p>
  <p class="line"><span class="label">Cons：</span>受 <span class="tag">GIL</span> 限制，純 Python 多線程無法真正平行；缺少 JIT 動態最佳化，CPU-bound 效能一般。</p>
  <p class="line"><span class="label">Use case：</span>通用後端、資料處理、科學計算（仰賴 C 擴充）、教育與自動化腳本。</p>
</section>

<section>
  <h2>2) Stackless Python</h2>
  <p class="line"><span class="label">Description：</span>Stackless 是 CPython 的分支，保留同樣的語法解析與 bytecode，但在 <span class="tag">Virtual Machine</span> 層重新設計呼叫堆疊管理，移除對 C call stack 的依賴，提供 <span class="tag">microthreads（tasklets）</span>、<span class="tag">channels</span> 與排程器，讓大量協作式任務能以極低成本在單執行緒間切換，並可 <span class="tag">pickle</span> 任務狀態以持久化或遷移。</p>
  <p class="line"><span class="label">Pros：</span>協作式高並發容易表達、切換成本低、狀態可序列化。</p>
  <p class="line"><span class="label">Cons：</span>社群較小眾，與主流 <span class="tag">async/await</span> 生態並行時採用成本較高；維護速度不若 CPython。</p>
  <p class="line"><span class="label">Use case：</span>遊戲伺服器、模擬系統、工作流引擎等需要大量協作式任務的場景。</p>
</section>

<section>
  <h2>3) Nuitka</h2>
  <p class="line"><span class="label">Description：</span>Nuitka 以 CPython 的 <span class="tag">AST</span> 為前端，將 Python 轉為 <span class="tag">C source code</span>，再由系統編譯器（GCC/Clang/MSVC）產生可執行檔或擴充模組；為保持語義相容，執行時會 <span class="tag">嵌入 CPython runtime/VM</span>。這種 AOT 打包路徑讓 Python 程式能像傳統編譯語言一樣分發，部署更單純。</p>
  <p class="line"><span class="label">Pros：</span>部署友善（single executable）、部分情境有效能提升、降低原始碼可見性。</p>
  <p class="line"><span class="label">Cons：</span>仍依賴 CPython 執行期，效能提升因工作負載而異；建置流程較複雜、建置時間增加。</p>
  <p class="line"><span class="label">Use case：</span>桌面封裝、商業軟體分發、需要簡化部署與保護原始碼的情境。</p>
</section>

<section>
  <h2>4) Anaconda</h2>
  <p class="line"><span class="label">Description：</span>Anaconda 是以 <span class="tag">CPython</span> 為核心的 <span class="tag">distribution</span>，整合 <span class="tag">conda</span> 套件與環境管理、圖形化工具（Navigator），並提供大量 <span class="tag">pre-installed scientific/AI packages</span>（例如 NumPy、pandas、scikit-learn、Jupyter）。設計重點在於「環境再現性與二進位套件」，減少依賴衝突與編譯困難。</p>
  <p class="line"><span class="label">Pros：</span>安裝即用、依賴管理穩定、科學計算生態開箱即用。</p>
  <p class="line"><span class="label">Cons：</span>安裝體積大，容器或生產部署時需精簡。</p>
  <p class="line"><span class="label">Use case：</span>資料科學教學、探索性分析、快速建立 data science 工作站與原型。</p>
</section>

<section>
  <h2>5) Miniconda</h2>
  <p class="line"><span class="label">Description：</span>Miniconda 是 <span class="tag">CPython-based distribution</span> 的「極簡版」，只包含 <span class="tag">conda</span> 與少量必要元件。使用者自行安裝所需套件，保留 conda 的依賴解決與環境隔離能力，同時將初始體積與映像大小降到最低。</p>
  <p class="line"><span class="label">Pros：</span>最小化安裝、可精準控制依賴與映像大小、保留 conda 生態優勢。</p>
  <p class="line"><span class="label">Cons：</span>需要時間挑選與安裝套件，初期導入不如 Anaconda 便利。</p>
  <p class="line"><span class="label">Use case：</span>生產環境、容器部署、DevOps 工作流，需要高可再現性與精簡映像的場景。</p>
</section>

<section>
  <h2>6) ActivePython</h2>
  <p class="line"><span class="label">Description：</span>ActivePython 是商用的 <span class="tag">CPython-based distribution</span>，提供預編譯、驗證過的套件組合，以及版本與授權管理、維護與安全更新；重點在於企業級的「供應鏈可控與技術支援」，讓開源在企業內更安全可靠。</p>
  <p class="line"><span class="label">Pros：</span>企業級支援、套件供應鏈可控、授權與安全合規管理。</p>
  <p class="line"><span class="label">Cons：</span>商業成本、套件選型受供應商策略影響、社群自由度較低。</p>
  <p class="line"><span class="label">Use case：</span>金融、政府、醫療等重視合規與維護的企業環境。</p>
</section>

<section>
  <h2>7) PyPy</h2>
  <p class="line"><span class="label">Description：</span>PyPy 是替代的 Python 實作，採自訂前端與 <span class="tag">PyPy Virtual Machine</span>，以 <span class="tag">Tracing JIT</span> 將執行中的「熱路徑」動態編譯為 <span class="tag">machine code</span>，並使用 <span class="tag">incremental generational moving GC</span>。目標是提升「純 Python」程式在執行期間的效能與互動性。</p>
  <p class="line"><span class="label">Pros：</span>純 Python 的 CPU-bound 任務常見顯著效能提升、GC 停頓較低、迴圈密集表現佳。</p>
  <p class="line"><span class="label">Cons：</span>與 CPython 的 <span class="tag">C extension</span> 相容性不完全；大量依賴 C-層的情境優勢有限。</p>
  <p class="line"><span class="label">Use case：</span>演算法研究與迭代、解題平台、需要純 Python 快速的計算密集型應用。</  <p class="line"><span class="label">Use case：</span>演算法研究與迭代、解題平台、需要純 Python 快速的計算密集型應用。</p>
</section>

<section>
  <h2>8) MicroPython</h2>
  <p class="line"><span class="label">Description：</span>MicroPython 面向微控制器（MCU），使用 <span class="tag">minimal parser</span>、<span class="tag">MicroPython bytecode</span> 與 <span class="tag">lightweight VM</span>，標準庫精簡並提供硬體導向模組（GPIO、I2C、SPI）；記憶體以 <span class="tag">mark-and-sweep garbage collection</span> 搭配固定大小區塊管理，以適應極小的 RAM。</p>
  <p class="line"><span class="label">Pros：</span>極低資源占用、可直接驅動硬體、適合快速原型與教學板子。</p>
  <p class="line"><span class="label">Cons：</span>語言與標準庫是子集，與桌面 Python 程式不一定相容；效能與容量受 MCU 限制。</p>
  <p class="line"><span class="label">Use case：</span>IoT 節點、教育用微控板（ESP32、RP2040 等）、感測器控制與輕量嵌入式應用。</p>
</section>

<section>
  <h2>9) CircuitPython</h2>
  <p class="line"><span class="label">Description：</span>CircuitPython 基於 MicroPython，沿用輕量 VM 與 GC，但強調 <span class="tag">edit–save–run</span> 的即時開發體驗、統一且友善的硬體 API，以及大量的 <span class="tag">Adafruit hardware libraries</span>；設計焦點是讓初學者能用一致介面快速操作各式周邊。</p>
  <p class="line"><span class="label">Pros：</span>學習門檻低、裝置支援一致、開發體驗優良（USB Mass Storage、REPL）。</p>
  <p class="line"><span class="label">Cons：</span>對非 Adafruit 板子或高階硬體控制彈性較小、部分底層特性被抽象化。</p>
  <p class="line"><span class="label">Use case：</span>K12/STEM 教學、互動裝置與藝術專案、快速硬體原型。</p>
</section>

<section>
  <h2>10) Jython</h2>
  <p class="line"><span class="label">Description：</span>Jython 使用 <span class="tag">ANTLR parser</span>，將 Python 直接編譯為 <span class="tag">JVM bytecode</span>，在 <span class="tag">Java Virtual Machine</span> 上執行，並可直接使用 <span class="tag">Java libraries</span>；記憶體管理交由 JVM。這使 Python 能無縫整合 Java 生態與工具鏈，適合深度 JVM 場景。</p>
  <p class="line"><span class="label">Pros：</span>與 Java 生態高度整合、跨平台與部署受益於 JVM。</p>
  <p class="line"><span class="label">Cons：</span>不支援 CPython 的 C 擴充，科學計算生態相容性有限；語言版本更新節奏不一定與 CPython 同步。</p>
  <p class="line"><span class="label">Use case：</span>企業 Java 系統中的 Python 腳本整合、需要 Java 互通的應用。</p>
</section>

<section>
  <h2>11) IronPython</h2>
  <p class="line"><span class="label">Description：</span>IronPython 以 <span class="tag">Dynamic Language Runtime</span> 解析 Python，編譯成 <span class="tag">.NET Intermediate Language</span>，在 <span class="tag">.NET Common Language Runtime</span> 上執行，並直接使用 <span class="tag">.NET Base Class Library</span>；記憶體管理由 .NET 垃圾回收負責。此結構讓 Python 與 .NET 應用高度整合，方便在 Windows 生態中擴充。</p>
  <p class="line"><span class="label">Pros：</span>與 .NET 生態原生整合、可嵌入 WPF/WinForms/ASP.NET 等應用。</p>
  <p class="line"><span class="label">Cons：</span>不相容 CPython 的 C 擴充，科學套件生態連動有限；維護與語言版本節奏可能與 CPython 有差距。</p>
  <p class="line"><span class="label">Use case：</span>Windows 桌面或伺服器系統的 .NET 互通腳本、企業工具擴展。</p>
</section>

<section>
  <h2>12) PyJs</h2>
  <p class="line"><span class="label">Description：</span>PyJs 屬於 <span class="tag">transpiler</span>，將 Python 程式碼轉為 <span class="tag">JavaScript</span>，在瀏覽器或 Node.js 的 <span class="tag">JavaScript engine</span> 上執行；它不使用 Python VM，標準庫須以 JS 生態的等效庫替代，記憶體管理依 JS 引擎垃圾回收。此模式讓熟悉 Python 的人以 Python 語法進入 web/Node.js 平台，同時保留前端部署優勢。</p>
  <p class="line"><span class="label">Pros：</span>可用 Python 語法進入 web/Node.js、生態互通易於教學與原型。</p>
  <p class="line"><span class="label">Cons：</span>並非完整 Python 語義，標準庫差異大；效能與除錯品質仰賴 JS 引擎與轉譯品質。</p>
  <p class="line"><span class="label">Use case：</span>以 Python 撰寫但部署在 web/JS 的原型、教學或實驗性專案。</p>
</section>

</body>

