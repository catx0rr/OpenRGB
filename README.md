### OpenRGB Installation

---

This is to setup Open RGB on my setup (ASUSTUF-PC) which runs on multiple hardware manufacturers. This will 'sync' all ARGB headers from the mother board to the mouse, keyboard and other peripherals that runs with ARGB. It will only use the default profile, which is (LED White). You need to select other profiles to change it.

---

Photo Samples:

<p float="left">
  <img src="https://github.com/catx0rr/OpenRGB/blob/master/images/default.jpg" width="150" />
  <img src="https://github.com/catx0rr/OpenRGB/blob/master/images/hacker_lite.jpg" width="150" /> 
  <img src="https://github.com/catx0rr/OpenRGB/blob/master/images/chroma_oak.jpg" width="150" />
  <img src="https://github.com/catx0rr/OpenRGB/blob/master/images/chroma_pastel.jpg" width="150" />
  <img src="https://github.com/catx0rr/OpenRGB/blob/master/images/rosy.jpg" width="150" />
</p>

---

### Installation

1. Clone this repository:

```sh
git clone https://github.com/catx0rr/OpenRGB
```

or 

```powershell
wget 
```

2. Copy the appdata files to %appdata%\OpenRGB

```cmd
xcopy /E .\appdata %appdata%
```

3. Copy the OpenRGB file to C:\Program Files

```cmd
xcopy /E .\OpenRGB "C:\Program Files"
```

4. Create a Scheduled Task:

```cmd
taskschd.msc
```

![task scheduler](https://github.com/catx0rr/OpenRGB/blob/master/images/task.png)

OpenRGB
```
  General:
    - Run only when user is logged on
    - Run with highest privileges
  Triggers:
    - Begin the task: At log on
    - Specific user: <PC>\<user>
    - Stop task if it runs longer than: 3 days
    - Enabled
  Actions:
    - Start a program
    - Program/script: "C:\Program Files\OpenRGB\OpenRGB.exe"
    - Add arguments: --gui --startminimized --server --profile Default.orp
  Settings:
    - Allow task to be run on demand
    - If the task fails, restart every: 1 minute
    - Attempt to restart: 3 times
    - Stop the task if it runs longer than: 3 days
    - If the running task does not end when requested, force it to stop
    - Do not start a new instance
```

OpenRGB Lock State
```
  General:
    - Run only when user is logged on
    - Run with highest privileges
  Triggers:
    - Begin the task: On workstation lock
    - Specific user: <PC>\<user>
    - Enabled
  Actions:
    - Start a program
    - Program/script: C:\Windows\System32\cmd.exe
    - Add arguments: /c "taskkill /IM OpenRGB.exe /F"
  Settings:
    - Allow task to be run on demand
    - If the task fails, restart every: 1 minute
    - Attempt to restart: 3 times
    - Stop the task if it runs longer than: 3 days
    - If the running task does not end when requested, force it to stop
    - Do not start a new instance
```

OpenRGB Unlock State
```
  General:
    - Run only when user is logged on
    - Run with highest privileges
  Triggers:
    - Begin the task: On workstation unlock
    - Specific user: <PC>\<user>
    - Enabled
  Actions:
    - Start a program
    - Program/script: "C:\Program Files\OpenRGB\OpenRGB.exe"
    - Add arguments: --gui --startminimized --server --profile Default.orp
  Settings:
    - Allow task to be run on demand
    - If the task fails, restart every: 1 minute
    - Attempt to restart: 3 times
    - Stop the task if it runs longer than: 3 days
    - If the running task does not end when requested, force it to stop
    - Do not start a new instance
```


5. Done!
