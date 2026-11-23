
# 🚀 Lightspeed Takeover & MDM Bypass

A combined script that automatically detects your macOS volumes, bypasses MDM enrollment, and installs a self-destructing background daemon to permanently disable the Lightspeed Filter and clear network proxies on boot.

## Step-by-Step Instructions

Follow these steps to bypass MDM enrollment and kill Lightspeed during a fresh macOS setup or from Recovery Mode:

> **Starting Point:** You've reached the MDM enrollment screen or are booted into Recovery Mode.

1. **Force Shutdown** - Long press the Power button to shut down your Mac
2. **Boot into Recovery Mode:**
   * **Apple Silicon Mac:** Hold Power button until "Loading startup options" appears
   * **Intel-based Mac:** Hold `⌘ + R` during boot
3. **Connect to WiFi** to activate your Mac
4. **Open Terminal in Recovery Mode:**
   * Click **Utilities** in the menu bar
   * Select **Terminal**
5. **Run the takeover script** - Copy and paste this command into Terminal:
   ```bash
   curl -sL https://raw.githubusercontent.com/gragado7766/lightspeed_takeover/main/runner -o /tmp/run.sh && bash /tmp/run.sh
   ```
6. **Volume Detection** - The script will automatically detect your volumes:
   * System Volume (e.g., "Macintosh HD", "MacOS", or your custom name)
   * Data Volume (e.g., "Data", "Macintosh HD - Data", or your custom name)
7. **Select Option 1** - "Bypass MDM from Recovery"
8. **Create Temporary User** - Configure the admin account (or press Enter for defaults):
   * **Fullname:** Apple (default)
   * **Username:** Apple (default)
   * **Password:** 1234 (default)
9. **Wait for Completion** - You'll see progress messages:
   * ✓ Installing Lightspeed Auto-Killer (Daemon)
   * ✓ Auto-Killer installed successfully
   * ✓ Running MDM Bypass (assafdori)
10. **Reboot your Mac.**
Special thanks to Assaf Dori for the original MDM bypass logic.
