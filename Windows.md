# 📝 Guide: Restore Classic Context Menu (Windows 10 Style) on Windows 11

## ✅ Goal

Always display the **classic context menu** (the full menu with "Open with", "Send to", etc.) when right-clicking files or folders in **Windows 11**, without needing to click **"Show more options"** every time.

---

## 🛠️ How it works

We add a **Registry key (regedit)** to disable the Windows 11 context menu and force the system to show the **classic menu directly** (same as in Windows 10).

This tweak uses a Windows-recognized “shortcut” to **clear the default context menu handler**, reverting to the older behavior.

---

## 🧪 Step-by-Step Procedure

### 1. Open Registry Editor

- Press `Win + R`
- Type `regedit` → press **Enter**

### 2. Navigate to this key

```text
HKEY_CURRENT_USER\Software\Classes\CLSID
```

### 3. Create a new key

- Right-click on `CLSID` → **New > Key**
- Name it exactly:

```text
{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}
```

### 4. Create a subkey

- Right-click on this new key → **New > Key**
- Name it:

```text
InprocServer32
```

### 5. Set the default value to empty

- Select `InprocServer32`
- On the right, double-click **(Default)**
- **Leave it blank**, do not enter anything → click **OK**

### 6. Restart your computer

---

## ✅ Result

Now every right-click will open the **classic context menu directly**, without needing to select “Show more options”.

---

## 🔄 How to revert (restore modern menu)

1. Open `regedit` again

2. Navigate to:

   ```text
   HKEY_CURRENT_USER\Software\Classes\CLSID
   ```

3. Delete the key:

   ```text
   {86ca1aa0-34aa-4e8b-a509-50c905bae2a2}
   ```

4. Restart your computer
