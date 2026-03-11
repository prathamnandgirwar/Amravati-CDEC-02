# DAY 17 - Managing Processes and Optimizing Performance

## Understanding Process Priority and Nice Values

Process priority determines the importance of a process relative to others in the system.  
In Linux, the **nice value** is used to influence process scheduling by assigning a priority level.

When multiple processes are running, **process priority decides which process gets CPU first**.

### Key Points

#### Nice Values
- Range: **-20 (highest priority)** to **19 (lowest priority)**
- Default value: **0**
- Negative nice values require **root privileges**

#### Command to Check Priority
Use the following commands to view running processes and their priorities:

```bash
top
```

or

```bash
htop
```

#### Changing Nice Values

Start a process with a specific nice value:

```bash
nice -n 10 sleep 1000
```

Change the nice value of an existing process:

```bash
renice <nice_value> -p <PID>
```

---

# Finding Process IDs

Each running process in Linux is assigned a **unique Process ID (PID)**.

### Commands

List all processes:

```bash
ps -e
```

Find a specific process:

```bash
pgrep <process_name>
```

Detailed process information:

```bash
ps -aux | grep <process_name>
```

---

# Sending Signals to Processes

Linux allows sending **signals** to control or terminate processes.

### Common Signals

| Signal | Number | Description |
|------|------|-------------|
| SIGTERM | 15 | Graceful termination |
| SIGKILL | 9 | Forceful termination |

### Commands

Send a signal:

```bash
kill -<signal_number> <PID>
```

Example:

```bash
kill -9 1234
```

This **forcefully terminates** the process with PID `1234`.

---

# Practical Example: Adjusting Priority of Long-Running Processes

### 1. Start a Process with Nice Value

```bash
nice -n 10 sleep 1000
```

This starts a `sleep` process with a **nice value of 10**.

---

### 2. Change Priority of an Existing Process

```bash
renice 15 -p <PID>
```

This changes the nice value of the process.

---

### 3. Monitor the Changes

```bash
top
```

Observe the updated priority in the **PR** and **NI** columns.

You can also check using:

```bash
ps -o pid,ni,pri,cmd -p <PID>
```

---

# Overview of Process States

Processes in Linux can exist in different states.

### Common Process States

| State | Meaning |
|------|--------|
| R | Running or runnable |
| S | Sleeping (waiting for an event) |
| D | Uninterruptible sleep (waiting for I/O) |
| Z | Zombie (terminated but not cleaned up) |
| T | Stopped or traced |

### View Process States

```bash
ps -e -o pid,stat,cmd
```

---

# Different Job Types and States

Jobs represent **processes managed by the shell**.

### Commands

List jobs:

```bash
jobs
```

Move job to foreground:

```bash
fg <job_id>
```

Move job to background:

```bash
bg <job_id>
```

Stop a job:

```bash
kill -TSTP <PID>
```

---

# Visualizing the Process Tree

Understanding **parent-child relationships** among processes helps analyze system behavior.

### Command

```bash
pstree
```

Displays processes in a **tree structure**.

Example with PIDs:

```bash
pstree -p
```

This shows **processes along with their PIDs**.
