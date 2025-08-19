# Running Tasks in the Background on Cloud-Based Linux Machines

When working with cloud Linux servers that only provide a single terminal interface, knowing how to run tasks in the background can be a **life-saver**. These steps ensure that long-running processes continue without requiring an active terminal session.

---

## What is `nohup`?

The [`nohup`](https://en.wikipedia.org/wiki/Nohup) command in Linux and Unix-like systems stands for **“no hang up.”** It allows a command to run in a way that ignores the **SIGHUP (hangup) signal**, which is normally sent when a terminal session is closed. Without `nohup`, such processes would terminate when you log out or close the terminal.

Using `nohup`:

* Detaches the process from the terminal.
* Ensures it keeps running in the background even after logging out.
* Is ideal for **long-running tasks** such as data processing, backups, or system maintenance.

By default:

* Output (stdout and stderr) is redirected to a file named `nohup.out` in the current directory.
* If you don’t have write permissions, it defaults to your home directory.
* You can specify a custom log file, e.g.,

  ```bash
  nohup command > custom.log &
  ```

 **Note:** `nohup` is not a replacement for terminal multiplexers like `screen` or `tmux`. Those allow you to reattach and interact with a session later. `nohup` is best for tasks that **don’t require user interaction** after starting.

---

## Example: Running a Python Script in the Background

Suppose you have a Python script that processes a large dataset and may take hours to finish. You can run it in the background using `nohup`:

```bash
nohup python -u some_sciprt.py > output.log 2>&1 &
```

Explanation:

* `-u` → runs Python in **unbuffered mode**, so log output appears immediately in the file.
* `output.log` → the file where all output (including errors) will be written.
* `&` → sends the process to the **background** so your terminal is free.

To **view the logs in real-time**, use:

```bash
tail -f output.log
```

This will continuously display new log entries as the script runs.

---

That’s all you need to run long Python scripts (or any commands) in the background on Linux without keeping the terminal open.
