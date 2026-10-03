# servicenow-acl-project.
# Script-Controlled ACL - Restrict Record Access Based on Field Value

## Description
This lab implements a script-controlled Access Control List (ACL) in ServiceNow. Only users with the bb1 role can read records in `u_institution_details` where Branch is EEE. Administrators retain full access.

## Steps

### 1. User and Roles
- Created user **EEEUser** (First: EEE, Last: User, eeeuser@gmail.com).
- Created roles **bb1, bb2, bb3, bb4** and assigned all to EEEUser.

### 2. Table Creation
- Created table **Institution Details** (`u_institution_details`).
- Fields: Student Roll Number, Student Name, Faculty Name, Branch (ECE, EEE, CSE), Email, Phone Number, Description.
- Added multiple records with different Branch values.

### 3. Read ACL (bb1)
- Elevated to `security_admin`.
- Created ACL: Type record, Operation read, Name `u_institution_details`, Advanced true.
- Requires role: **bb1**. Data condition: **Branch is EEE**.
- Script returns true for admin and bb1, false for others.

### 4. Create ACL (bb2)
- Operation create, Requires role **bb2**, no data condition.

### 5. Write ACL (bb3)
- Operation write, Requires role **bb3**, no data condition.

### 6. Delete ACL (bb4)
- Operation delete, Requires role **bb4**, no data condition.

## Verification
- **bb1 user:** sees only EEE branch records.
- **User without role:** no records displayed.
- **Admin:** sees all records.
- **bb1 + bb2:** New button visible.
- **bb1 + bb2 + bb3:** can edit records.
- **bb1 + bb2 + bb3 + bb4:** can delete records.

## Outcome
Learners understand how script-controlled READ, WRITE, CREATE
