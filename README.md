# FitLynx Backend

FitLynx is a gym management system designed to streamline reservations, attendance tracking, and membership management. The backend is built using **Django** and **Django REST Framework (DRF)**, providing a robust API for both administrative and student users.

## Features

### User Management
* **Authentication**: Secure login and user registration.
* **JWT Integration**: Uses `djangorestframework-simplejwt` for secure token-based authentication.
* **Role-Based Access**: Distinguishes between standard users (students) and administrators.
* **Password Recovery**: Integrated password reset via email using SendGrid.

### Gym Operations
* **Reservations**: Students can reserve time slots based on gym capacity and operating hours.
* **Attendance Tracking**: Administrators can confirm student attendance or create attendance records without a prior reservation.
* **Schedules**: Dynamic management of gym opening and closing times for each day of the week.

### Memberships & Penalties
* **Membership Plans**: Management of active student memberships to allow extended gym access.
* **Penalty System**: Automatically restricts users from making reservations if they fail to attend their scheduled slots.

### Reporting
* **Attendance Reports**: Generates downloadable Excel reports (`.xlsx`) for gym administrators to analyze attendance data.

---

## Technical Stack

* **Framework**: Django 5.1.1.
* **API**: Django REST Framework.
* **Database**: PostgreSQL.
* **Email Service**: SendGrid API.
* **Data Handling**: Pandas & Openpyxl (for reports).

---

## Installation

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd FitLynx-Backend-master
   ```

2. **Set up a virtual environment**:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure Environment Variables**:
   Create a `sendgrid.env` file in the root directory and add your SendGrid API key:
   ```env
   SENDGRID_API_KEY=your_api_key_here
   ```

5. **Database Setup**:
   Configure your PostgreSQL credentials in `Backend/settings.py`.

6. **Run Migrations**:
   ```bash
   python manage.py migrate
   ```

7. **Start the server**:
   ```bash
   python manage.py runserver
   ```

---

## API Endpoints Summary

| Endpoint | Method | Description |
| :--- | :--- | :--- |
| `/gym/Login/` | POST | User authentication and JWT generation. |
| `/gym/CreateUser/` | POST | Register a new user. |
| `/gym/CreateReserve/` | POST | Create a gym reservation. |
| `/gym/GetReport/<gym_id>/` | GET | Download attendance report (Admin only). |
| `/gym/UpdateSchedule/<gym_id>/` | POST | Update gym operating hours (Admin only). |
| `/gym/PenalizeUser/` | POST | Penalize a user for missed sessions. |

For a full list of available paths, refer to `gym/urls.py`.
