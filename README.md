# ASP.NET Core MVC - Basic Model-View-ViewModel-Controller Structure

This project demonstrates a simple and clean implementation of **ASP.NET Core MVC** using:

- **Models** for data structure
- **ViewModels** for passing multiple models or complex data to views
- **Controllers** to handle logic and routing
- **Views** using Razor for UI rendering

---

## 📦 Project Features

- Add, display, and manage users and related entities
- Use of **ViewModels** to pass combined data to views
- Clean separation of responsibilities using MVC pattern
- Integration with **SQL Server** using **ADO.NET** or Entity Framework (optional)

---

## 🧱 Tech Stack

- ASP.NET Core MVC (.NET 6 or later)
- C# 10+
- Razor Views
- ADO.NET or Entity Framework Core
- SQL Server (via SSMS)
- Bootstrap (optional for styling)

---

## 📁 Folder Structure

```

/MyFirstApp/
├── Controllers/
│   └── HomeController.cs
├── Models/
│   ├── User.cs
│   └── Student.cs
├── ViewModels/
│   └── StudentUser.cs
├── Views/
│   └── Home/
│       └── Index.cshtml
├── wwwroot/
│   └── css, js, etc.
├── appsettings.json
└── Program.cs

````

---

## 🔄 MVC Architecture Explained

### 🧾 Models
Located in `/Models`, these classes represent the **structure of your data**, such as:

```csharp
public class User
{
    public int Id { get; set; }
    public string? Name { get; set; }
    public string? Email { get; set; }
    public int Age { get; set; }
}
````

---

### 📦 ViewModels

Stored in `/ViewModels`, these classes **combine multiple models** or shape data for the view.

```csharp
public class StudentUser
{
    public Student? Student { get; set; }
    public User? User { get; set; }
}
```

---

### 🎮 Controllers

Located in `/Controllers`, these handle **requests and return views**:

```csharp
public class HomeController : Controller
{
    public IActionResult Index()
    {
        var viewModel = new StudentUser
        {
            User = new User { Name = "Alice", Email = "alice@example.com", Age = 25 },
            Student = new Student { Name1 = "Vishal", div1 = "A", age1 = 21 }
        };
        return View(viewModel);
    }
}
```

---

### 🖼️ Views

Stored under `/Views/Home/Index.cshtml`, these use Razor syntax:

```razor
@model MyFirstApp.ViewModels.StudentUser

<h2>User Info</h2>
<p>Name: @Model.User?.Name</p>
<p>Email: @Model.User?.Email</p>
<p>Age: @Model.User?.Age</p>

<h2>Student Info</h2>
<p>Name: @Model.Student?.Name1</p>
<p>Division: @Model.Student?.div1</p>
<p>Age: @Model.Student?.age1</p>
```

---

## 🛠️ Setup Instructions

1. Open the project in Visual Studio 2022 or later.
2. Update the `appsettings.json` with your SQL Server connection string (if using DB).
3. Build and run the project (`F5`).
4. Navigate to `/Home/Index` to test the ViewModel-based view.

---

## ✅ Best Practices Used

* `ViewModels` to pass multiple models to a single view
* Nullable reference types (`string?`) to avoid compiler warnings
* Clean separation of concerns (MVC architecture)

---

## 🧠 Future Ideas

* Add form submission with `POST` actions
* Integrate Entity Framework for DB operations
* Add validation using Data Annotations
* Add CRUD operations for users/students

---

## 📩 Contact

**Developer**: Vishal Waghmode
**Email**: vishalwaghmode247@gmail.com.


