
![Screenshot_06-May_04-13-24_4866](https://github.com/user-attachments/assets/1e6b9143-1aab-4006-b032-4c3bba667a21)

---

### ⚙️ **Step-by-Step Configuration Process from `windows configuration.docx`**

---

### Step 1: Clone Windots Repository

**Command:**

```powershell
git clone https://github.com/RohitRai1141/MyWindowsConfig.git
```

✅ No error encountered.

---

### Step 2: Navigate into Windots directory

**Command:**

```powershell
cd windots
```

✅ No error encountered.

---

### Step 3: Run setup script

**Command:**

```powershell
.\setup.ps1
```

❌ **Error:**

```powershell
.\setup.ps1 : File C:\Users\[user]\windots\setup.ps1 cannot be loaded because running scripts is disabled on this system.
```

### 👉 Go to Step 4 to fix the error.

---

### Step 4: Enable Script Execution

**Command:**

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

✅ Fixes script execution issue.

---

### Step 5: Re-run the setup script

**Command:**

```powershell
.\setup.ps1
```

❌ **Error:**

```powershell
No match was found for the specified search criteria and module name 'WinGet'. Try Get-PSRepository to see all available registered module repositories.
```

### 👉 Go to Step 6 to fix the error.

---

### Step 6: Enable TLS 1.2 to fix WinGet/PowerShell errors

**Command:**

```powershell
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
```

✅ Fixes the TLS error that blocks module installation.

---

### Step 7: Re-run the setup again

**Command:**

```powershell
.\setup.ps1
```

✅ This time it proceeds without error and begins installing dependencies and symlinking config files.

---

### Step 8: Restart the machine

✅ Restarted as required after the configuration completed.

---

### Step 9: Open GlazeWM and check terminal layout

**Command:**

```powershell
winfetch
```

❌ **Error:**

```powershell
winfetch : The term 'winfetch' is not recognized as the name of a cmdlet...
```

### 👉 Go to Step 10 to fix winfetch not found issue.

---

### Step 10: Install Winfetch manually

**Command:**

```powershell
winget install Winfetch
```

✅ Winfetch installed manually after the setup script failed to handle it.

---

### Step 11: Re-run winfetch

**Command:**

```powershell
winfetch
```

✅ Output now shows correctly with system information.

---

### Step 12: Configure fonts manually (due to missing automatic install)

**Steps:**

1. Download font from [Nerd Fonts](https://www.nerdfonts.com/)
2. Install fonts manually by double-clicking or dragging into Fonts settings
3. Apply the font in Windows Terminal settings → Profiles → Defaults → Appearance → Font Face

✅ Font now renders correctly in terminal with proper symbols.

---

### Step 13: Fix `config.yaml` path in GlazeWM if not loading

**Steps:**

1. Go to `C:\Users\[username]\AppData\Roaming\glazewm\config.yaml`
2. Confirm it's symlinked to `windots/config/glazewm/config.yaml`
3. If broken:

```powershell
New-Item -ItemType SymbolicLink -Path "C:\Users\[username]\AppData\Roaming\glazewm\config.yaml" -Target "C:\Users\[username]\windots\config\glazewm\config.yaml"
```

✅ GlazeWM loads the correct config now.

---

### Step 14: Check PowerToys is installed

❌ **Observation:** PowerToys was not installed automatically.

### 👉 Go to Step 15 to install manually.

---

### Step 15: Install PowerToys

**Command:**

```powershell
winget install Microsoft.PowerToys
```

✅ PowerToys installed successfully.

---

### Step 16: Launch PowerToys and enable FancyZones

1. Open PowerToys → FancyZones → Turn on
2. Set up layout as per preference

✅ FancyZones active and working.

---

### Step 17: Optional – Add PowerToys to Startup (if not auto-starting)

**Command:**

```powershell
shell:startup
```

Drag a shortcut of PowerToys into that folder.

✅ PowerToys now launches on startup.

---
