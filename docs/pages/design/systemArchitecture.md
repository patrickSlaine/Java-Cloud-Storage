# ___Proposed System Architecture___

![Architecture Diagram](../../images/architectureDiagram.png)

1. **Microsoft Azure** has been chosen as the single Cloud Services Provider within this system.
    - In-order to improve my knowledge of Microsoft Azure as I work towards AZ-204 Certification.
    - I have pre-existing knowledge about developing solutions using Azure.
2. **Blob Storage** was chosen as the File Storage solution because:
    - Blog Storage's access tiers will improve the solution's cost effectiveness. Since data must be stored within our solution for an indefinite period of time, being able to store file's which are in-frequently accessed in **Cold** or **Archive** tier storage will **reduce storage costs**.
    - Blob Storage has client libaries for a large number of programming languages meaning our choice of development language isn't restricted by this technology.
    - Blob Storage automatically **encrypts and decrypts files at rest using AES-256**.

3. **App Service** has been chosen to host the storage application. 
    - Integration with DevOps CICD pipelines such as GitHub Actions.
    - Ability to automatically scale to respond to changes in traffic.
    - Support for Containerisation and Docker.

4. **SQL Database** has been chosen to store the application's structured information such as User and File related information.
    - Supports Data Encryption at Rest using AES and 3DES.


### ___Areas of Potential Change___
1. The interaction between the User and Storage Application may change whenever this application is introduced into a larger **Product Architecture**.
    - A **Front-End Application** may be used to interact with the Storage application.
    - In a Product Architecture, Back-End Services such as the Storage application may be behind a **Reverse Proxy**.  
    - A **Load Balancer** could be used to balance traffic between difference instances of the Storage Application. *Role could be covered by Reverse Proxy.
2. Azure Blob Storage could be replaced with **Azure Files**.
    - To allow the developer to gain experience with Azure Files.
3. Azure App Service could be replaced with a difference application hosting environment such as **Azure Container Instances** or **Azure Kubernetes Clusters**.
