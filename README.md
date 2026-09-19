# Tiket.id — Flight Ticket Booking System

Tiket.id is a web-based flight ticket booking system developed as a practical portfolio and learning project.

The application is designed to simulate the complete flight booking process, starting from user registration and flight search to booking, simulated payment, booking history, and electronic ticket management.

This project is a reimplementation of an earlier programming project, rebuilt from scratch with a redesigned database structure and application architecture.

## Project Goals

This project is developed with the following goals:

- Build a practical web-based flight ticket booking system from scratch.
- Strengthen skills in PHP web development and MySQL database management.
- Practice designing and implementing a relational database.
- Understand the implementation of user authentication, booking workflows, and transaction processes.
- Apply structured programming and database concepts in a real-world application scenario.
- Develop a practical portfolio project that demonstrates both technical and problem-solving skills.

## Key Features

### User Authentication

- User registration
- User login and logout
- Session-based authentication
- Password hashing for secure password storage

### Flight Search

- Search flights by departure airport
- Search flights by arrival airport
- Search flights by departure date
- Display available flights with flight details and ticket prices

### Flight Booking

- Select an available flight
- Enter passenger information
- Create a unique booking code
- Calculate and store the total booking price
- Manage booking status
- Update flight seat availability after a successful booking

### Simulated Payment

- Simulated payment process for flight bookings
- Support for bank transfer and QR payment
- Payment status management
- Unique payment reference for each transaction

### Booking History

- View previously created bookings
- Display booking details and status
- Access the corresponding e-ticket from booking history

### E-Ticket

- Display electronic ticket directly on the website
- Show booking code, passenger, flight, route, date, time, price, and booking status
- No PDF generation required

## Technology Stack

### Frontend

- HTML
- CSS
- JavaScript

### Backend

- PHP

### Database

- MySQL
- phpMyAdmin

### Development Environment

- XAMPP
- Visual Studio Code

### Version Control

- Git
- GitHub

## Application Flow

The application follows a structured flight booking workflow:

```text
User Registration
       ↓
User Login
       ↓
Flight Search
       ↓
Select Flight
       ↓
Passenger Information
       ↓
Checkout
       ↓
Simulated Payment
       ↓
Booking Confirmation
       ↓
E-Ticket
       ↓
Booking History
```

### Flight Search Flow

Users can search for available flights by selecting:

- Departure airport
- Arrival airport
- Departure date

The system then displays available flights that match the selected criteria.

### Booking Flow

After selecting a flight, the user provides passenger information and proceeds to checkout.

The system creates a unique booking code and stores the booking information in the database.

### Payment Flow

The payment process is simulated for educational purposes.

Users can select an available simulated payment method and confirm the payment.

After a successful payment confirmation:

```text
Payment Status: PAID
        ↓
Booking Status: CONFIRMED
        ↓
E-Ticket Available
```

### Booking History Flow

Users can access their previous bookings through the booking history page.

```text
Login
  ↓
Booking History
  ↓
Select Booking
  ↓
View E-Ticket
```

## Database Design

The system uses a relational MySQL database to manage users, airports, flights, bookings, and simulated payments.

### Main Database Tables

The database consists of the following main tables:

| Table | Description |
|---|---|
| `users` | Stores user account and authentication information |
| `airports` | Stores airport information such as airport code, name, city, and province |
| `flights` | Stores flight schedules, routes, prices, and seat availability |
| `bookings` | Stores flight booking and passenger information |
| `payments` | Stores simulated payment information related to each booking |

### Table Relationships

The main relationships between the tables are:

```text
Users
  │
  │ 1:N
  ↓
Bookings
  │
  ├──────── N:1 ────────→ Flights
  │                         │
  │                         ├──→ Departure Airport
  │                         │
  │                         └──→ Arrival Airport
  │
  └──────── 1:1 ────────→ Payments
```

### Users

The `users` table stores user account information required for authentication and user management.

Main information includes:

- User ID
- Username
- Password
- Full name
- Email
- Phone number
- User role
- Account creation date

### Airports

The `airports` table stores airport information used as departure and arrival locations for flights.

Main information includes:

- Airport ID
- Airport code
- Airport name
- City
- Province

### Flights

The `flights` table stores available flight schedules and related information.

Main information includes:

- Flight ID
- Flight number
- Airline
- Departure airport
- Arrival airport
- Departure date
- Departure time
- Arrival time
- Ticket price
- Available seats

### Bookings

The `bookings` table stores information about flight reservations made by users.

Main information includes:

- Booking ID
- Unique booking code
- User ID
- Flight ID
- Passenger name
- Passenger identification number
- Booking date
- Total price
- Booking status

Each booking represents one passenger reservation.

### Payments

The `payments` table stores simulated payment information for a booking.

Main information includes:

- Payment ID
- Booking ID
- Payment method
- Payment amount
- Payment status
- Payment date
- Payment reference

The payment system is simulated and does not connect to a real payment gateway.

### Database Design Principles

The database is designed using relational database principles to maintain data consistency and reduce unnecessary data duplication.

Foreign keys are used to establish relationships between related tables, while unique constraints are applied to values such as usernames, booking codes, and payment references.

## Project Structure

The project is organized into separate directories to keep the application structure clear and maintainable.

```text
tiket-id-flight-booking-system/
│
├── assets/
│   ├── css/
│   │   └── style.css
│   │
│   ├── js/
│   │   └── script.js
│   │
│   └── images/
│
├── config/
│   └── database.php
│
├── includes/
│   ├── header.php
│   ├── footer.php
│   ├── auth.php
│   └── functions.php
│
├── auth/
│   ├── login.php
│   ├── register.php
│   └── logout.php
│
├── flights/
│   ├── search.php
│   ├── results.php
│   └── detail.php
│
├── booking/
│   ├── passenger.php
│   ├── checkout.php
│   ├── process.php
│   └── confirmation.php
│
├── payment/
│   ├── payment.php
│   └── process.php
│
├── ticket/
│   └── ticket.php
│
├── history/
│   └── booking-history.php
│
├── database/
│   └── tiket_id.sql
│
├── index.php
└── README.md
```

### Directory Description

#### `assets/`

Contains static files used by the application, including CSS, JavaScript, and image resources.

#### `config/`

Contains configuration files required by the application.

The `database.php` file is responsible for establishing the connection between the PHP application and the MySQL database.

#### `includes/`

Contains reusable PHP components and helper functions used throughout the application.

Examples include:

- Header and footer components
- Authentication checking
- Reusable application functions

#### `auth/`

Contains pages related to user authentication.

Main functionality includes:

- User registration
- User login
- User logout

#### `flights/`

Contains functionality related to flight searching and flight information.

Main functionality includes:

- Flight search
- Search results
- Flight details

#### `booking/`

Contains the main flight booking process.

The booking process includes:

- Passenger information
- Checkout
- Booking processing
- Booking confirmation

#### `payment/`

Contains the simulated payment process.

The payment module handles:

- Payment method selection
- Payment confirmation
- Payment status processing

No real payment gateway is connected to this project.

#### `ticket/`

Contains the e-ticket display functionality.

Users can view their confirmed booking and flight information through the e-ticket page.

#### `history/`

Contains the booking history functionality.

Users can view their previous bookings and access the corresponding e-ticket.

#### `database/`

Contains the SQL database structure and sample data required to set up the project.

The `tiket_id.sql` file contains the database schema and initial data.

#### `index.php`

Serves as the main entry point of the application and provides access to the main flight booking system.

### Application Architecture

The project uses a simple modular PHP structure where different application features are separated into their respective directories.

```text
User Interface
      ↓
PHP Application
      ↓
Business Logic
      ↓
MySQL Database
```

This structure is designed to make the project easier to understand, develop, maintain, and extend.

## Security & Data Handling

The application applies basic security practices to protect user accounts, booking information, and database operations.

### Password Security

User passwords are not stored as plain text.

Passwords are securely hashed before being stored in the database and verified during the login process.

### User Authentication

The application uses session-based authentication to manage logged-in users.

Protected pages require users to be authenticated before accessing features such as:

- Flight booking
- Booking history
- E-ticket management

### Database Security

The application uses prepared statements when interacting with the MySQL database to reduce the risk of SQL injection.

User input is validated and handled carefully before being processed or stored in the database.

### Input Validation

The application validates important user inputs such as:

- Username
- Password
- Email
- Passenger information
- Flight search parameters
- Booking information
- Payment information

Invalid or incomplete data should be rejected before being processed.

### Booking Data Integrity

The system maintains relationships between users, flights, bookings, and payments using primary keys and foreign keys.

Booking and payment records are linked using their respective identifiers to maintain data consistency.

### Payment Simulation

The payment functionality in this project is simulated for educational purposes.

The application does not process real financial transactions and does not store real payment credentials such as credit card numbers, bank passwords, or other sensitive financial information.

### Data Handling

The project is intended for educational and portfolio purposes.

Any user, passenger, flight, and payment data used during development or testing should be fictional or sample data.

## Installation & Setup

Follow the steps below to run the Tiket.id flight booking system in a local development environment.

### Requirements

Before running the application, make sure the following software is installed:

- XAMPP
- PHP
- MySQL
- phpMyAdmin
- Visual Studio Code
- Git

### 1. Clone the Repository

Clone this repository to the local development environment:

```bash
git clone https://github.com/MohAdityaSirojulHilmi/tiket-id-flight-booking-system.git
```

Navigate to the project directory:

```bash
cd tiket-id-flight-booking-system
```

### 2. Move the Project to XAMPP

Copy the project folder into the XAMPP `htdocs` directory.

Example:

```text
C:\xampp\htdocs\tiket-id-flight-booking-system
```

### 3. Start XAMPP

Open the XAMPP Control Panel and start the following services:

```text
Apache
MySQL
```

Both services must be running before accessing the application.

### 4. Create the Database

Open phpMyAdmin through:

```text
http://localhost/phpmyadmin
```

Create a new database named:

```text
tiket_id
```

### 5. Import the Database

Import the SQL file provided in the project:

```text
database/tiket_id.sql
```

The SQL file contains the database structure and initial sample data required by the application.

### 6. Configure the Database Connection

Open:

```text
config/database.php
```

Configure the database connection according to the local MySQL environment.

Example configuration:

```php
$host = "localhost";
$dbname = "tiket_id";
$username = "root";
$password = "";
```

The default XAMPP MySQL configuration commonly uses the `root` username with an empty password for local development.

### 7. Run the Application

After Apache and MySQL are running, open the application through:

```text
http://localhost/tiket-id-flight-booking-system/
```

The application should display the Tiket.id homepage.

### Local Development Flow

```text
Install XAMPP
      ↓
Start Apache & MySQL
      ↓
Create MySQL Database
      ↓
Import tiket_id.sql
      ↓
Configure database.php
      ↓
Open localhost
      ↓
Run Tiket.id
```

### Troubleshooting

If the application cannot connect to the database, check:

- Apache is running.
- MySQL is running.
- The database name is correct.
- The MySQL username and password are correct.
- The database connection configuration matches the local environment.

If the application cannot be accessed through localhost, make sure the project is located inside the XAMPP `htdocs` directory.

## Usage

The following steps describe how to use the Tiket.id flight booking system.

### 1. User Registration

New users must create an account before using the flight booking system.

The registration process requires basic account information such as:

- Username
- Password
- Full name
- Email
- Phone number

After successful registration, the user can proceed to the login page.

### 2. User Login

Users can log in using their registered username and password.

After successful authentication, the user is redirected to the main application page.

### 3. Search for Flights

Users can search for available flights by providing:

- Departure airport
- Arrival airport
- Departure date

The system displays available flights that match the selected search criteria.

### 4. Select a Flight

Users can select one of the available flights from the search results.

The system displays relevant flight information, including:

- Airline
- Flight number
- Departure airport
- Arrival airport
- Departure date
- Departure time
- Arrival time
- Ticket price
- Available seats

### 5. Enter Passenger Information

After selecting a flight, users must enter the required passenger information.

Each booking represents one passenger.

### 6. Checkout

The system displays the selected flight and passenger information before the booking is confirmed.

The total booking price is calculated based on the selected flight.

Users can review the booking information before proceeding to payment.

### 7. Simulated Payment

Users can select one of the available simulated payment methods:

- Bank transfer
- QR payment

The payment process is simulated for educational purposes and does not involve a real payment gateway.

After the payment is successfully confirmed, the booking status is updated to:

```text
CONFIRMED
```

### 8. View E-Ticket

After a successful payment, users can view their electronic ticket directly through the website.

The e-ticket contains information such as:

- Booking code
- Passenger name
- Airline
- Flight number
- Departure airport
- Arrival airport
- Departure date
- Departure time
- Arrival time
- Ticket price
- Booking status

### 9. Booking History

Users can access their previous bookings through the booking history page.

The booking history allows users to:

- View previous bookings
- Check booking status
- View booking details
- Access the corresponding e-ticket

### Complete User Flow

```text
Register
   ↓
Login
   ↓
Search Flight
   ↓
Select Flight
   ↓
Passenger Information
   ↓
Checkout
   ↓
Simulated Payment
   ↓
Booking Confirmation
   ↓
View E-Ticket
   ↓
Booking History
```

## Future Improvements

The current version of Tiket.id focuses on the core flight booking workflow.

Several features can be added in future development to improve the functionality, usability, security, and scalability of the application.

### Planned Improvements

#### Admin Dashboard

Develop an administrative dashboard for managing:

- Users
- Airports
- Flights
- Bookings
- Payments

#### Flight Management

Add functionality for administrators to:

- Add new flights
- Edit flight schedules
- Update ticket prices
- Manage available seats
- Remove inactive flights

#### Advanced Flight Search

Improve the flight search functionality by adding filters such as:

- Airline
- Price range
- Departure time
- Arrival time
- Available seats

#### Real Payment Gateway

Replace the simulated payment system with a real payment gateway integration.

Possible payment methods could include:

- Bank transfer
- QRIS
- E-wallets
- Credit or debit cards

#### E-Ticket Improvements

Improve the e-ticket system by adding:

- QR code generation
- Printable e-tickets
- PDF e-ticket generation
- Downloadable tickets

#### Booking Cancellation

Add a booking cancellation feature that allows users to cancel eligible bookings and automatically update the corresponding seat availability.

#### Email Notification

Implement email notifications for important booking events, such as:

- Registration confirmation
- Booking confirmation
- Payment confirmation
- Booking cancellation

#### Improved Security

Further strengthen application security by implementing additional measures such as:

- CSRF protection
- Rate limiting
- More advanced input validation
- Secure session configuration
- Improved access control

#### Responsive User Interface

Improve the user interface to provide a better experience across:

- Desktop
- Tablet
- Mobile devices

#### Application Architecture

The application can be further refactored into a more structured architecture, such as the MVC (Model-View-Controller) pattern, to improve maintainability and scalability as the project grows.

### Long-Term Development

The long-term goal is to transform Tiket.id from a learning and portfolio project into a more complete flight booking application with improved functionality, security, usability, and scalability.

## Project Status

Tiket.id is currently under active development.

This project is a reimplementation of an earlier flight ticket booking project that was developed as part of a programming learning project.

The original source code is no longer available. Therefore, the current version is being rebuilt from scratch based on the original project concept, remembered functionality, and a redesigned database and application structure.

### Current Development Progress

| Component | Status |
|---|---|
| Project documentation | Completed |
| Project structure | Completed |
| Database design | Completed |
| Application flow | Completed |
| Security planning | Completed |
| Development environment setup | In progress |
| Database implementation | Planned |
| Backend development | Planned |
| Frontend development | Planned |
| Authentication system | Planned |
| Flight search system | Planned |
| Booking system | Planned |
| Simulated payment system | Planned |
| E-ticket system | Planned |
| Booking history | Planned |

### Development Approach

The project is being developed incrementally.

The development process focuses on implementing and testing each major component before moving to the next stage.

The planned development sequence is:

```text
Environment Setup
       ↓
Database Implementation
       ↓
Database Connection
       ↓
User Authentication
       ↓
Flight Management
       ↓
Flight Search
       ↓
Booking System
       ↓
Simulated Payment
       ↓
E-Ticket
       ↓
Booking History
       ↓
Testing & Refinement
```

As development progresses, the project documentation will be updated to reflect the actual implementation and current project status.

## Learning Outcomes

Developing Tiket.id provides practical experience in web development, database management, and application logic.

Through this project, the following skills and concepts are practiced:

### Web Development

- Building a web application using PHP
- Creating interactive web pages using HTML, CSS, and JavaScript
- Organizing a PHP application into modular components
- Implementing user interaction and application workflows

### Database Management

- Designing a relational database using MySQL
- Creating tables, primary keys, and foreign keys
- Establishing relationships between related entities
- Managing data using SQL
- Using phpMyAdmin for database administration

### Backend Development

- Connecting PHP applications to MySQL
- Processing user input
- Implementing authentication and session management
- Handling booking and payment workflows
- Managing application logic and database transactions

### Software Development Practices

- Structuring a project into logical modules
- Applying basic security practices
- Validating user input
- Debugging application errors
- Testing application functionality
- Using Git and GitHub for version control

### Problem Solving

The project also provides practical experience in designing solutions for a real-world application scenario, including:

- User authentication
- Flight searching
- Booking management
- Seat availability management
- Payment status management
- Booking confirmation
- E-ticket generation and display

### Overall Learning

The main objective of this project is to strengthen practical programming and database development skills by building a complete application from scratch.

The project also demonstrates the ability to translate a real-world process into a structured software system consisting of user interfaces, application logic, and relational database components.

## Screenshots

Screenshots of the application will be added as the development progresses.

### Homepage

The homepage will provide access to the main flight search functionality.

> Screenshot will be added after the homepage implementation is completed.

### Flight Search

The flight search page will allow users to search for available flights based on departure airport, arrival airport, and departure date.

> Screenshot will be added after the flight search functionality is implemented.

### Flight Details

The flight details page will display information about the selected flight before the user proceeds with the booking process.

> Screenshot will be added after the flight details page is implemented.

### Checkout

The checkout page will allow users to review their flight and passenger information before proceeding to payment.

> Screenshot will be added after the checkout functionality is implemented.

### Simulated Payment

The payment page will provide simulated payment methods and display the payment status of the booking.

> Screenshot will be added after the payment functionality is implemented.

### E-Ticket

The e-ticket page will display the confirmed booking and flight information.

> Screenshot will be added after the e-ticket functionality is implemented.

### Booking History

The booking history page will allow users to view their previous bookings and access their e-tickets.

> Screenshot will be added after the booking history functionality is implemented.

## Author

**Moh. Aditya Sirojul Hilmi, S.Mat**

Mathematics graduate with an interest in Data Science, Data Analysis, Artificial Intelligence, Machine Learning, and software development.

This project is developed as part of a personal learning and portfolio journey to strengthen practical programming, database management, and problem-solving skills.

### Areas of Interest

- Data Science
- Data Analysis
- Artificial Intelligence
- Machine Learning
- Python
- SQL
- Web Development
- Database Management

### GitHub

More projects and learning activities are available on my GitHub profile:

- GitHub: [Your GitHub Profile](https://github.com/MohAdityaSirojulHilmi)

## License

This project is currently developed as a personal learning and portfolio project.

No open-source license has been applied to this repository at this time.

The source code is provided for educational and portfolio purposes.

## Project Notes

Tiket.id is a reimplementation of an earlier programming project that has been rebuilt from scratch.

The current implementation, database structure, application architecture, and source code are newly developed based on the original project concept and remembered functionality.

The project is intended to demonstrate practical skills in PHP web development, MySQL database management, relational database design, authentication, booking workflows, and application development.

This project is not affiliated with or officially connected to any real-world company or commercial ticket booking platform using a similar name.
