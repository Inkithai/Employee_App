# Employee Management System

This project is a full-stack Employee Management System, which includes a React frontend, a Spring Boot backend, and a database. It provides functionalities to create, view, update, and list employees, along with the necessary RESTful APIs to handle these operations.

## Project Structure

### Frontend (React)

- **React Frontend**: This is the main user interface for the application, where users can interact with employee data.
- **UI Components**:
  - **CreateEmployeeComponent**: A form to create a new employee.
  - **ListEmployeeComponent**: A list of all employees.
  - **UpdateEmployeeComponent**: A form to update an existing employee.
  - **ViewEmployeeComponent**: A page to view employee details.
  - **HeaderComponent**: Header for the application.
  - **FooterComponent**: Footer for the application.
  
- **EmployeeService**: A service layer to make REST API calls to the Spring Boot backend.

### Backend (Spring Boot)

- **Spring Boot Backend**: This is the backend service that provides RESTful APIs for the frontend to interact with.
- **Layers**:
  - **EmployeeController**: The controller layer to handle HTTP requests and send responses.
  - **Employee Model**: Represents the employee entity.
  - **EmployeeRepository**: Repository for CRUD operations on the employee data.
  - **ResourceNotFoundException**: Custom exception to handle resource not found errors.
  - **ApplicationProperties**: Configuration file for Spring Boot.

### Database

- **Database**: The database layer where employee data is stored, accessed, and manipulated.

## Flowchart Overview

This project is structured into three main layers: Frontend, Backend, and Database. The following flowchart gives an overview of how these layers interact with each other:

```mermaid
flowchart TD
    %% Frontend Layer
    subgraph "Frontend"
        React_Frontend("React Frontend"):::frontend
        subgraph "UI Components"
            CreateEmployeeComponent("CreateEmployeeComponent"):::frontend
            ListEmployeeComponent("ListEmployeeComponent"):::frontend
            UpdateEmployeeComponent("UpdateEmployeeComponent"):::frontend
            ViewEmployeeComponent("ViewEmployeeComponent"):::frontend
            HeaderComponent("HeaderComponent"):::frontend
            FooterComponent("FooterComponent"):::frontend
        end
        EmployeeService("EmployeeService"):::service
    end

    %% Backend Layer
    subgraph "Backend"
        SpringBoot_Backend("Spring Boot Backend"):::backend
        subgraph "Layers"
            EmployeeController("EmployeeController"):::backend
            EmployeeModel("Employee Model"):::backend
            EmployeeRepository("EmployeeRepository"):::backend
            ResourceNotFoundException("ResourceNotFoundException"):::backend
            ApplicationProperties("application.properties"):::config
        end
    end

    %% Database
    Database("Database"):::db

    %% Connections - Frontend interactions
    CreateEmployeeComponent -->|"submit"| EmployeeService
    ListEmployeeComponent -->|"fetchData"| EmployeeService
    EmployeeService -->|"RESTcall"| EmployeeController

    %% Connections - Backend interactions
    EmployeeController -->|"repositoryCall"| EmployeeRepository
    EmployeeController -->|"errorHandling"| ResourceNotFoundException
    EmployeeRepository -->|"CRUD"| Database

    %% Click Events for Frontend Components
    click React_Frontend "https://github.com/inkithai/employee_app/tree/main/react-frontend"
    click CreateEmployeeComponent "https://github.com/inkithai/employee_app/blob/main/react-frontend/src/components/CreateEmployeeComponent.jsx"
    click ListEmployeeComponent "https://github.com/inkithai/employee_app/blob/main/react-frontend/src/components/ListEmployeeComponent.jsx"
    click UpdateEmployeeComponent "https://github.com/inkithai/employee_app/blob/main/react-frontend/src/components/UpdateEmployeeComponent.jsx"
    click ViewEmployeeComponent "https://github.com/inkithai/employee_app/blob/main/react-frontend/src/components/ViewEmployeeComponent.jsx"
    click HeaderComponent "https://github.com/inkithai/employee_app/blob/main/react-frontend/src/components/HeaderComponent.js"
    click FooterComponent "https://github.com/inkithai/employee_app/blob/main/react-frontend/src/components/FooterComponent.jsx"
    click EmployeeService "https://github.com/inkithai/employee_app/blob/main/react-frontend/src/services/EmployeeService.js"

    %% Click Events for Backend Components
    click SpringBoot_Backend "https://github.com/inkithai/employee_app/tree/main/springboot-backend"
    click EmployeeController "https://github.com/inkithai/employee_app/blob/main/springboot-backend/src/main/java/net/javaguides/springboot/controller/EmployeeController.java"
    click EmployeeModel "https://github.com/inkithai/employee_app/blob/main/springboot-backend/src/main/java/net/javaguides/springboot/model/Employee.java"
    click EmployeeRepository "https://github.com/inkithai/employee_app/blob/main/springboot-backend/src/main/java/net/javaguides/springboot/repository/EmployeeRepository.java"
    click ResourceNotFoundException "https://github.com/inkithai/employee_app/blob/main/springboot-backend/src/main/java/net/javaguides/springboot/exception/ResourceNotFoundException.java"
    click ApplicationProperties "https://github.com/inkithai/employee_app/blob/main/springboot-backend/src/main/resources/application.properties"

    %% Styles
    classDef frontend fill:#ADD8E6,stroke:#333,stroke-width:2px;
    classDef service fill:#FFB6C1,stroke:#333,stroke-width:2px;
    classDef backend fill:#90EE90,stroke:#333,stroke-width:2px;
    classDef config fill:#F3E5AB,stroke:#333,stroke-width:2px;
    classDef db fill:#FFD700,stroke:#333,stroke-width:2px;
