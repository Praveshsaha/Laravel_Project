# IMPLEMENTATION JOURNAL - Laravel To-Do List API with PostgreSQL

## **Submitted By**
**Pravesh Sahai**

## **Submitted To**
**Vipin Tripathi**

## **Test Case Version**
**1.0**

## **Reviewer Name**
**Manmeet Narang, Pooja Joshi**

---

## **Goal**
The purpose of this project is to develop a Laravel-based To-Do List API that enables users to create, update, delete, and retrieve tasks. The system is built with PostgreSQL as the database and is containerized using Podman. It also includes a front-end UI developed with Laravel Blade templates to interact with the API.

---

## **Table of Contents**

1. [Prerequisites](#prerequisites)
   - [Hardware Requirements](#hardware-requirements)
   - [Software Requirements](#software-requirements)
   - [Network Requirements](#network-requirements)
2. [Implementation Steps](#implementation-steps)
   - [Step 1: Setting up the Laravel Project](#step-1-setting-up-the-laravel-project)
   - [Step 2: Setting up PostgreSQL with Podman](#step-2-setting-up-postgresql-with-podman)
   - [Step 3: Configure Database in Laravel](#step-3-configure-database-in-laravel)
   - [Step 4: Creating Models and Migrations](#step-4-creating-models-and-migrations)
   - [Step 5: Implementing the Controller](#step-5-implementing-the-controller)
   - [Step 6: Defining Routes](#step-6-defining-routes)
   - [Step 7: Setting up the UI with Laravel Blade](#step-7-setting-up-the-ui-with-laravel-blade)
   - [Step 8: Testing the API](#step-8-testing-the-api)
3. [Conclusion](#conclusion)

---

## **Prerequisites**

### **Hardware Requirements**
- Ubuntu OS
- Minimum 2GB RAM
- Minimum 10GB Disk Space

### **Software Requirements**
- Laravel 9.x
- PostgreSQL
- Podman

### **Network Requirements**
- Internet connection for downloading dependencies
- Localhost setup for API testing

---
# Implementation Journal

## **Project Title:** Laravel To-Do List API with PostgreSQL

## **Introduction**
This project involves the development of a To-Do List REST API using PHP Laravel framework with PostgreSQL as the database, containerized using Podman. The API supports CRUD operations and is integrated with a front-end UI using Laravel Blade templates to demonstrate these operations.

---
## **Step 1: Setting up the Laravel Project**

### **Initialize Laravel**
To begin, a Laravel project was initialized using the following command:
```sh
mkdir laravel-todo && cd laravel-todo
composer create-project laravel/laravel .
```

---
## **Step 2: Setting up PostgreSQL with Podman**

### **Pull PostgreSQL Image from Docker Hub**
```sh
podman pull docker.io/library/postgres:latest
```

### **Run PostgreSQL Container**
```sh
podman run -d \
  --name postgres \
  -e POSTGRES_USER=myuser \
  -e POSTGRES_PASSWORD=mypassword \
  -e POSTGRES_DB=tododb \
  -v /home/user/p-data:/var/lib/postgresql/data \
  docker.io/library/postgres:latest
```

### **Verify PostgreSQL is Running**
```sh
podman ps
```

---
## **Step 3: Configure Database in Laravel**

Modify the `.env` file with PostgreSQL credentials:
```env
DB_CONNECTION=pgsql
DB_HOST=127.0.0.1
DB_PORT=5432
DB_DATABASE=tododb
DB_USERNAME=myuser
DB_PASSWORD=mypassword
```

Update `config/database.php` to ensure PostgreSQL is set as the default database:
```php
'default' => env('DB_CONNECTION', 'pgsql'),
```

---
## **Step 4: Creating Models and Migrations**

Generate a model with migration and controller:
```sh
php artisan make:model Todo -a
```

Modify the migration file in `database/migrations/`:
```php
Schema::create('todos', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->string('title');
    $table->boolean('completed')->default(false);
    $table->timestamps();
});
```

Run the migration:
```sh
php artisan migrate
```

---
## **Step 5: Implementing the Controller**

Modify `app/Http/Controllers/TodoController.php` to handle CRUD operations:

### **Get All To-Dos**
```php
public function index() {
    return response()->json(Todo::all());
}
```

### **Create a New To-Do**
```php
public function store(Request $request) {
    $todo = Todo::create($request->all());
    return response()->json($todo, 201);
}
```

### **Update a To-Do**
```php
public function update(Request $request, $id) {
    $todo = Todo::findOrFail($id);
    $todo->update($request->all());
    return response()->json($todo);
}
```

### **Delete a To-Do**
```php
public function destroy($id) {
    Todo::findOrFail($id)->delete();
    return response()->json(['message' => 'Deleted successfully']);
}
```

---
## **Step 6: Defining Routes**
Modify `routes/api.php` to add API endpoints:
```php
Route::get('/todos', [TodoController::class, 'index']);
Route::post('/todos', [TodoController::class, 'store']);
Route::put('/todos/{id}', [TodoController::class, 'update']);
Route::delete('/todos/{id}', [TodoController::class, 'destroy']);
```

---
## **Step 7: Setting up the UI with Laravel Blade**

Create a simple front-end using Laravel Blade templates:

- A form to add new tasks.
- A list of tasks with options to update or delete.
- JavaScript (AJAX) to interact with the API.

Example view file (`resources/views/todo.blade.php`):
```html
<form method="POST" action="/api/todos">
    <input type="text" name="title" placeholder="Task Title" required>
    <button type="submit">Add Task</button>
</form>
<ul>
    @foreach($todos as $todo)
        <li>{{ $todo->title }} - {{ $todo->completed ? 'Completed' : 'Pending' }}</li>
    @endforeach
</ul>
```

---
## **Step 8: Testing the API**

Use Postman or cURL to test the API:
```sh
curl -X GET http://127.0.0.1:8000/api/todos
```

---
## **Conclusion**
The Laravel To-Do List API successfully implements CRUD operations with PostgreSQL as the database and is containerized using Podman. The Blade template UI allows users to interact with the API, creating a complete, functional application.


