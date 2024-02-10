# ___Technical Consideration___

This document contains considerations that must be made when making decisions about the architecture of the application.

## ___Application Considerations___

- File Access logs must be queryable.
    - File access logs contains events such as:
        - File Creation
        - File Read
        - File Update
        - File Deletion
- Administator Levels
    - Admin (Top Level Admin - Contains access of all other admin types)
    - File Admin - Read, Update & Deletion access to all users files.
    - Database Admin - CRUD access to User database records.
    - User - Can CRUD their own files. Do not have access to any other user files.
- Files must be Encrypted at Rest.
- Files must have a Unique ID which will be used to interact with them.
- File Constraints
    - Max File Size - 50mb
        - This is a guess-timates figure. Theoretically storage platforms could store extremely large files.
        - Main Limiting Factors are:
            - File Upload Time causing Application Latency/ Slowness/ Memory Issues
            - Compute Capacity / Cost
    - How do we actually upload a file via HTTP.
        - Will need extra research....
        - https://spring.io/guides/gs/uploading-files/

## ___Technical Considerations___
1. **Project dependencies** must be managed to ensure vulnerabilities are not unintentional introduced.
2. **Java** must be the primary development language.
3. **Microsoft Azure** must be the cloud platform used.