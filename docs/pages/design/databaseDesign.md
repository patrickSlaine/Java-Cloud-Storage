# ___Proposed Database Entity Relationship___
![Entity Relationship Diagram](../../images/entityRelationshipDiagram.png)

1. User entity is used to represent all users such Normal Users and Administrators.
2. Users are linked to the File's entity via the UserFile entity.
3. The FileActivityLog entity will be used to log every Create, Read, Update or Delete event which occurs for any file within the system. This will allow for a traceable audit log to be produced.