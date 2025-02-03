<h2 align=center>Process Management</h2>
<br>

**Introduction**:  
In Linux, a process is an instance of a running program. Each process has a unique Process ID (PID) and can be in various states such as running, sleeping, or stopped.

**Key Concepts**:  
- **PID**: Unique identifier for each process.
- **Parent Process**: The process that creates another process.
- **Child Process**: The process created by another process.

**Basic Commands**:  
- `ps`: Displays information about active processes.
  ```bash
  $ ps
    PID TTY          TIME CMD
   1234 pts/0    00:00:00 bash
   5678 pts/0    00:00:00 ps
  ```
- `top`: Provides a dynamic, real-time view of running processes.
  ```bash
  $ top
  top - 11:00:00 up  1:23,  2 users,  load average: 0.00, 0.01, 0.05
  Tasks:  85 total,   1 running,  84 sleeping,   0 stopped,   0 zombie
  %Cpu(s):  0.3 us,  0.1 sy,  0.0 ni, 99.6 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
  KiB Mem :  2048000 total,  1024000 free,   512000 used,   512000 buff/cache
  KiB Swap:  1024000 total,  1024000 free,        0 used.  1536000 avail Mem

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
   1234 user      20   0  123456  12345   6789 S   0.3  0.6   0:00.01 bash
   5678 user      20   0  123456  12345   6789 R   0.3  0.6   0:00.01 top
  ```
- `htop`: An enhanced version of `top` with more features.
  ```bash
  $ htop
  ```

**Practice: Processes**

**Objective**:  
Understand and identify processes running on your system.

**Tasks**:  
1. Open a terminal.
2. Run the `ps` command to list current processes.
3. Use `top` or `htop` to monitor processes in real-time.

**Controlling Jobs**

**Introduction**:  
Jobs are processes that are started by the shell. You can control jobs by running them in the foreground or background.

**Key Concepts**:  
- **Foreground Job**: A job that takes control of the terminal until it finishes.
- **Background Job**: A job that runs without taking control of the terminal.

**Basic Commands**:  
- `&`: Run a command in the background.
  ```bash
  $ sleep 60 &
  [1] 1234
  ```
- `jobs`: List all jobs.
  ```bash
  $ jobs
  [1]+  Running                 sleep 60 &
  ```
- `fg`: Bring a background job to the foreground.
  ```bash
  $ fg %1
  sleep 60
  ```
- `bg`: Resume a suspended job in the background.
  ```bash
  $ bg %1
  [1]+ sleep 60 &
  ```

**Practice: Background and Foreground Processes**

**Objective**:  
Learn to manage jobs by running them in the background and foreground.

**Tasks**:  
1. Start a long-running process in the background using `&`.
2. Use the `jobs` command to list all jobs.
3. Bring a background job to the foreground using `fg`.

**Killing Processes**

**Introduction**:  
Sometimes, processes may become unresponsive or need to be terminated. Killing a process stops it from running.

**Key Concepts**:  
- **Signal**: A message sent to a process to trigger a specific behavior.
- **SIGKILL**: A signal to forcefully terminate a process.

**Basic Commands**:  
- `kill <PID>`: Send a signal to a process.
  ```bash
  $ kill 1234
  ```
- `killall <process_name>`: Kill all processes with the specified name.
  ```bash
  $ killall sleep
  ```
- `pkill <pattern>`: Kill processes matching a pattern.
  ```bash
  $ pkill sleep
  ```

**Practice: Killing Processes**

**Objective**:  
Learn to terminate unresponsive or unnecessary processes.

**Tasks**:  
1. Identify the PID of a process using `ps` or `top`.
2. Use the `kill` command to terminate the process.
3. Verify the process has been terminated using `ps` or `top`.

**Monitoring Process Activity**

**Introduction**:  
Monitoring process activity helps you understand system performance and resource usage.

**Key Concepts**:  
- **CPU Usage**: The amount of CPU time used by a process.
- **Memory Usage**: The amount of memory used by a process.

**Basic Commands**:  
- `top`: Monitor system processes and resource usage.
  ```bash
  $ top
  ```
- `htop`: An enhanced version of `top` with more features.
  ```bash
  $ htop
  ```
- `vmstat`: Report virtual memory statistics.
  ```bash
  $ vmstat
  procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
   r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
   1  0      0 1024000  512000  512000    0    0     0     0  100  200  0  0 100  0  0
  ```

**Practice: Monitoring Process Activity**

**Objective**:  
Learn to monitor and analyze process activity on your system.

**Tasks**:  
1. Use `top` or `htop` to monitor processes.
2. Analyze CPU and memory usage of processes.
3. Use `vmstat` to report virtual memory statistics.

**Lab: Monitoring and Managing Linux Processes**

**Objective**:  
Apply your knowledge to monitor and manage processes on a Linux system.

**Tasks**:  
1. Open a terminal and list all running processes using `ps`.
2. Start a long-running process in the background and monitor it using `top`.
3. Terminate an unresponsive process using `kill`.
4. Use `htop` to analyze system performance and resource usage.
