# Vehicle Rental System

A menu-driven vehicle rental management application written in C. It supports administrator and regular-user workflows for managing vehicles, customers, rentals, and rental payments. Records are stored locally in binary `.dat` files.

## Features

- User registration and login with administrator and regular-user roles.
- Add and list vehicles, including daily prices and availability.
- Add and list customers.
- Create rentals with a calculated total cost and expected return date.
- Cancel a rental within six hours of its recorded creation time.
- Return a vehicle after the rental balance has been paid.
- Record full or partial rental payments and view payment details.
- Administrator tools for managing users, changing passwords, and updating account status.
- Regular users see records associated with their account; administrators can view records across users.

## Requirements

- GCC or another C compiler that supports the C code in this project.
- A writable `data/` directory in the project root. The repository includes this directory and its `.dat` files.

## Build and run

Run these commands from the project root:

```sh
gcc -std=c11 -Wall -Wextra main.c -o vehicle_rental
./vehicle_rental
```

The application opens a console menu. Register a regular user from the welcome menu, then log in. Administrator options are available only when logging in with an account whose role is administrator.

## Project structure

```text
main.c              Application entry point and role-specific menus
struct/models.h     Shared user, vehicle, customer, rental, and payment structures
app/user.h          Registration, login, and user management
app/vehicle.h       Vehicle management
app/customer.h      Customer management
app/rental.h        Rental creation, listing, cancellation, and return
app/payment.h       Payment recording and payment details
app/date_handler.h  Rental date calculations
data/               Local binary record files
```

## Data storage

Application records are stored in `data/users.dat`, `data/vehicles.dat`, `data/customers.dat`, `data/rentals.dat`, and `data/payments.dat`. These files contain binary representations of the C structures, not portable text or a database format. Keep the files together with the application, back them up before making changes, and avoid editing them manually. Since the files are tied to the structure layout and compiler/platform representation, changing the models or moving data between platforms may require a data migration.

## Notes

- Passwords are stored as a simple non-cryptographic hash. This project is suitable for learning and local demonstration, not for protecting real user accounts or sensitive production data.
- Data files are local to the working directory; run the program from the project root so it can find the `data/` directory.
- No automated test suite is included in the repository.
