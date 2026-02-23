CSV MERGE SCRIPT
================

Overview
--------
This PowerShell script merges multiple CSV files from a specified folder into
a single combined CSV file. It assumes all CSV files share the same header
(row 1). The script writes the header once, then appends all data rows from
every file in the folder.

This is useful when:
- You receive multiple CSV exports from a system and need one master file
- You split data into multiple CSVs and want to recombine them
- You want to automate manual copy/paste merging
- You need a repeatable, reliable way to consolidate CSV data

--------------------------------------------------------------------------

How It Works
------------
1. The script looks inside the folder you specify.
2. It finds all files ending in ".csv".
3. It reads the header (first line) from the first CSV file.
4. It writes that header to the output CSV file.
5. It loops through every CSV file in the folder:
      - Skips the header row
      - Appends all remaining rows to the output file
6. The result is one combined CSV containing all data.

--------------------------------------------------------------------------

Script Parameters
-----------------
You can customize two parameters at the top of the script:

    $folderPath  - The folder containing the CSV files to merge
    $outputFile  - The full path and filename of the merged CSV output

Example:

    param (
        [string]$folderPath = "C:\Data\MonthlyReports",
        [string]$outputFile = "C:\Data\Merged\AllReports.csv"
    )

--------------------------------------------------------------------------

How To Use
----------
1. Save the script as:  Merge-CSVs.ps1
2. Edit the two parameter values at the top of the script:
       - Set the folder containing your CSVs
       - Set the output file path
3. Open PowerShell.
4. Navigate to the folder where the script is saved:
       cd "C:\Path\To\Script"
5. Run the script:
       .\Merge-CSVs.ps1
6. When complete, check the output file for the merged data.

--------------------------------------------------------------------------

Requirements
------------
- Windows PowerShell 5+ or PowerShell 7+
- CSV files must:
    - Have the same header row
    - Use standard text encoding (UTF-8 recommended)

--------------------------------------------------------------------------

Use Cases
---------
• **Monthly or weekly reports**
  Combine multiple exported CSVs into one master file for analysis.

• **Survey or form responses**
  Merge multiple batches of responses into a single dataset.

• **System exports**
  Some systems export data in chunks; this script recombines them.

• **Data cleaning workflows**
  Use this script as a preprocessing step before importing into Excel,
  Power BI, SQL, or Python.

--------------------------------------------------------------------------

Notes
-----
- The script does NOT validate whether all CSV headers match.
  If needed, you can add header validation logic.
- Files are merged in the order returned by Get-ChildItem.
  If order matters, you can sort the list before merging.

--------------------------------------------------------------------------

Support
-------
If you need help modifying or extending this script—such as adding
header validation, sorting, logging, or error handling—feel free to ask.
