# install.arch.io
openbox on the arch

### **Openbox: A Lightweight Window Manager for X11**  

**Openbox** is a highly customizable, lightweight **stacking window manager** for **X11**. It does **not** include a desktop environment (DE), making it ideal for **minimalist setups**.  

---

## **🔹 Why Use Openbox?**
✅ **Lightweight** – Uses minimal system resources.  
✅ **Fast & Simple** – No unnecessary bloat, just a clean window manager.  
✅ **Highly Customizable** – Configure everything via text files.  
✅ **Standalone or Hybrid** – Use it alone or integrate it with a DE (like XFCE, LXQt).  
✅ **Keyboard & Mouse Friendly** – Supports keybindings for power users.  

---

## **🔹 How Does Openbox Work?**
Unlike full desktop environments (KDE, GNOME, etc.), Openbox only **manages windows**:
- **No built-in panels or docks** (you add your own).
- **No desktop icons** (you use a tool like **pcmanfm** for this).
- **Uses config files** (`~/.config/openbox/rc.xml`) for keybindings, themes, etc.

---

## **🔹 Installing Openbox on Arch Linux**
1️⃣ **Install Openbox**  
```sh
sudo pacman -S openbox obconf obmenu
```

2️⃣ **Create a default configuration**  
```sh
mkdir -p ~/.config/openbox
cp -r /etc/xdg/openbox/* ~/.config/openbox/
```

3️⃣ **Start Openbox**  
- If using **startx**, edit `~/.xinitrc`:  
  ```sh
  exec openbox-session
  ```
  Then run:
  ```sh
  startx
  ```

- If using a **display manager (SDDM, LightDM, etc.)**, just select **Openbox** at login.

---

## **🔹 Customizing Openbox**
### **1. Configure Keybindings & Themes**
- **`rc.xml`** → Main config (themes, keybindings, behavior).
- **`menu.xml`** → Right-click menu customization.
- Use **`obconf`** (GUI tool) to tweak appearance.

### **2. Add a Panel & Launcher**
- **Polybar** (modern, minimal)
- **tint2** (lightweight, simple)
- **Plank** (macOS-like dock)

Example:
```sh
sudo pacman -S tint2
tint2 &
```

### **3. Set a Wallpaper**
```sh
sudo pacman -S feh
feh --bg-scale /path/to/image.jpg
```

---

## **🔹 Who Should Use Openbox?**
🚀 **Power users** who want a fast, minimal desktop.  
🛠️ **Developers** who prefer a clean, distraction-free workspace.  
💻 **Older hardware** users needing a lightweight system.  

---

### **🔹 Openbox vs. Other Window Managers**
| **WM**       | **Type**     | **Best For**          | **Resource Usage** | **Customization** |
|-------------|-------------|----------------------|------------------|------------------|
| **Openbox** | Stacking WM | Lightweight desktops | 🔋 Low | 🔥🔥🔥 |
| **i3**      | Tiling WM   | Keyboard-focused devs | 🔋 Ultra Low | 🔥🔥🔥🔥 |
| **Sway**    | Wayland WM  | Modern tiling WM users | 🔋 Low | 🔥🔥🔥 |
| **dwm**     | Tiling WM   | Hardcore minimalists | 🔋 Ultra Low | 🔥🔥🔥🔥🔥 |
