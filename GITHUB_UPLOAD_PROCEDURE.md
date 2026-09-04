# How to Upload This Repository to GitHub

## Step 1: Create a GitHub Account (if you don't have one)
- Go to https://github.com
- Click "Sign up" and create an account

---

## Step 2: Create a New Repository on GitHub

1. Click the **"+"** icon (top right) → **"New repository"**
2. Fill in:
   - **Repository name:** `BGR_Project` (or `CMOS-Self-Biased-Bandgap-Reference`)
   - **Description:** `CMOS Self-Biased Bandgap Reference design using 180nm CMOS - NIE Mysuru VLSI Project`
   - **Visibility:** Public (so anyone can view)
   - ✅ Check **"Add a README file"** → NO (we already have one)
3. Click **"Create repository"**

---

## Step 3: Download and Install Git

Download from: https://git-scm.com/downloads
Install with default settings.

---

## Step 4: Extract the ZIP File

1. Find the downloaded `BGR_Project_Repository.zip`
2. Right-click → **Extract All**
3. Extract to a location like `C:\Users\YourName\BGR_Project_Repository\`

---

## Step 5: Take & Add Screenshots (IMPORTANT)

Before uploading, add your screenshots to the correct folders inside the extracted directory:

```
BGR_Project_Repository/
├── images/
│   ├── pdf1_final_report/      ← Screenshots from BGR_FINAL_REPORT.pdf
│   ├── pdf2_reference/         ← Screenshots from BGR.pdf
│   └── pdf3_workshop_notes/    ← Screenshots from BGR_VSD_Written_notes_workshop.pdf
```

See `docs/03_Screenshot_Upload_Guide.md` for the exact list of screenshots needed.

**How to take screenshots:**
- Open each PDF
- Go to the page listed
- Press `Win + Shift + S` (Windows) or `Cmd + Shift + 4` (Mac)
- Save with the filename specified

---

## Step 6: Upload via GitHub Website (Easiest Method)

### Option A: Drag and Drop (No Git needed)

1. Go to your new repository on GitHub
2. Click **"uploading an existing file"** link
3. Drag your entire `BGR_Project_Repository` folder contents into the browser
4. Scroll down → Add commit message: `"Initial commit: Complete BGR project repository"`
5. Click **"Commit changes"**

**Note:** GitHub allows up to 100 files at once. If you have more, upload in batches.

---

### Option B: Using Git Command Line (Recommended)

Open **Git Bash** (Windows) or **Terminal** (Mac/Linux):

```bash
# Navigate to your extracted folder
cd C:\Users\YourName\BGR_Project_Repository

# Initialize git
git init

# Add all files
git add .

# Create first commit
git commit -m "Initial commit: CMOS Self-Biased BGR complete project"

# Connect to your GitHub repository
# Replace YOUR-USERNAME and YOUR-REPO-NAME:
git remote add origin https://github.com/YOUR-USERNAME/BGR_Project.git

# Push to GitHub
git branch -M main
git push -u origin main
```

When prompted, enter your GitHub **username** and **password** (or Personal Access Token).

---

## Step 7: Add Screenshots After Initial Upload

After uploading the main files, add your screenshots:

```bash
# Copy screenshots to correct folders first, then:
git add images/
git commit -m "Add simulation screenshots from PDF documents"
git push
```

---

## Step 8: Verify Your Repository

1. Go to `https://github.com/YOUR-USERNAME/BGR_Project`
2. You should see:
   - `README.md` displayed automatically (the main documentation)
   - `docs/` folder with theory and implementation guides
   - `images/` folder with all screenshots
   - `simulation_results/` folder
   - `layout/` folder

---

## Step 9: Make It Look Professional (Optional)

### Add Repository Topics/Tags:
1. On your repo page, click the gear icon ⚙ next to "About"
2. Add topics: `vlsi`, `bandgap-reference`, `cmos`, `cadence-virtuoso`, `analog-design`, `180nm`, `BGR`
3. Click **Save changes**

### Pin the Repository:
1. Go to your GitHub profile
2. Click **"Customize your pins"**
3. Select this repository to pin it

---

## Repository Structure After Upload

```
BGR_Project/
├── README.md                          ← Main documentation (auto-displayed)
├── docs/
│   ├── 01_BGR_Theory.md               ← Complete mathematical theory
│   ├── 02_Design_Implementation.md    ← Cadence step-by-step guide
│   └── 03_Screenshot_Upload_Guide.md  ← Which screenshots to add
├── images/
│   ├── pdf1_final_report/             ← 15 screenshots from your report
│   ├── pdf2_reference/                ← 13 screenshots from IISc reference
│   └── pdf3_workshop_notes/           ← 24 screenshots from VSD workshop
├── simulation_results/
│   └── simulation_summary.md          ← All simulation results documented
└── layout/
    └── layout_verification.md         ← DRC/LVS/PEX documentation
```

---

## Sharing Your Repository

Once uploaded, share the link:
```
https://github.com/YOUR-USERNAME/BGR_Project
```

This can be added to:
- Your resume / LinkedIn profile
- Project report appendix
- Portfolio website
