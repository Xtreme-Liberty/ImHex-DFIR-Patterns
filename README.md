ImHex Pattern Files - Digital Forensics

Enhanced features of the stock Disk/Filesystem pattern files for forensic review of disk content.

Install:
  - Create a new folder called "DFIR"
  - Add these updated pattern files to "DFIR"
<img width="1192" height="658" alt="1-Folder_Structure" src="https://github.com/user-attachments/assets/35183dfc-b5fa-426b-bddd-35d94a6b7f8a" />


Use:
  - Open a physical disk via Raw Provider (read-only)
      - EXAMPLE: /dev/disk6
  - Import Pattern File
      - EXAMPLE: DISK_PARSER.hexpat
  <img width="558" height="539" alt="2-DISK_PARSER-Pattern" src="https://github.com/user-attachments/assets/f05775ae-fbe0-4414-9ec1-cbb9daed1f19" />




  - DISK_PARSER.hexpat
      - Recognize MBR/GPT Disks and parse MPT/GPT
        - Including Logical Volumes in an Extended Partition (container) 
      - Auto load file system patterns for FAT32, exFAT, NTFS formatted volumes
      - Optional Disk Report
<img width="2572" height="1484" alt="3-DISK-HYBRID" src="https://github.com/user-attachments/assets/d864ebe5-5898-46fd-bfcf-5adef338b9fa" />
<img width="2572" height="1484" alt="3a-DISK-MBR" src="https://github.com/user-attachments/assets/f893c375-d196-4147-b2c9-0d281c789184" />



        
  - FAT32.hexpat
      - Auto loaded by DISK_PARSER.hexpat
      - Parse VBR, FAT1, FAT2, Root Dir, and 1 level of SubDirs
      - FAT1/FAT2 Cluster chaining with SFN resolution
      - LFN/SFN Alias grouping in Root Dir
      - Recognize deleted entries (xE5)
      - File Content pointer
      - D/T Conversions
      - Optional FAT32 Volume Report
<img width="2572" height="1484" alt="4-FAT32-1_SMALL_TXT" src="https://github.com/user-attachments/assets/ca849df6-780f-437d-90ce-3a4e461f82e7" />
<img width="2572" height="1484" alt="5-FAT32_ROOT_DIR" src="https://github.com/user-attachments/assets/eddc1be5-fd20-49e1-af38-dd302a1b6884" />
<img width="2572" height="1484" alt="6-FAT32_SFN_POINTER" src="https://github.com/user-attachments/assets/b175e5bf-5d12-41ad-9995-b57273ea8103" />



        
  - exFAT.hexpat
      - Auto loaded by DISK_PARSER.hexpat
      - Parse VBR/Boot Sector/Extended Sectors, FAT1, Root Dir
      - Recognize active directory entries (x85, xC0, xC1)
      - Recognize inactive directory entries (x05, x40, x41)
      - xC0/x40 File Content pointer
      - D/T Conversions
      - Optional exFAT Volume Report
<img width="2572" height="1484" alt="7-exFAT-1" src="https://github.com/user-attachments/assets/5ae26e10-3704-4f2b-883c-bee9f51dad89" />
<img width="2572" height="1484" alt="8-exFAT_xC0" src="https://github.com/user-attachments/assets/c964be45-b461-41ab-be07-aa6478d9f237" />
<img width="2572" height="1484" alt="9-exFAT-Data_Pointer" src="https://github.com/user-attachments/assets/ba97ad60-7da8-4256-a59f-2d13f4e0faca" />



        
   - NTFS.hexpat
      - Auto loaded by DISK_PARSER.hexpat
      - Parse VBR (Boot Sector), $MFT, Root Dir, and Indexes
      - Recursively parse the $Metadata files, $Attributes, and user files/dirs
          - Added file record | parent [MFT#] [SEQ#] indicators
      - Parse x80 Data Runs
      - File Content pointer
      - D/T Conversions
      - Optional NTFS Volume Report
<img width="2572" height="1484" alt="10-NTFS-DT" src="https://github.com/user-attachments/assets/c7208a87-f873-490f-9d39-aafbb193ad7b" />
<img width="2572" height="1484" alt="11-NTFS-DATA_RUN" src="https://github.com/user-attachments/assets/581294b0-ccdd-454b-9d46-632d59297bbf" />
<img width="2572" height="1484" alt="12-NTFS-DATA_POINTER" src="https://github.com/user-attachments/assets/f3fd1754-25a6-4fa6-88da-f9409dc1ddaa" />




  - Optional Reports
    - Simply copy the console output to a file...

    - To enable/disable the reports:
      - Open each DFIR related .hexpat
      - Find the report constant (near the top)
        - "true" = enabled
        - "false" = disabled

    [exFAT_Report.pdf](https://github.com/user-attachments/files/22339456/exFAT_Report.pdf)
  
    [MBR_5_VOLs.pdf](https://github.com/user-attachments/files/22354005/MBR_5_VOLs.pdf)


