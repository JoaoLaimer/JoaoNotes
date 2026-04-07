The Task Manager is a built-in GUI-based [[Windows]] utility that allows users to see what is running on the Windows system. It also provides information on resource usage, such as how much each process utilizes CPU and memory. When a program is not responding, Task Manager is used to end (kill) the process.
Task Managers doesn't show a Parent-Child process view. That is where other utilities, such as **[[Process Hacker]]** and **[[Process Explorer]]**, come to the rescue.

**System**
The official definition from Windows Internals 6th Edition:

"_The System process (process ID 4) is the home for a special kind of thread that runs only in kernel mode a kernel-mode system thread. System threads have all the attributes and contexts of regular user-mode threads (such as a hardware context, priority, and so on) but are different in that they run only in kernel-mode executing code loaded in system space, whether that is in Ntoskrnl.exe or in any other loaded device driver. In addition, system threads don't have a user process address space and hence must allocate any dynamic storage from operating system memory heaps, such as a paged or nonpaged pool._"

It's normal behaviour is as follow:
**Image Path**:  N/A
**Parent Process**:  None
**Number of Instances**:  One
**User Account**:  Local System
**Start Time**:  At boot time

Using Process Hacker:
  **Image Path**: C:\Windows\system32\ntoskrnl.exe (NT OS Kernel)
**Parent Process**: System Idle Process (0)

**System > smss.exe**
smss.exe (Session Manager Subsystem), aka. Windows Session Manager, is responsible for creating new session. It is the first user-mode process started by the kernel. This process starts the kernel and user mode. This subsystem includes win32k.sys (kernel mode), winsrv.dll (user mode), and csrss.exe (user mode). Any other subsystem listed in the Required value of `HKLM\System\CurrentControlSet\Control\Session Manager\Subsystems` is also launched. SMSS is also responsible for creating environment variables,virtual memory paging files and starts winlogon.exe.
Smss.ee start csrss.exe and wininit.exe in Session 0, an isolated Windows session for the operating system, and csrss.exe and winlogon.exe for Session 1, which is the user sesssion.
It's normal behaviour is as follow:
**Image Path**:  %SystemRoot%\System32\smss.exe
**Parent Process**:  System
**Number of Instances**:  One master instance and child instance per session. The child instance exits after creating the session.
**User Account**:  Local System
**Start Time**:  Within seconds of boot time for the master instance

What is unusual?
Different parent and image path, more than one process, running user is not SYSTEM, unexpected registry entries for Subsystem.

**crss.exe**
Client Server Runtime Process, is the user-mode side of the Windows Subsystem. This process is responsible for the Win32 console windows and process thread creating and deletion. For each instance, csrsrv.dll, basesrv.dll, and winsrv.dll are loaded (along with others).
This process is also responsible for making the Windows API available to other processes, mapping drive letters, and handling the Windows shutdown process.
What is normal?
**Image Path**:  %SystemRoot%\System32\smss.exe
**Parent Process**:  System
**Number of Instances**:  One master instance and child instance per session. The child instance exits after creating the session.
**User Account**:  Local System
**Start Time**:  Within seconds of boot time for the master instance.

What is unusual?
An actual parent process (smss.exe calls this process and self-terminates).

**Wininit.exe**
The Windows Iniitialization Process is responsible for launching services.exe (Service Control Manager), lsass.exe (Local Security Authority), and lsaiso.exe within Session 0.
lsaiso.exe is a process associated with Credential Guard and KeyGuard. You will only see this process if Credential Guard is enabled.
What is normal?
**Image Path**:  %SystemRoot%\System32\wininit.exe
**Parent Process**:  Created by an instance of smss.exe
**Number of Instances**:  One
**User Account**:  Local System
**Start Time**:  Within seconds of boot time

What is unusual?
An actual parent process, other image file path than C:\Windows\System32, subtle misspellings to hide rogue processes in plain sight,multiple running instances, not running as SYSTEM.

**wininit.exe > services.exe**

Service Control Manager (SCM) is responsible for handling system services: loading services, interacting with services and starting or ending services. It mantains a database that can be queried using `sc.exe`

Information regarding services is stored in the registry, `HKLM\System\CurrentControlSet\Services`
This process also loads device drivers marked as auto-start iinto memory.
When a user logs into a machine, this process is responsble for setting the value of the Last Known Good control set, `HKLM\System\Select\LastKnownGood`.
This process is parent to several other key processes: svchost.exe, spoolsv.exe, msmpeng.exe, and dllhost.exe, to name a few.

What is normal?
**Image Path**:  %SystemRoot%\System32\services.exe
**Parent Process**:  wininit.exe
**Number of Instances**:  One
**User Account**:  Local System
**Start Time**:  Within seconds of boot time

What is unusual?
A parent process other than wininit.exe

**wininit.exe > services.exe > svchost.exe**

Service Host is responsable for hosting and managing Windows services.
The services running in this process are implemented as DLLs. The DLL to implement is stored in the registry for the service under the Paramters subkey in ServiceDLL. The full path is `HKLM\SYSTEM\CurrentControlSet\Services\SERVICENAME\Parameters`

What is normal?
**Image Path**: %SystemRoot%\System32\svchost.exe
**Parent Process**: services.exe
**Number of Instances**: Many
**User Account**: Varies (SYSTEM, Network Service, Local Service) depending on the svchost.exe instance. In Windows 10, some instances run as the logged-in user.
**Start Time**: Typically within seconds of boot time. Other instances of svchost.exe can be started after boot.

What is unusual?
A parent process other than services.exe and the absence of the -k parameter in the Binary path of the service.

**lsass.exe**

Local Security Authority Subsystem Service is responsible for enforcing the security policy on the system. It verifies users logging on to a Windows computer or server, handles password changes, and creates access tokens. It also writes to the Windows Security Log.
Common tools such as mimikatz mimic this process to hide in plain sight.
What is normal?
**Image Path**:  %SystemRoot%\System32\lsass.exe
**Parent Process**:  wininit.exe
**Number of Instances**:  One
**User Account**:  Local System
**Start Time**:  Within seconds of boot time
What is unusual?
A parent other than wininit.exe, not running as SYSTEM, multiple running instances.

**winlogon.exe**
The WIndows Logon is responsible for handling the Secure Attention Sequence (SAS), loading the user profile. It loads the user's NTUSER.DAT into HKCU, and usernint.exe loads the user's shell.

What is normal?
**Image Path**:  %SystemRoot%\System32\winlogon.exe
**Parent Process**:  Created by an instance of smss.exe that exits, so analysis tools usually do not provide the parent process name.
**Number of Instances**:  One or more
**User Account**:  Local System
**Start Time**:  Within seconds of boot time for the first instance (for Session 1). Additional instances occur as new sessions are created, typically through Remote Desktop or Fast User Switching logons.

What is unusual?
An actual parent process, Shell value in the registry other than explorer.exe

**explorer.exe**
Windows Explorer is the process that gives the user access to their folders and files.
The WInlogon process runs userinit.exe, which launches the value in `HKLM\Software\Microsoft\Windows NT\CurrentVersion\Shell`. Userinit.exe exits after spawning explorer.exe.
There will be many child processes for explorer.exe

What is normal?
**Image Path**:  %SystemRoot%\explorer.exe
**Parent Process**:  Created by userinit.exe and exits
**Number of Instances**:  One or more per interactively logged-in user
**User Account**:  Logged-in user(s)
**Start Tim**e:  First instance when the first interactive user logon session begins

What is unusual?
Parent process, outbound TCP/IP connections, running as an unknown user.
