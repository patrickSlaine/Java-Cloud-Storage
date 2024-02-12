# ___API Definition___
The API Definitions are based on the Database Design that were defined earlier in the Software Design process. The API's will be used later in the design process to create Sequence Diagrams of the system.

___**Important Note** - All endpoints will be written using HTTP___

## ___Contents___
- [User Endpoints](#user-endpoints)
- [File Endpoints](#file-endpoints)
- [Admin Endpoints](#admin-endpoints)

## ___User Endpoints___

- GET User
    - Receives User UUID
    - Returns
        - 200 OK w\ User Details
        - 400 BAD REQUEST
        - 404 NOT FOUND 
        - 500 INTERNAL SERVER ERROR
- POST User
    - Receives User Details
    - Returns
        - 201 CREATED w\ User UUID
        - 400 BAD REQUEST
        - 500 INTERNAL SERVER ERROR
- DELETE User
    - Receives User Details
    - Returns 
        - 200 OK
        - 400 BAD REQUEST
        - 404 NOT FOUND
        - 500 INTERNAL SERVER ERROR
- PUT User
    - Received User UUID & Updated Details
    - Returns
        - 200 OK
        - 400 BAD REQUEST
        - 404 NOT FOUND
        - 500 INTERNAL SERVER ERROR

## ___File Endpoints___
- POST File
    - Receives File & User UUID
    - Returns
        - 201 CREATED w\ File UUID
        - 400 BAD REQUEST
        - 500 INTERNAL SERVER ERROR
- GET FILE
    - Received File UUID & User UUID
    - Returns
        - 200 OK w\ File
        - 400 BAD REQUEST
        - 404 NOT FOUND
        - 500 INTERNAL SERVER ERROR
- PUT File
    - Receives File, File UUID & User UUID
    - Returns
        - 200 OK w\ File
        - 400 BAD REQUEST
        - 404 NOT FOUND
        - 500 INTERNAL SERVER ERROR
- DELETE File
    - Receives File UUID & User UUID
    - Returns
        - 200 OK
        - 400 BAD REQUEST
        - 404 NOT FOUND
        - 500 INTERNAL SERVER ERROR
- GET File List
    - Receives User UUID
    - Returns 
        - 200 OK w\ File List
        - 400 BAD REQUEST
        - 404 NOT FOUND
        - 500 INTERNAL SERVER ERROR

## ___Admin Endpoints___
- GET User List
    - Receives Admin UUID
    - Returns
        - 200 OK w\ Paginated List of Users
        - 400 BAD REQUEST
        - 404 NOT FOUND
        - 500 INTERNAL SERVER ERROR


