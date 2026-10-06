# JobBoardPlatform

A job board web application built with ASP.NET Core, following a clean/layered architecture (Domain, Business, Infrastructure, MVC, WebApi).

## Tech Stack

- ASP.NET Core 10 (MVC + Web API)
- Entity Framework Core (SQL Server)
- ASP.NET Core Identity (authentication & roles)
- JWT authentication (Web API)
- MailKit (email notifications)

## Project Structure

- **JobBoardPlatform.Domain** — Entities and enums
- **JobBoardPlatform.Buisiness** — DTOs, interfaces, and business logic/services
- **JobBoardPlatform.Infrastructure** — EF Core DbContext, repositories, migrations, external services (email, JWT)
- **JobBoardPlatform.MVC** — Razor Views front-end (employers, job seekers, admin panel)
- **JobBoardPlatform.WebApi** — REST API for the same functionality

## Features

- Job seeker & employer registration/authentication
- Job posting creation, search, and management
- Job applications with status tracking
- Company profiles
- Admin dashboard: manage employers, job seekers, job postings, email templates
- Email notifications (via SMTP)

## Getting Started

### Prerequisites

- [.NET 10 SDK](https://dotnet.microsoft.com/download)
- SQL Server (LocalDB or full instance)
- An SMTP account for testing emails (e.g. a free [Mailtrap](https://mailtrap.io) sandbox inbox)

### Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/SinaFarahmandian/JobBoardPlatform.git
   cd JobBoardPlatform
   ```

2. Copy the example config and fill in your own values, for **both** `JobBoardPlatform.WebApi` and `JobBoardPlatform.MVC`:
   ```bash
   cp JobBoardPlatform.WebApi/appsettings.example.json JobBoardPlatform.WebApi/appsettings.json
   cp JobBoardPlatform.MVC/appsettings.example.json JobBoardPlatform.MVC/appsettings.json
   ```

   In each `appsettings.json`, set:
   - `ConnectionStrings:DefaultConnection` — your SQL Server instance
   - `Jwt:Key` — a random string of at least 32 characters (must be **identical** in both files)
   - `AdminSeed:Email` / `AdminSeed:Password` — credentials for the seeded admin account
   - `Smtp:*` — your SMTP credentials (e.g. from Mailtrap)

3. Apply database migrations (run from the solution root):
   ```bash
   dotnet ef database update --project JobBoardPlatform.Infrastructure --startup-project JobBoardPlatform.WebApi
   ```

4. Run the application:
   ```bash
   dotnet run --project JobBoardPlatform.MVC
   # or
   dotnet run --project JobBoardPlatform.WebApi
   ```

## Notes

- `appsettings.json` files are gitignored — never commit real credentials. Use `appsettings.example.json` as the template.
- The admin account is seeded on first run using the `AdminSeed` settings above.

## License

No license has been specified for this project yet.
