# ___Sequence Diagrams___
The purpose of these sequence diagrams is to map out the interactions that will occur within the codebase whenever a User sends an HTTP request to an API.

The sequence diagrams will be used during the **Requirement Analysis** process to define work-items and during development. This will increase the speed of Agile Software Development because the work-items will be well-defined based on the intended design of the system.


## ___User Functionality___

### ___Get User By ID___

```mermaid
sequenceDiagram
    actor Requestor
    Requestor ->>+ UserController: HTTP GET /user/{UUID}
    UserController->>+GetUserHandler: fetchUserInformation(User UUID)
    GetUserHandler ->>+ UserRepository: getUser(UUID)
    UserRepository -->>+ GetUserHandler: return User
    GetUserHandler -->>+ UserController: return User
    UserController -->>+ Requestor: HTTP Response w/ JSON data
```

### ___Create User___
```mermaid
sequenceDiagram
    actor Requestor
    Requestor ->>+ UserController: HTTP POST /user with JSON Content
    UserController ->>+ CreateUserHandler: createUser(CreateUserValueObject object)
    CreateUserHandler ->>+ UserRepository: createUser(User user)
    UserRepository -->>+ CreateUserHandler: return Boolean
    CreateUserHandler ->>+ UserRepository: findUserByUserName(String username)
    UserRepository -->>+ CreateUserHandler: return User
    CreateUserHandler -->>+ UserController: return UUID
    UserController -->>+ Requestor: HTTP Response w/ JSON Data (UUID)
```

### ___Delete User___
```mermaid
sequenceDiagram
    actor Requestor
    Requestor ->>+ UserController: HTTP DELETE /user (UUID userId, UUID deletorId)
    UserController ->>+ DeleteUserHandler: deleteUser(UUID userId, UUID deletorId)
    alt If userId != deletorId
        DeleteUserHandler ->>+ UserRespository: isAdminUser(UUID id)
        UserRespository -->>+ DeleteUserHandler: return Boolean
    end

    alt If adminUser == true || userRequested == true
        DeleteUserHandler ->>+ UserRepository: deleteUser(UUID id)
        UserRepository -->>+ DeleteUserHandler: return boolean
    end

    DeleteUserHandler -->>+ UserController: return boolean
    UserController -->>+ Requestor: HTTP Response w/ JSON Content
```

### ___Update User___
```mermaid
sequenceDiagram
    actor Requestor
    Requestor ->>+ UserController: HTTP PUT /user (UUID userId, UUID requestorId, UpdateUserObject object)
    UserController ->>+ UpdateUserHandler: updateUser(UpdateUserValueObject object)
    alt If userId != requestorId
        UpdateUserHandler ->>+ UserRepository: isAdminUser(UUID id)
        UserRepository -->>+ UpdateUserHandler: return Boolean
    end

    alt If adminUser == true || userRequested == true
        UpdateUserHandler ->>+ UserRepository: getUser(UUID id)
        UserRepository -->>+ UpdateUserHandler: return User
        UpdateUserHandler ->>+ UserRepository: saveUser(User user)
        UserRepository -->>+ UpdateUserHandler: return boolean
    end

    UpdateUserHandler -->>+ UserController: return boolean
    UserController -->>+ Requestor: HTTP Reponse w/ Json Data
```

## ___File Functionality___

### ___Create File___
```mermaid
sequenceDiagram
    actor Requestor
    Requestor ->>+ FileController: HTTP POST /file
    FileController ->>+ SaveFileHandler: saveFile(File file, UUID userId)
    SaveFileHandler ->>+ FileSecurityImp: checkFile(File file)
    FileSecurityImp -->>+ SaveFileHandler: return boolean
    alt If fileValid != true
    SaveFileHandler -->>+ FileController: throw FileNotValidException
    end
    SaveFileHandler ->>+ UserRepository: getUser(UUID id)
    UserRepository -->>+ SaveFileHandler: return User

    alt If User == null
    SaveFileHandler -->>+ FileController: throw UserNotFoundException
    end

    SaveFileHandler ->>+ FileManagementImp: saveFile(File file)
    FileManagementImp -->>+ SaveFileHandler: return String
    SaveFileHandler ->>+ FileRepository: saveFileReference(File file, User user)
    FileRepository -->>+ SaveFileHandler: return boolean

    SaveFileHandler -->>+ FileController: return boolean
    FileController -->>+ Requestor: HTTP Response w/ Json Date

```