# Approach Paper - Laravel API with PostgreSQL & Keycloak

## **Table of Contents**
- [Objective](#objective)
- [Proposed Solution](#proposed-solution)
  - [Approach: Laravel API with Keycloak Authentication & Blade UI](#approach-laravel-api-with-keycloak-authentication--blade-ui)
  - [Architecture Diagram](#architecture-diagram)
  - [Description](#description)
    - [Solution](#solution)
    - [Pros](#pros)
    - [Cons](#cons)
- [Implementation Steps](#implementation-steps)
  - [1. Set Up Laravel Project](#1-set-up-laravel-project)
  - [2. Set Up Keycloak for Authentication](#2-set-up-keycloak-for-authentication)
  - [3. Develop API Endpoints](#3-develop-api-endpoints)
  - [4. Develop Laravel Blade UI](#4-develop-laravel-blade-ui)
  - [5. Perform CRUD Operations](#5-perform-crud-operations)
  - [6. Testing & Deployment](#6-testing--deployment)
- [Pre-requisites](#pre-requisites)
  - [Hardware Requirements](#hardware-requirements)
  - [Software Requirements](#software-requirements)
  - [Networking Requirements](#networking-requirements)

---

## **Objective**
The goal of this project is to develop a **RESTful API** using **PHP Laravel**, with **PostgreSQL as the database** and **Keycloak for authentication and authorization**. This API will support **CRUD (Create, Read, Update, Delete) operations** and will be deployed using **Podman on Ubuntu terminal**. Additionally, a **Laravel Blade Template-based UI** will be used to interact with the API.

---

## **Proposed Solution**

### **Approach: Laravel API with Keycloak Authentication & Blade UI**

### **Architecture Diagram**
![app diagram new](https://github.com/user-attachments/assets/3422ad6c-b12d-4c3c-9cee-94c24f94b422)



### **Description**
#### **Solution:**
- The **user interacts** with the **Laravel Blade-based UI**, which sends CRUD requests to the API.
- The **Laravel API** processes the request and verifies the authentication token with **Keycloak**.
- If the **token is valid**, the API performs CRUD operations on **PostgreSQL** and returns the response.
- If the **token is invalid**, the API returns an **error message**.

#### **Pros:**
- Secure authentication with **Keycloak**.
- **User-friendly UI** using Laravel Blade templates.
- Easy deployment with **Podman containers**.

#### **Cons:**
- Complex initial setup due to **multiple integrations**.
- Requires additional resources to **manage Keycloak**.

### **Implementation Steps**
#### **1. Set Up Laravel Project**
- Install **Laravel** on the Ubuntu server.
- Configure **PostgreSQL** as the database in the `.env` file.

#### **2. Set Up Keycloak for Authentication**
- Deploy **Keycloak server** and configure **clients, roles, and users**.
- Integrate Laravel with Keycloak using **OAuth2/OpenID Connect**.
- Implement **token validation in middleware** to secure API endpoints.

#### **3. Develop API Endpoints**
- Define **routes in `routes/api.php`** for CRUD operations.
- Implement **controllers** for handling requests.
- Use **Eloquent models** for database interactions.

#### **4. Develop Laravel Blade UI**
- Create a **user-friendly interface** to interact with the API.
- Implement forms for **creating, updating, and deleting tasks**.
- Display tasks fetched from the API.

#### **5. Perform CRUD Operations**
- Allow **authenticated users** to perform **create, read, update, and delete** operations.
- Implement **validation and error handling**.

#### **6. Testing & Deployment**
- **Test API functionality** using **Postman**.
- Deploy the API on an **Ubuntu server**.

---

## **Pre-requisites**
### **Hardware Requirements**
- Minimum **4GB RAM**
- **Multi-core processor**
- At least **20GB storage**

### **Software Requirements**
- **Operating System**: Ubuntu 22.04 LTS
- **Web Framework**: Laravel 10
- **Database**: PostgreSQL 15
- **Authentication Server**: Keycloak 21
- **Containerization**: Podman
- **PHP Version**: 8.1+

### **Networking Requirements**
- Secure API endpoints with **HTTPS**
- Open **ports for PostgreSQL, Keycloak, and API server**
- Secure **communication between services**


---


