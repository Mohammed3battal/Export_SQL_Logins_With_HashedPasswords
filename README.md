## Script:  Export SQL Server Logins with Passwords, SIDs, and Roles

**Description**:
This script creates two stored procedures:
- `sp_hexadecimal`: Converts binary SID and password hashes to hexadecimal
- `sp_help_revlogin`: Extracts SQL logins (excluding `sa`), along with their:
  - Password hash
  - SID
  - Default database and language
  - Password policy settings
  - Enabled/disabled status
  - Server-level role memberships

The script generates `CREATE LOGIN` statements that can be used to recreate logins on another SQL Server instance, preserving their security configuration exactly.

**Use Case**:
- Server migration
- Disaster recovery
- Replicating logins across environments
- Restoring orphaned logins with the same SID

**How to Use**:
1. Run this script on the **source server** (it creates the procedures).
2. Execute:
   ```sql
   EXEC sp_help_revlogin;
3. run the result in the secondary
