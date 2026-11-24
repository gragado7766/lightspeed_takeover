# 🚀 Lightspeed Takeover & MDM Bypass

A combined script that automatically detects your macOS volumes, bypasses MDM enrollment, and installs a self-destructing background daemon to permanently disable the Lightspeed Filter and clear network proxies on boot.

> **Credit:** The MDM enrollment bypass portion of this script is entirely powered by the excellent open-source work of **[Assaf Dori](https://github.com/assafdori/bypass-mdm)**.
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
Select Your Option:

1 - Stop and Exit

2 - Bypass MDM + Kill Lightspeed

3 - Bypass MDM + Kill Lightspeed + Remove iPhone Mirroring Block

4 - Bypass MDM + Kill Lightspeed + Custom Profile Remover (Advanced User Caution)

5 - Erasure (Nuclear Option - removes all profiles)

Volume Detection - The script will automatically detect your volumes:

System Volume (e.g., "Macintosh HD", "MacOS", or your custom name)

Data Volume (e.g., "Data", "Macintosh HD - Data", or your custom name)

Select Option 1 - "Bypass MDM from Recovery" (for the Assafdori script)

Create Temporary User - Configure the admin account (or press Enter for defaults):

Fullname: Apple (default)

Username: Apple (default)

Password: 1234 (default)

Wait for Completion - You'll see progress messages:

✓ Installing Lightspeed Auto-Killer (Daemon)

✓ Auto-Killer installed successfully

✓ Running MDM Bypass (assafdori)

Reboot your Mac.

🤖 How the Auto-Killer Works
Once you reboot and log into the new admin account, a hidden background service waits 20 seconds and then executes the following:

Kills all active lsfilter and mobilefilter processes.

Disables the Lightspeed LaunchDaemons so they cannot restart.

Flushes the macOS proxy settings to restore internet access to Chrome, Steam, etc.

Self-Destructs: Deletes the daemon and script from the system so it only runs once.

🗑️ How the Custom Profile Remover Works (Option 4)
If you select Option 4, the script scans the MDM profile store and prints a numbered list of all installed management profiles. You can enter the numbers of the profiles you want to delete, separated by commas (e.g., 1,3), to surgically remove specific restrictions without breaking your Wi-Fi settings.

⚠️ Important Notes
The script works even with System Integrity Protection (SIP) enabled.

Option 3 specifically targets the MDM profile UUID for the iPhone Mirroring Block, leaving your Wi-Fi and other school settings intact.

Option 5 will completely wipe all management profiles from the system.

If your school's MDM pushes Lightspeed back to the Mac in the future, you will need to run the manual pkill commands again, as the self-destructing daemon will be gone.

Special thanks to Assaf Dori for the original MDM bypass logic.
