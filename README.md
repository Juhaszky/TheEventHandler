# TheEventHandler

An event handler where customers can post events.

## Task: Event Booking System

Create an Event Booking System that allows users to browse and book tickets for events. This exercise includes user management, event scheduling, availability management, and dynamic pricing for VIP tickets.

## Requirements

### Backend (ASP.NET Core)

Create a RESTful API that allows:

- **Managing users** (registration, login)
- **Managing events** (adding, updating, viewing details)
- **Booking tickets** for events, including seat availability limits
- **Dynamic ticket pricing** for VIP seats

### Frontend (Angular)

Build a frontend application to interact with the API:

- User registration, login, event details view, and ticket booking
- Event list display and user-specific views for managing bookings

## Detailed Instructions

### Backend (ASP.NET Core)

1. **User Authentication and Authorization**
   - Implement user registration and login with JWT-based authentication.
   - Create endpoints for user registration (`/users/register`) and login (`/users/login`).
   - Secure the API using ASP.NET Core Identity with role-based access (USER for standard users, ADMIN for event managers).

2. **Event Entity and Repository**
   - Create an Event entity with fields: `Id`, `Name`, `Description`, `Location`, `Date`, `AvailableSeats`, and `Price`.
   - Set up an `EventRepository` to manage event data using **Entity Framework Core**.

3. **Booking Entity and Service**
   - Define a Booking entity connecting a User to an Event, including fields: `Id`, `UserId`, `EventId`, `SeatType` (e.g., STANDARD, VIP), and `PricePaid`.
   - Implement `BookingService` for:
     - Checking seat availability
     - Handling seat allocation
     - Applying dynamic pricing (e.g., VIP seats are 1.5x the standard ticket price)
     - Saving booking data to the database

4. **Dynamic Pricing Logic**
   - Apply dynamic pricing in `BookingService` for VIP tickets.
   - Example: VIP ticket price = `basePrice * 1.5`.

5. **Exception Handling and Validation**
   - Create a custom exception (e.g., `BookingException`) for cases like sold-out events or invalid seat types.
   - Use a global exception handler to return descriptive error responses.

### Frontend (Angular)

1. **User Authentication**
   - Set up JWT authentication in the Angular app.
   - Create login and registration components.
   - Store the JWT token in local storage and use it for API request authentication.

2. **Event List and Details View**
   - Create an `EventListComponent` to display available events.
   - Create an `EventDetailsComponent` that shows detailed information about a specific event.
   - Use Angular services to fetch event data and manage authentication tokens.

3. **Booking Component**
   - Build a `BookingComponent` where users can select seat types and book tickets.
   - Display dynamic pricing for VIP seats and show available seats.

4. **User Profile and Booking History**
   - Create a `UserProfileComponent` where users can view their booking history.
   - Allow users to view details of past bookings and possibly cancel upcoming ones if within a certain timeframe.

5. **Admin Views (Optional)**
   - Add an `AdminDashboardComponent` for managing events (create, edit, delete).
   - Allow admins to view booking statistics for each event.

## Expected Outcomes

### Backend
- The ASP.NET Core API should handle user registration, authentication, event management, and ticket booking.
- Proper error handling should provide descriptive messages for both general and user-specific errors.

### Frontend
- The Angular app should display events, manage authentication, and handle bookings.
- A user-friendly UI should show event information, booking status, and dynamically update seat availability and pricing.

## Installation

### Prerequisites

- .NET SDK (version X.X or higher)
- Node.js and npm
- Angular CLI
- SQL Server or any preferred database

### Steps to Run the Backend

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/TheEventHandler.git
   cd TheEventHandler/Backend