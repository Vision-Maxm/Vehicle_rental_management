# 🚗 Vehicle Rental Management System

> **A Python command-line application for managing a vehicle rental fleet.**  
> Add cars and vans, manage rentals and returns, estimate rental charges, search vehicles, and save fleet records using CSV storage.

---

## 📌 Project Overview

The **Vehicle Rental Management System** is a menu-driven Python project that simulates common operations in a small vehicle rental business. It supports two vehicle categories—**Cars** and **Vans**—and tracks whether each vehicle is available or rented. The application calculates rental charges based on the vehicle type and rental duration, displays vehicle information, and saves records to a CSV file so the fleet can be loaded again in a later session.

This project is intended for learning and demonstration. It is **not a complete commercial rental or payment platform**.

## ✨ Key Features

- 🚘 **Add Cars** — Register cars with vehicle ID, make, model, daily rate, and number of seats.
- 🚐 **Add Vans** — Register vans with vehicle ID, make, model, daily rate, and cargo capacity.
- 📅 **Rent a Vehicle** — Assign an available vehicle to a customer and calculate an estimated rental charge.
- 🔄 **Return a Vehicle** — Mark a rented vehicle as available and calculate the final rental settlement.
- 🔎 **Search Vehicles** — Find a vehicle by its unique ID.
- ✅ **Display Available Vehicles** — Show only vehicles that are not currently rented.
- 🚗 **Display Full Fleet** — View all registered vehicles and their current status.
- 💾 **Save Fleet Records** — Store vehicle details and rental status in `vehicles.csv`.
- 🛡️ **Custom Exceptions** — Handle missing vehicles, duplicate IDs, unavailable vehicles, invalid rental durations, and invalid returns.
- 🧱 **Object-Oriented Design** — Demonstrates abstraction, inheritance, encapsulation, and method overriding.

## 🛠️ Technologies Used

- **Python 3.9+**
- `csv` — Read and write vehicle records
- `os` — Resolve the data file location and check whether it exists
- `abc` — Define an abstract base class for vehicles

All imports used in this project are from Python's standard library. No third-party packages are required.

## 📁 Project Structure

```text
vehicle-rental-management-system/
├── vehicle_rental.py   # Python source code (suggested filename)
├── vehicles.csv        # Fleet records; created when records are saved
└── README.md           # Project documentation
```

> **Note:** `vehicle_rental.py` is a suggested filename. If your script has another name, use that name in the run command.

## ⚙️ Getting Started

### 1. Install Python

Install Python **3.9 or newer** from [python.org](https://www.python.org/downloads/).

Verify your installation:

```bash
python --version
```

On some systems, use:

```bash
python3 --version
```

### 2. Prepare the Project Folder

Save your Python script and this README in the same project folder. The application stores `vehicles.csv` in the directory containing the Python script.

### 3. Run the Application

If your file is named `vehicle_rental.py`, run:

```bash
python vehicle_rental.py
```

Replace the filename with your actual script name if it differs.

## 🚀 How to Use

When the application starts, it displays the following menu:

```text
=== VEHICLE RENTAL MANAGEMENT SYSTEM ===
1. Add Car
2. Add Van
3. Rent Vehicle
4. Return Vehicle & Settle Bill
5. Search Vehicle
6. Display Available Vehicles
7. Display Full Fleet
8. Save Records
9. Save & Exit
```

Choose an option by entering its number.

| Option | Action | Description |
|---|---|---|
| `1` | Add Car | Enter the vehicle ID, make, model, daily rate, and number of seats |
| `2` | Add Van | Enter the vehicle ID, make, model, daily rate, and cargo capacity in tons |
| `3` | Rent Vehicle | Enter the vehicle ID, customer name, and rental duration |
| `4` | Return Vehicle | Enter the vehicle ID and actual days used to calculate the settlement |
| `5` | Search Vehicle | Find and display a vehicle by ID |
| `6` | Display Available Vehicles | List only vehicles currently available |
| `7` | Display Full Fleet | List all vehicles and their status |
| `8` | Save Records | Save the current fleet to CSV |
| `9` | Save & Exit | Save the records and close the application |

## 💵 How Rental Charges Are Calculated

The program calculates rental charges according to the vehicle type and the number of days.

### 🚘 Cars

Cars include a daily insurance fee of **₹200 per day**.

**Formula:**

```text
Total rental = (Daily rate × Number of days) + (₹200 × Number of days)
```

### 🚐 Vans

Vans include a capacity surcharge of **₹350 per ton per day**.

**Formula:**

```text
Total rental = (Daily rate × Number of days)
             + (Cargo capacity in tons × ₹350 × Number of days)
```

### 🧮 Example

For a car with a daily rental rate of ₹1,000 rented for 2 days:

```text
Base rental:       ₹1,000 × 2 = ₹2,000
Insurance:           ₹200 × 2 =   ₹400
Estimated total:                  ₹2,400
```

*This example illustrates the formula implemented in the code; actual totals depend on the vehicle details and duration entered.*

## 💾 Data Storage

The application saves fleet data in a CSV file named **`vehicles.csv`**. The file includes the following columns:

```csv
type,id,make,model,rate,spec,is_rented,rented_by
```

| Column | Meaning |
|---|---|
| `type` | Vehicle category: `Car` or `Van` |
| `id` | Unique vehicle ID |
| `make` | Manufacturer or make |
| `model` | Vehicle model |
| `rate` | Daily rental rate |
| `spec` | Number of seats for a car or cargo capacity for a van |
| `is_rented` | Whether the vehicle is currently rented |
| `rented_by` | Customer name when rented |

The program attempts to load existing records when it starts. Use **Save Records** or **Save & Exit** to write the current fleet to the CSV file.

## 🧠 Python Concepts Demonstrated

| Concept | How it is used |
|---|---|
| **Classes and Objects** | Models vehicles, cars, vans, and rental management |
| **Abstraction** | `Vehicle` defines the common interface for all vehicle types |
| **Inheritance** | `Car` and `Van` inherit from `Vehicle` |
| **Encapsulation** | Uses protected and private-style attributes for vehicle data |
| **Polymorphism** | Each vehicle type implements its own `calculate_rental()` and `get_details()` methods |
| **Properties** | Exposes vehicle information through getter properties |
| **Custom Exceptions** | Represents common rental-operation errors with specific exception classes |
| **CSV File Handling** | Persists vehicle inventory and rental status |
| **Input Validation** | Handles invalid numeric input and invalid menu choices |

## 🖥️ Example Interaction

An example of adding a car might look like this:

```text
=== VEHICLE RENTAL MANAGEMENT SYSTEM ===
1. Add Car
2. Add Van
3. Rent Vehicle
4. Return Vehicle & Settle Bill
5. Search Vehicle
6. Display Available Vehicles
7. Display Full Fleet
8. Save Records
9. Save & Exit

Enter choice (1-9): 1
Vehicle ID (e.g. C01): C01
Make (e.g. Maruti): Maruti
Model (e.g. Swift): Swift
Daily Rental Rate (₹): 1000
Number of Seats: 5
✓ Car 'Maruti Swift' added successfully.
```

*This is an illustrative example. Your output will depend on the information entered.*

## ⚠️ Notes & Limitations

- This is an educational command-line application, not a complete commercial rental system.
- Rental records are stored locally in a CSV file; there is no database, login system, or online booking service.
- The program estimates rental charges but does not process payments.
- Vehicle information such as rates, seats, and cargo capacity is not fully validated for business-specific limits.
- Save the records before closing if you want to preserve the latest changes.
- The current design does not maintain a separate historical log of completed rentals.

## 🔮 Future Enhancements

Potential improvements include:

- 🧾 Generate printable rental invoices and receipts.
- 📆 Store rental start and end dates.
- 🗂️ Add customer records and rental history.
- 🔐 Add user authentication and administrator access.
- 🗄️ Replace CSV storage with SQLite or another database.
- 🖥️ Create a graphical interface using Tkinter or a web framework.
- 🧪 Add automated tests for rental calculations and error handling.
- 💳 Integrate a secure payment workflow in a properly designed production system.

## 🎓 Learning Outcomes

This project provides hands-on practice with:

- Designing a menu-driven Python application.
- Applying OOP concepts to a real-world-style scenario.
- Creating reusable base and derived classes.
- Validating operations with custom exceptions.
- Reading and writing structured data using CSV.
- Implementing rental calculations and vehicle availability management.

## 👨‍💻 Author

**Your Name**  
*Python / Machine Learning Intern*

> Replace **Your Name** with your preferred name before publishing.

---

⭐ **If you find this project useful, consider starring the repository!**

Built with 🐍 Python and a passion for learning.
