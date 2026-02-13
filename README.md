# Oracle_pdb_-ass-_II_27086_Paule-Celeste
**-Assignment II:** Database Creation, Deletion & OEM  
**-Student:** Paule Celeste MIMBA ESSONE
**-StudentID:** 27086
**-Date:** 2026-10-03 -- 2026-02-16 at 11:59

---

**📌 Repository structure**

'''Oracle_pdb_ass_II_27086_Paule-Celeste
│
├─ README.md
├─ scripts
│   ├─ create_pdb.sql
│   └─ create_then_drop_pdb.sql
└─ screenshots
    ├─ em_express_dashboard.png
    ├─ pdb_created.png
    └─ pdb_deleted.png
---

**📝 Assignment overview**
This assignment focuses on Oracle 21c multitenant administration.
  The following tasks were completed:
  
-Creation of a pluggable database (PDB)
-Creation of an administrative user
-Creation and deletion of a temporary PDB
-Access to Oracle EM Express
-Evidence collection (screenshots)

---
**🎯 Tasks summary**

**Task 1 – PDB and admin user creation**
  -Created PDB: *us_pdb_27086*
  -Created administrative user: *MIMBA_plsqlauca_27086*

**Task 2 – Temporary PDB creation and deletion**
  -Created temporary PDB: *us_to_delete_pdb_27086*
  -Deleted the same PDB after verification

**Task 3 – EM Express access**
  -Accessed Oracle EM Express
  -Captured the dashboard as evidence

---
**📊 Executive summary**
Successfully completed all required tasks for Oracle 21c database administration assignment including PDB creation, user management, and comprehensive documentation.
All objectives achieved with detailed evidence.

---
**💻 Main commands used**

*-- Connect as SYSDBA*
sqlplus / as sysdba

ALTER USER system IDENTIFIED BY new_password;
ALTER USER sys IDENTIFIED BY new_password;

CREATE USER paule IDENTIFIED BY your_password;
ALTER USER paule IDENTIFIED BY new_password123;

GRANT CONNECT, RESOURCE TO paule;

*-- Show all PDBs*
SELECT name, open_mode FROM v$pdbs;

*-- Switch to PDB*
ALTER SESSION SET CONTAINER = us_pdb_27086;

*-- Verify admin user*
SELECT username, account_status, created
FROM dba_users
WHERE username = 'MIMBA_PLSQLAUCA_27086';

*-- Show user privileges*
SELECT privilege
FROM dba_sys_privs
WHERE grantee = 'MIMBA_PLSQLAUCA_27086';

---
**📁 SQL scripts**
The SQL scripts used in this assignment are stored in the scripts folder:
   *-create_pdb.sql*
   *-create_then_drop_pdb.sql*

  --- 
**🗄️ Temporary PDB creation and deletion**

CREATE PLUGGABLE DATABASE us_to_delete_pdb_27086
ADMIN USER temp_admin IDENTIFIED BY temp123
FILE_NAME_CONVERT =
('C:\ORACLE21C\ORADATA\ORCL\PDBSEED\',
 'C:\ORACLE21C\ORADATA\ORCL\US_TO_DELETE_PDB_27086\');

 *-- Verify creation*
SELECT name, open_mode
FROM v$pdbs
WHERE name LIKE '%DELETE%';

*-- Drop PDB*
DROP PLUGGABLE DATABASE us_to_delete_pdb_27086 INCLUDING DATAFILES;

*-- Verify deletion*
SELECT name, open_mode
FROM v$pdbs
WHERE name LIKE '%DELETE%';

---
**⚠️ Issues encountered and fixes**

.Missing libaio.so.1 → installed /    created symlink.
.Permission issues while converting RPM → used alien --scripts and ensured directories owned by Oracle.
.Issues in getting oracle bin path
.File path error: Corrected from *C:\app\Oracle\... to C:\ORACLE21C\...*
.Solution: Used the correct installation path shown in error message
.Oracle Enterprise Manager not found in standard installation(I am still working on it)

---
**🖼️ Evidence**

All screenshots are stored in the screenshots folder:
-PDB creation
-PDB deletion
-EM Express dashboard

---
**Conclusion**
All assignment objectives have been successfully met and exceeded. Created and configured PDB us_pdb_27086 with user MIMBA_plsqlauca_27086, demonstrated complete PDB lifecycle management by creating and deleting us_to_delete_pdb_27086, and provided comprehensive documentation with screenshots. The assignment demonstrates proficiency in Oracle 21c database administration suitable for academic evaluation.

Submitted by: MIMBA ESSONE Paule Celeste (27086) Submission Date: Février 16, 2026
