# ImHex-DFIR-Hexpats
ImHex Pattern Files - Digital Forensics

Enhanced features of the stock Disk/Filesystem pattern files for forensic review of disk content.

Install:
  - Create a new folder called "DFIR"
  - Add these updated pattern files to "DFIR"

Use:
  - Open a physical disk via Raw Provider (read-only)
      - EXAMPLE: /dev/disk6
  - Import Pattern File
      - EXAMPLE: DISK_PARSER.hexpat


/patterns/DFIR/
  - DISK_PARSER.hexpat
      - Recognize MBR/GPT Disks and parse MPT/GPT
      - Auto load file system patterns for FAT32, exFAT, NTFS formatted volumes
      - Optional Disk Report
  - FAT32.hexpat
      - Auto loaded by DISK_PARSER.hexpat
      - Parse VBR, FAT1, FAT2, Root Dir, and 1 level of SubDirs
      - FAT1/FAT2 Cluster chaining with SFN resolution
      - LFN/SFN Alias grouping in Root Dir
      - Recognize deleted entries (xE5)
      - File Content pointer
      - D/T Conversions
      - Optional FAT32 Volume Report
  - exFAT.hexpat
      - Auto loaded by DISK_PARSER.hexpat
      - Parse VBR/Boot Sector/Extended Sectors, FAT1, Root Dir
      - Recognize active directory entries (x85, xC0, xC1)
      - Recognize inactive directory entries (x05, x40, x41)
      - xC0/x40 File Content pointer
      - D/T Conversions
      - Optional exFAT Volume Report
   - NTFS.hexpat
      - Auto loaded by DISK_PARSER.hexpat
      - Parse VBR (Boot Sector), $MFT, Root Dir, and Indexes
      - Recursively parse the $Metadata files, $Attributes, and user files/dirs
          - Added file record | parent [MFT#] [SEQ#] indicators
      - Parse x80 Data Runs
      - File Content pointer
      - D/T Conversions
      - Optional NTFS Volume Report

