**TEST CASES - Laravel To-Do List API**

**Submitted By**

Pravesh Sahai

**Submitted To**

Vipin Tripathi

**Test Case Version**

1.0

**Reviewer Name**

Manmeet Narang, Pooja Joshi

---

### **Goal**
The goal of this project is to develop a **Laravel-based To-Do List API** that allows users to perform **CRUD (Create, Read, Update, Delete) operations** on tasks. The API is built using **PHP Laravel** with a **PostgreSQL database** running in a **Podman container**, and a frontend UI using **Laravel Blade templates** to interact with the API.

---

### **Table of Contents**
- [Test Environment](#test-environment)
- [TC1: Verify Database is Running](#tc1-verify-database-is-running)
- [TC2: Verify API is Running](#tc2-verify-api-is-running)
- [TC3: Verify API Can Connect to Database](#tc3-verify-api-can-connect-to-database)
- [TC4: Verify UI Loads Correctly](#tc4-verify-ui-loads-correctly)
- [TC5: Create a New Task](#tc6-create-a-new-task)
- [TC6: Update an Existing Task](#tc7-update-an-existing-task)
- [TC7: Mark a Task as Completed](#tc8-mark-a-task-as-completed)
- [TC8: Delete a Task](#tc9-delete-a-task)
- [TC9: Validate Required Fields in Task Creation](#tc10-validate-required-fields-in-task-creation)
---

## **Test Environment**
- **Frontend URL**: `http://127.0.0.1:8000`
- **API Base URL**: `http://127.0.0.1:8000/api/todos`
- **Database**: PostgreSQL running in a Podman container
- **Podman Container ID**: `92ec1277009d`
- **Laravel Version**: 12.x
- **PHP Version**: 8.3

---

### **TC1: Verify Database is Running**
**Scenario**: The PostgreSQL database is running.

**Given**
- The PostgreSQL container is started.

**When**
- The tester runs `podman ps`.

**Then**
- The container is listed as running.

**Test Run Date**: <Date>

**Result**:Pass

![Screenshot from 2025-03-26 00-47-09](https://github.com/user-attachments/assets/fac1ca1c-7d26-4943-b033-7b0839920c06)


---

### **TC2: Verify API is Running**
**Scenario**: The API is active and responsive.

**Given**
- Laravel is running (`php artisan serve`).

**When**
- A GET request is sent to `/api/todos`.

**Then**
- The API returns `200 OK`.

**Test Run Date**: <Date>

**Result**:Pass
![Screenshot from 2025-03-26 00-50-48](https://github.com/user-attachments/assets/1cb3c8cb-f90d-4fd3-8949-8f95745ab753)


---

### **TC3: Verify API Can Connect to Database**
**Scenario**: Laravel API successfully connects to PostgreSQL.

**Given**
- The `.env` file contains correct DB credentials.

**When**
- The tester runs `php artisan migrate:status`.

**Then**
- The command returns `Yes` for applied migrations.

**Test Run Date**: <Date>

**Result**:Pass

![Screenshot from 2025-03-26 00-52-11](https://github.com/user-attachments/assets/cd625a82-23b2-47b8-b6e8-bb82c65329f7)

---

### **TC4: Verify UI Loads Correctly**
**Scenario**: The UI loads without errors.

**Given**
- The frontend is deployed.

**When**
- The user opens `http://127.0.0.1:8000` in the browser.

**Then**
- The To-Do List page loads successfully without errors.

**Test Run Date**: <Date>

**Result**:Pass

![Screenshot from 2025-03-26 00-53-20](https://github.com/user-attachments/assets/5dfe567b-8d6f-480b-aabd-fa52ae284234)


---

### **TC5: Create a New Task**
**Scenario**: Users can create a task.

**Given**
- The UI is accessible.

**When**
- The user fills in a title and clicks "Add Task".

**Then**
- The task is saved in the database.

**Test Run Date**: <Date>

**Result**:Pass

![Screenshot from 2025-03-26 00-56-49](https://github.com/user-attachments/assets/eef00270-399f-4f1f-9b36-75411710520f)

---

### **TC6: Update an Existing Task**
**Scenario**: Users can update a task.

**Given**
- The task exists.

**When**
- The user clicks "Edit", modifies the title, and clicks "Save".

**Then**
- The task is updated in the database.

**Test Run Date**: <Date>

**Result**:Pass

![Screenshot from 2025-03-26 00-57-37](https://github.com/user-attachments/assets/f8449322-8215-4f72-869d-abbe88f914b4)

---

### **TC7: Mark a Task as Completed**
**Scenario**: Users can mark tasks as completed.

**Given**
- A task exists.

**When**
- The user checks the "completed" box.

**Then**
- The database updates the task as completed.

**Test Run Date**: <Date>

**Result**:Pass

![Screenshot from 2025-03-26 00-58-36](https://github.com/user-attachments/assets/b1dd9d54-2b69-4212-ab0e-db48b1ce3fb9)

---

### **TC8: Delete a Task**
**Scenario**: Users can delete a task.

**Given**
- A task exists.

**When**
- The user clicks "Delete".

**Then**
- The task is removed from the database.

**Test Run Date**: <Date>

**Result**:Pass

![Screenshot from 2025-03-26 00-59-21](https://github.com/user-attachments/assets/103b30ee-ceb4-4064-8224-1e4a27f130ac)

---

### **TC9: Validate Required Fields in Task Creation**
**Scenario**: The task title is required.

**Given**
- The UI is accessible.

**When**
- The user tries to add a task without a title.

**Then**
- An error message appears.

**Test Run Date**: <Date>

**Result**:Pass

![Screenshot from 2025-03-26 01-00-34](https://github.com/user-attachments/assets/8d7d4bd5-470e-490f-98dc-d5a48065de20)

---
