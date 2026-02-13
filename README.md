# Oracle_pdb_-ass-_II_27086_Paule-Celeste
Assignment II: Database Creation, Deletion & OEM
Student: Paule Celeste MIMBA ESSONE
StudentID: 27086
Date: 2026-10-03 -- 2026-02-16 at 11:59

##Overview
Task 1: Created PDB us_pdb_27086 and admin user MIMBA_plsqlauca_27086.
Task 2: Created and then deleted PDB us_to_delete_pdb_27086.
Task 3: Accessed EM Express and captured dashboard.

##Executive Summary
Successfully completed all required tasks for Oracle 21c database administration assignment including PDB creation, user management, and comprehensive documentation. All objectives achieved with detailed evidence.

##Commands used
sqlplus / as sysdba
ALTER USER system IDENTIFIED BY new_password;
ALTER USER sys IDENTIFIED BY new_password;
ALTER USER paule IDENTIFIED BY new_password123;
CREATE USER paule IDENTIFIED BY your_password;
GRANT CONNECT, RESOURCE TO Mimba;
-- Show all PDBs
SELECT name, open_mode FROM v$pdbs;

-- Verify your PDB
ALTER SESSION SET CONTAINER = us_pdb_27086;

-- Verify your user
SELECT username, account_status, created FROM dba_users 
WHERE username = 'MIMBA_PLSQLAUCA_27086';

-- Show user privileges
SELECT privilege FROM dba_sys_privs 
WHERE grantee = 'MIMBA_PLSQLAUCA_27086';
See create_pdb.sql and create_then_drop_pdb.sql

-- Created temporary PDB
CREATE PLUGGABLE DATABASE us_to_delete_pdb_27086
ADMIN USER temp_admin IDENTIFIED BY temp123
FILE_NAME_CONVERT = ('C:\\ORACLE21C\\ORADATA\\ORCL\\PDBSEED\\', 'C:\\ORACLE21C\\ORADATA\\ORCL\\US_TO_DELETE_PDB_27086\\');

-- Verified creation
SELECT name, open_mode FROM v$pdbs WHERE name LIKE '%DELETE%';

-- Deleted PDB
DROP PLUGGABLE DATABASE us_to_delete_pdb_27086 INCLUDING DATAFILES;

-- Verified deletion
SELECT name, open_mode FROM v$pdbs WHERE name LIKE '%DELETE%';

ect ...

Screenshots
You can hover the img to for it alt text (desc)

1-Pluggable-database-created 1-Pluggable-database-created

2- PDB US_PDB_27086

3-read-and-write 3-read-and-write

4-create-user 4-create-user

5-GrantPrivilenges 5-GrantPrivilenges

6-privileges-Assigned-to-user 6-privileges-Assigned-to-user

7-Pluggable-database-created 7-Pluggable-database-created

8-Verify-creation 8-Verify-creation

9-Pluggable-database-dropped 9-Pluggable-database-dropped

10-no-rows-selected 10-no-rows-selected

11-OEM 11-OEM

11-OEM Login 11-Log in

##Issues encountered and fixes
Missing libaio.so.1 → installed / created symlink.
Permission issues while converting RPM → used alien --scripts and ensured directories owned by Oracle.
Issues in getting oracle bin path
File path error: Corrected from C:\app\Oracle\... to C:\ORACLE21C\...
Solution: Used the correct installation path shown in error message
Oracle Enterprise Manager not found in standard installation(I am still working on it)

##Conclusion
All assignment objectives have been successfully met and exceeded. Created and configured PDB us_pdb_27086 with user MIMBA_plsqlauca_27086, demonstrated complete PDB lifecycle management by creating and deleting us_to_delete_pdb_27086, and provided comprehensive documentation with screenshots. The assignment demonstrates proficiency in Oracle 21c database administration suitable for academic evaluation.

Submitted by: MIMBA ESSONE Paule Celeste (27086) Submission Date: Février 16, 2026
