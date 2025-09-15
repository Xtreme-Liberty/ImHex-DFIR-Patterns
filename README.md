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



/patterns/DFIR/
  - DISK_PARSER.hexpat
      - Recognize MBR/GPT Disks and parse MPT/GPT
      - Auto load file system patterns for FAT32, exFAT, NTFS formatted volumes
      - Optional Disk Report
<img width="2572" height="1484" alt="3-DISK-HYBRID" src="https://github.com/user-attachments/assets/d864ebe5-5898-46fd-bfcf-5adef338b9fa" />

        
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

I:            # # # #   # #   
I:            #     #     #   
I:            #     #     #   
I:            # # # #   # # # 
I:             I  m  H  e  x    
 
I: -----------------------------------------
 
I:   ENTITY: _____________________
 
I: EXAMINER: _____________________
 
I: -----------------------------------------
I:    LOCAL: 09/15/2025 @ 06:30:02
I:      UTC: 09/15/2025 @ 10:30:02
I: -----------------------------------------
 
I: -----------------------------------------
I: ---------- FAT32 VOLUME_REPORT ----------
I: -----------------------------------------
I: VOL_LABEL        	= 1GB_F32    
I: FILE_SYSTEM      	= FAT32   
I: SERIAL_NUMBER    	= 0x44FC110A
I: -----------------------------------------
I: BYTES/SECTOR     	= 512
I: SECTORS/CLUSTER  	= 08
I: BYTES/CLUSTER    	= 4096
I: ROOT_ENTRIES     	= 00
I: CLUSTER_COUNT    	= 243232
I: -----------------------------------------
I: VOLUME_SIZE      	= 1949696 SECTORS
I: VOLUME_SIZE      	= 0.9982 GB  @ 1000
I: VOLUME_SIZE      	= 0.9297 GiB @ 1024
I: -----------------------------------------
I: RESERVED_SECTORS 	= 32
I: FAT_COUNT        	= 02
I: FAT_SIZE         	= 1901 SECTORS
I: FAT1_START_OFF   	= 1064960 | 0x104000
I: FAT2_START_OFF   	= 2038272 | 0x1F1A00
I: ROOT_DIR_CLUSTER 	= 02
I: ROOT_DIR_OFFSET  	= 3011584 | 0x2DF400
I: -----------------------------------------
I: SFN_DEL(xE5)     	= DETECTED
I: LFN_DEL(xE5)     	= DETECTED
I: FAT1_EOF_COUNT   	= 23
I: -----------------------------------------
I: ------------------ END ------------------
I: -----------------------------------------
 
I: -----------------------------------------
I: -------------- DISK_REPORT --------------
I: -----------------------------------------
I: DISK_PATH            = /dev/disk6
I: SECTOR_SIZE          = 512 BYTES
I: DISK_SIZE            = 1953165 SECTORS
I: DISK_SIZE            = 1.0000 GB  @ 1000
I: DISK_SIZE            = 0.9313 GiB @ 1024
I: DISK_PROTECT         = NOT_COPY_PROTECTED
I: PART_SCHEME          = HYBRID (MBR + GPT)
I: -----------------------------------------
I: -------------- MBR_MPT [0] --------------
I: -----------------------------------------
I:  STATUS              = INACTIVE/NOT_BOOTABLE
I:  TYPE_CODE           = GPT_PROTECTIVE (0xEE)
I:  FIRST_LBA           = 01
I:  LAST_LBA            = 1953164
I:  VOL_SIZE            = 1953164 SECTORS
I:  VOL_SIZE            = 1.0000 GB
I:  VOL_SIZE            = 0.9313 GiB
I: -----------------------------------------
I: -------------- GPT_HEADER ---------------
I: -----------------------------------------
I: SIGNATURE            = "EFI PART"
I: REVISION             = 0x10000
I: GPT_HDR_CRC          = 0x25C20620
I: GPT_HDR_BACKUP_LBA   = 1953164
I: DISK_GUID            = {ECFF9ACD-647D-42EF-AFE8-5A0E262EEF23}
I: FIRST_USABLE_LBA     = 34
I: LAST_USABLE_LBA      = 1953131
I: MAX_GPT_ENTRIES      = 128
I: GPT_ENTRY_SIZE       = 128 BYTES
I: GPT_ARRAY_CRC        = 0x1525C854
I: -----------------------------------------
I: ------------- GPT_PART [0] --------------
I: -----------------------------------------
I:  PART_TYPE_LABEL     = GUIDPartLabel::BASIC_DATA_PART
I:  PART_TYPE_GUID      = {EBD0A0A2-B9E5-4433-87C0-68B6B72699C7}
I:  UNIQUE_PART_GUID    = {524EFEAD-179B-400C-AC26-A151FAFFAD70}
I:  FIRST_LBA           = 2048
I:  LAST_LBA            = 1951743
I:  ATTR_FLAGS |
I:             |- - - - > NONE
I:  PART_TYPE_NAME      = disk image
I: -----------------------------------------
I: ------------------ END ------------------
I: -----------------------------------------

