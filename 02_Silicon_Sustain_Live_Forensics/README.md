# 🍏 Live Imaging Guide: Apple Silicon (M1/M2) without Admin Password

This guide describes the forensic acquisition process using **SUMURI RECON ITR** on an unlocked macOS system where the administrator password is unknown.

---

## 🛑 Phase 1: Immediate Session Preservation
The absolute priority is to prevent the Mac from sleeping or locking, as you cannot log back in without the password.

1.  **Open Terminal** and execute the prevention command:
    * `caffeinate -d`
2.  **Reference:** See `dziewiec.jpg` where the terminal is active alongside the imager.
3.  **Keep the Terminal window visible** to ensure the process hasn't been terminated.

---

## 🛠️ Phase 2: RECON ITR Initialization
1.  **Connect** your RECON ITR 1TB drive to the target Mac.
2.  **Launch** the application and select **"New Case"** from the main dashboard.
    * *Reference:* `piec.jpg` (Main Dashboard).
3.  **Enter** case details and investigator information.
    * *Reference:* `jeden.jpg` / `dwa.jpg` (Case Examiner Space).

---

## 🔍 Phase 3: Target Identification & Triage
Before imaging, you must identify the correct partitions.

1.  **Open Disk Manager** to view the APFS structure.
    * *Reference:* `trzy.jpg`.
2.  **Target:** Focus on `disk3s1` (**Macintosh HD - Data**), which contains the actual user files.
3.  **Use the File System browser** to verify user directories (e.g., `/Users/kamil_g`).
    * *Reference:* `szesc.jpg`.

---

## 💾 Phase 4: Logical Imaging Process
Since the disk is encrypted (FileVault) and we lack the password for offline decryption, we must perform a **Logical Image** while the session is live and the data is mounted.

### Configure Image Settings:
* **Source:** `disk3s1` (Macintosh HD - Data).
* **Image Type:** `Logical (Folder)` or `Logical (Sparse Image)`.
* **Destination:** Select your external RECON partition (e.g., RECON Imager Data).
    * *Reference:* `cztery.jpg` (Configuration screen).

### Select Data for "Imaging Bucket":
* Add the entire user home directory to the bucket.
    * *Reference:* `osiem.png` (Showing `/Users/kamil_g` added to the path list).

### Final Verification:
1.  Ensure **Source Hash** is checked for integrity.
2.  Set the **Image Name** (e.g., `kopia_test_Ciesielski`).
    * *Reference:* `siedem.png` / `dziewiec.jpg`.
3.  **Execute:** Click **Start** to begin the acquisition.

---

## ⚠️ Critical DFIR Notes
* **Artifact Note:** Running `caffeinate` is an intentional examiner action that modifies the Unified Log. It must be documented in the final report.
* **Power:** Ensure the Mac is plugged into a power adapter. If the battery dies, the session is lost forever.
* **Lid:** Never close the laptop lid during the process.

