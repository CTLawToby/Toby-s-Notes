<h1><code>python --version</code> but <code>Python was not found; ...</code></h1>
<ol>
    <li><h2>The Problem</h2></li>
    <ol>
        <li>
            When I typed <code>python --version</code> in the command prompt,  <br />
            I received the message:<br />
            <code>Python was not found; run without arguments to install from the Microsoft Store, or disable this shortcut from Settings > Apps > Advanced app settings > App execution aliases."</code><br />
        </li>
        <li>
            This indicated that the system was not finding my actual Python installation.
        </li>
    </ol>
    <hr />
    <li><h2>The Cause</h2></li>
    <p>
        There is a file also named python.exe in the WindowsApps folder which is a Windows-provided shim designed to redirect users to the Microsoft Store for Python, and it was being prioritized over the actual Python executable.<br />
        (Please be sure the path of the actual python.exe is added)
    </p>
    <hr />
    <li><h2>The Solution</h2></li>
    <p>
        To resolve the issue, I renamed the python.exe file in the WindowsApps directory. <br />
        This change forced the system to use the correct Python executable, so that when <code>python --version</code> is typed, it returns the proper version information.
    </p>
    <hr />
    <li><h2>Details of the Complete Process of Solving the Issue</h2></li>
    <ol>
        <li>
            <h3>Initial Observation:</h3><br />
            I opened the command prompt and ran <code>python --version</code>. The error message appeared, suggesting that Python was not found and prompting installation from the Microsoft Store.
        </li>
        <li>
            <h3>Checking the PATH:</h3><br />
            I confirmed that my actual Python installation directory were added to the PATH environment variable. However, the error persisted.
        </li>
        <li>
            <h3>Diagnosing the Issue:</h3><br />
            I executed the command <code>where python</code> to see which executables were being found. The output revealed two files:
            <ul>
                <li>The python.exe in WindowsApps folder</li>
                <li>My actual python.exe</li>
            </ul>
            It became clear that the system was prioritizing the shim from WindowsApps, which is intended for directing users to the Microsoft Store.
        </li>
        <li>
            <h3>Implementing the Fix:</h3><br />
            I navigated to the directory of WindowsApps and renamed the python.exe shim file. This ensured that the system would no longer use the Microsoft Store version.
        </li>
        <li>
            <h3>Final Verification:</h3><br />
            After making the change, I closed all command prompt windows and opened a new one. I then ran <code>python --version</code> again, and this time, the command correctly displayed the version of the Python interpreter.
        </li>
    </ol>
    <hr />