# Travel Booking Management System

A multi-role Java desktop application with full OOP architecture, MySQL/JDBC integration, and complete GUI supporting Passenger and Admin roles.

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [System Architecture](#system-architecture)
- [Database Schema](#database-schema)
- [Installation](#installation)
- [Usage](#usage)
- [Screenshots](#screenshots)
- [Project Structure](#project-structure)
- [Contributors](#contributors)

## Overview

Travel Booking Management System is a comprehensive travel booking management system designed to streamline the process of booking bus and train tickets. The application supports two main user roles: Passengers and Administrators, each with specific functionalities tailored to their needs.

## Features

### Passenger Features
- **User Authentication**: Secure login and registration system
- **Ticket Booking**: Book bus and train tickets with seat selection
- **Booking History**: View and manage past bookings
- **Ticket Management**: Cancel bookings and download tickets
- **Profile Management**: Update personal information and change password
- **Review System**: Submit and view reviews for travel experiences

### Admin Features
- **User Management**: Add, edit, and remove users from the system
- **Schedule Management**: Create and manage travel schedules
- **Reservation Management**: View and manage all bookings
- **Data Management**: Import and export system data
- **Reports Generation**: Generate various system reports
- **System Statistics**: View real-time system analytics

## Technologies Used

- **Programming Language**: Java 
- **GUI Framework**: Java Swing
- **Database**: MySQL 8.0
- **Database Connectivity**: JDBC
- **IDE**: Apache NetBeans
- **Design Pattern**: MVC (Model-View-Controller)
- **Architecture**: Object-Oriented Programming (OOP)

## System Architecture

The application follows a three-tier architecture:

```
┌─────────────────────────────────────────────────────────────────────────┐
│                        Presentation Layer (UI)                          │
│  - Login Frames  │  - Dashboard Frames  │  - Booking Frames  │          │
│  - Management Frames                                                    │
└─────────────────────────────────────────────────────────────────────────┘
                                    ↕
┌─────────────────────────────────────────────────────────────────────────┐
│                        Business Logic Layer                             │
│  - User (Admin, Passenger)  │  - Ticket (Standard, VIP)  │              │
│  - Booking, Transaction, Review                                         │
└─────────────────────────────────────────────────────────────────────────┘
                                    ↕
┌─────────────────────────────────────────────────────────────────────────┐
│                      Data Access Layer (DAO)                            │
│  - UserDAO  │  - TicketDAO  │  - TransactionDAO  │  - ReviewDAO         │
└─────────────────────────────────────────────────────────────────────────┘
                                    ↕
┌─────────────────────────────────────────────────────────────────────────┐
│                          MySQL Database                                 │
│  - users, tickets, bookings  │  - schedules, reviews                    │
└─────────────────────────────────────────────────────────────────────────┘
```



## Database Schema

### Main Tables

**users**
- `id` (INT, Primary Key, Auto Increment)
- `name` (VARCHAR)
- `email` (VARCHAR, Unique)
- `password` (VARCHAR)
- `phone` (VARCHAR)
- `role` (ENUM: 'Admin', 'Passenger')

**tickets**
- `ticket_id` (INT, Primary Key, Auto Increment)
- `passenger_id` (INT, Foreign Key → users.id)
- `type` (ENUM: 'Standard', 'VIP')
- `price` (DECIMAL)
- `seat_number` (INT)

**bookings**
- `booking_id` (INT, Primary Key, Auto Increment)
- `passenger_id` (INT, Foreign Key → users.id)
- `ticket_id` (INT, Foreign Key → tickets.ticket_id)
- `status` (VARCHAR)
- `booking_date` (DATE)

**schedules**
- `schedule_id` (INT, Primary Key, Auto Increment)
- `transportation_type` (ENUM: 'Bus', 'Train')
- `departure_time` (TIME)
- `arrival_time` (TIME)
- `departure_point` (VARCHAR)
- `destination` (VARCHAR)
- `available_seats` (INT)

**reviews**
- `review_id` (INT, Primary Key, Auto Increment)
- `rating` (INT)
- `comment` (TEXT)
- `user_id` (INT, Foreign Key → users.id)

## 📥 Installation

### Prerequisites
- Java Development Kit (JDK) 8 or higher
- MySQL Server 8.0 or higher
- Apache NetBeans IDE (recommended) or any Java IDE
- MySQL Connector/J (JDBC Driver)

### Default Login Credentials

**Admin Account:**
- Email: `admin1@example.com`
- Password: `adminpass1`

**Passenger Account:**
- Email: `fatimah@gmail.com`
- Password: `pass123`

## Usage

### For Passengers

1. **Register/Login**: Create an account or login with existing credentials
2. **Book Tickets**: 
   - Select travel type (Bus/Train)
   - Choose departure and arrival stations
   - Select date and time
   - Choose ticket type (Standard/VIP)
   - Confirm booking and proceed to payment
3. **View History**: Access your booking history from the dashboard
4. **Manage Bookings**: Cancel or download tickets
5. **Submit Reviews**: Rate and review your travel experience

### For Administrators

1. **Login**: Use admin credentials to access the admin dashboard
2. **Manage Users**: Add, edit, or remove user accounts
3. **Manage Schedules**: Create and update travel schedules
4. **View Reservations**: Monitor all bookings in the system
5. **Generate Reports**: Create system reports for analysis
6. **Manage Data**: Import/export data for backup purposes

## 📸 Screenshots

### Login Screen
<img width="1604" height="861" alt="image" src="https://github.com/user-attachments/assets/20997f7a-dde7-40ce-a4f3-81248f760274" />


### Passenger Dashboard
<img width="981" height="737" alt="image" src="https://github.com/user-attachments/assets/074b3354-16a1-48d6-a782-121c1b9a2fb9" />


### Ticket Booking
<img width="605" height="735" alt="image" src="https://github.com/user-attachments/assets/63ffcd98-85dd-4b8d-b487-532d693faa70" />


### Booking History
<img width="1107" height="610" alt="image" src="https://github.com/user-attachments/assets/df6a5f27-08d8-4b16-9047-30c02312d931" />


### Admin Dashboard
<img width="982" height="736" alt="image" src="https://github.com/user-attachments/assets/6b60cf20-6b56-4e2f-ab93-cd24d5f74576" />


## Project Structure

```
TravelEase/
├── src/
│   └── oopproject/
│       ├── model/
│       │   ├── User.java
│       │   ├── Admin.java
│       │   ├── Passenger.java
│       │   ├── Ticket.java
│       │   ├── StandardTicket.java
│       │   ├── VIPTicket.java
│       │   ├── Booking.java
│       │   ├── Transaction.java
│       │   └── Review.java
│       ├── dao/
│       │   ├── UserDAO.java
│       │   ├── TicketDAO.java
│       │   ├── TransactionDAO.java
│       │   └── ReviewDAO.java
│       ├── ui/
│       │   ├── main.java
│       │   ├── AdminLoginFrame.java
│       │   ├── PassengerLoginFrame.java
│       │   ├── RegisterFrame.java
│       │   ├── AdminDashboardFrame.java
│       │   ├── PassengerDashboardFrame.java
│       │   ├── TicketBookingFrame.java
│       │   ├── BookingHistoryFrame.java
│       │   ├── PaymentFrame.java
│       │   └── UserProfileFrame.java
│       ├── DBConnection.java
│       └── DatabaseInitializer.java
├── lib/
│   └── mysql-connector-java-x.x.xx.jar
├── screenshots/
├── database/
│   └── schema.sql
└── README.md
```


