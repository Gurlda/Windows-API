</head>
<body>

  <h1>Understanding the Windows API</h1>

  <h2>What is the Windows API?</h2>
  <p>
    The <strong>Windows API (Application Programming Interface)</strong> is like a toolbox that Microsoft provides so software programs can talk to the Windows operating system. It helps apps do things like open files, display windows, use memory, and more—without breaking security rules.
  </p>

  <h2>Goals of the Windows API</h2>
  <ul>
    <li>Prevent direct access to hardware</li>
    <li>Provide system services to software</li>
    <li>Maintain compatibility across Windows versions</li>
    <li>Ensure consistency for developers</li>
  </ul>

  <h2>Two Main Types of APIs</h2>
  <h3>User-Mode APIs</h3>
  <p>These are everyday functions used by most apps, found in <code>kernel32.dll</code>, <code>user32.dll</code>, and <code>advapi32.dll</code>.</p>

  <h3>Native APIs (NT APIs)</h3>
  <p>More powerful, lower-level functions found in <code>ntdll.dll</code>. These are often used by advanced tools and attackers to avoid detection.</p>

  <h2>User Mode vs Kernel Mode</h2>
  <table>
    <thead>
      <tr>
        <th>User Mode</th>
        <th>Kernel Mode</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Limited access</td>
        <td>Full system control</td>
      </tr>
      <tr>
        <td>Safe to run</td>
        <td>Can crash the system</td>
      </tr>
      <tr>
        <td>Crashes don’t affect Windows</td>
        <td>Crashes cause BSOD</td>
      </tr>
      <tr>
        <td>Uses <code>CreateFile</code></td>
        <td>Uses <code>NtCreateFile</code></td>
      </tr>
    </tbody>
  </table>

  <h2>API Layers</h2>
  <h3>Win32 API (Top Layer)</h3>
  <ul>
    <li>Easy to use</li>
    <li>Functions like <code>CreateFile</code>, <code>OpenProcess</code></li>
    <li>Located in <code>kernel32.dll</code></li>
  </ul>

  <h3>NT API (Deeper Layer)</h3>
  <ul>
    <li>Low-level functions like <code>NtOpenProcess</code></li>
    <li>Located in <code>ntdll.dll</code></li>
  </ul>

  <h3>Syscalls (Core Layer)</h3>
  <ul>
    <li>Deepest access point</li>
    <li>Used in assembly/shellcode</li>
    <li>Very stealthy and hard to detect</li>
  </ul>

  <h2>Nt, Zw, and Kernel Prefixes</h2>
  <table>
    <thead>
      <tr>
        <th>Prefix</th>
        <th>Kernel Component</th>
        <th>Example Function</th>
        <th>Purpose</th>
      </tr>
    </thead>
    <tbody>
      <tr><td>Cm</td><td>Configuration Manager</td><td>CmRegisterCallbackEx</td><td>Registry interaction</td></tr>
      <tr><td>Ex</td><td>Executive Layer</td><td>ExAllocatePool</td><td>Memory allocation, helpers</td></tr>
      <tr><td>Io</td><td>I/O Manager</td><td>IoAllocateIrp</td><td>Device I/O operations</td></tr>
      <tr><td>Ke</td><td>Kernel Core</td><td>KeSetEvent</td><td>Thread scheduling, events</td></tr>
      <tr><td>Mm</td><td>Memory Manager</td><td>MmUnlockPages</td><td>Virtual memory control</td></tr>
      <tr><td>Ob</td><td>Object Manager</td><td>ObReferenceObject</td><td>Handle objects like files</td></tr>
      <tr><td>Nt</td><td>Native API (user)</td><td>NtCreateFile</td><td>Used by apps from user mode</td></tr>
      <tr><td>Zw</td><td>Native API (kernel)</td><td>ZwCreateFile</td><td>Used internally by Windows</td></tr>
    </tbody>
  </table>

  <h2>Nt vs Zw Differences</h2>
  <table>
    <thead>
      <tr>
        <th>Nt Functions</th>
        <th>Zw Functions</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Used by user-mode applications</td>
        <td>Used by Windows kernel internally</td>
      </tr>
      <tr>
        <td>Go through access/security checks</td>
        <td>May skip those checks</td>
      </tr>
      <tr>
        <td>Returns raw NTSTATUS codes</td>
        <td>May wrap return values</td>
      </tr>
    </tbody>
  </table>

  <h2>Important DLLs to Know</h2>
  <table>
    <thead>
      <tr>
        <th>DLL Name</th>
        <th>Role</th>
      </tr>
    </thead>
    <tbody>
      <tr><td>kernel32.dll</td><td>High-level API: files, memory, threads</td></tr>
      <tr><td>ntdll.dll</td><td>NT API and syscalls</td></tr>
      <tr><td>user32.dll</td><td>Windows, input, GUI</td></tr>
      <tr><td>advapi32.dll</td><td>Security, services, registry</td></tr>
      <tr><td>gdi32.dll</td><td>Graphics, fonts, drawing</td></tr>
    </tbody>
  </table>

  <h2>Why Red Teams Care</h2>
  <p>
    Security tools like EDRs often watch <code>ntdll.dll</code> to catch threats. To avoid being noticed, red teamers (ethical hackers) use:
  </p>
  <ul>
    <li>Direct syscalls</li>
    <li>Manual syscall stubs</li>
    <li>API unhooking or remapping</li>
  </ul>

</body>
</html>
