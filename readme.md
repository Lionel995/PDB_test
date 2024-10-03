# Oracle PDB Management Assignment

This repository documents the process of creating and managing Pluggable Databases (PDBs) in Oracle, including creation, deletion, and monitoring through Oracle Enterprise Manager.

## 1. Creating a PDB

SQL Query:
```sql
CREATE PLUGGABLE DATABASE my_pdb
ADMIN USER pdb_admin IDENTIFIED BY secure_password
ROLES = (CONNECT)
DEFAULT TABLESPACE users
DATAFILE '/u01/app/oracle/oradata/orcl/my_pdb/users01.dbf' SIZE 250M AUTOEXTEND ON
FILE_NAME_CONVERT = ('/u01/app/oracle/oradata/orcl/pdbseed/',
                     '/u01/app/oracle/oradata/orcl/my_pdb/');
```

Explanation:
This query creates a new PDB named 'my_pdb' with an admin user 'pdb_admin'. It sets up a default tablespace and specifies the location for the datafile. The FILE_NAME_CONVERT clause ensures proper file path conversion from the seed PDB to the new PDB.


## 2. Deleting a PDB

SQL Queries:
```sql
ALTER PLUGGABLE DATABASE my_pdb CLOSE IMMEDIATE;
DROP PLUGGABLE DATABASE my_pdb INCLUDING DATAFILES;
```

Explanation:
The first query closes the PDB immediately, ensuring no active connections remain. The second query drops the PDB and removes all associated datafiles, freeing up storage space.



## 3. Oracle Enterprise Manager Dashboard



Key Observations:
- Overall database health status: [e.g., Good, with no critical alerts]
- Resource utilization: [e.g., CPU at 65%, memory at 80%]
- Number of active sessions: [e.g., 25]
- Performance metrics for PDBs: [e.g., 'my_pdb' showing normal I/O operations]

## Conclusion

This assignment demonstrated the process of creating and managing PDBs in Oracle. Key learnings include the importance of proper resource allocation during PDB creation and the efficiency of the Oracle Enterprise Manager in monitoring database performance. The hands-on experience provided valuable insights into real-world database administration tasks.

