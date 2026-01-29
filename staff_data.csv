import csv
import os


class EmployeeManager:
    def __init__(self, filename="employees.csv"):
        self.filename = filename
        self.employees = {}
        self.load_from_csv()

    def load_from_csv(self):
        if not os.path.exists(self.filename):
            return

        with open(self.filename, mode="r", newline="", encoding="utf-8") as file:
            reader = csv.DictReader(file)
            for row in reader:
                self.employees[row["ID"]] = row

    def save_to_csv(self):
        with open(self.filename, mode="w", newline="", encoding="utf-8") as file:
            fieldnames = ["ID", "Name", "Position", "Salary", "Email"]
            writer = csv.DictWriter(file, fieldnames=fieldnames)
            writer.writeheader()
            for emp in self.employees.values():
                writer.writerow(emp)

    def add_employee(self):
        emp_id = input("Enter ID: ")

        if emp_id in self.employees:
            print("Employee ID already exists.")
            return

        name = input("Enter Name: ")
        position = input("Enter Position: ")

        salary = input("Enter Salary: ")
        if not salary.isdigit():
            print("Salary must be a number.")
            return

        email = input("Enter Email: ")

        self.employees[emp_id] = {
            "ID": emp_id,
            "Name": name,
            "Position": position,
            "Salary": salary,
            "Email": email
        }

        self.save_to_csv()
        print("Employee added successfully.")

    def view_employees(self):
        if not self.employees:
            print("No employees found.")
            return

        for emp in self.employees.values():
            print(emp)

    def search_employee(self):
        emp_id = input("Enter Employee ID: ")
        if emp_id in self.employees:
            print(self.employees[emp_id])
        else:
            print("Employee not found.")

    def update_employee(self):
        emp_id = input("Enter Employee ID to update: ")

        if emp_id not in self.employees:
            print("Employee not found.")
            return

        emp = self.employees[emp_id]

        name = input(f"New Name ({emp['Name']}): ")
        position = input(f"New Position ({emp['Position']}): ")
        salary = input(f"New Salary ({emp['Salary']}): ")
        email = input(f"New Email ({emp['Email']}): ")

        if name:
            emp["Name"] = name
        if position:
            emp["Position"] = position
        if salary:
            if salary.isdigit():
                emp["Salary"] = salary
            else:
                print("Invalid salary.")
                return
        if email:
            emp["Email"] = email

        self.save_to_csv()
        print("Employee updated successfully.")

    def delete_employee(self):
        emp_id = input("Enter Employee ID to delete: ")

        if emp_id in self.employees:
            del self.employees[emp_id]
            self.save_to_csv()
            print("Employee deleted successfully.")
        else:
            print("Employee not found.")

    def menu(self):
        while True:
            print("\n1. Add Employee")
            print("2. View All Employees")
            print("3. Update Employee")
            print("4. Delete Employee")
            print("5. Search Employee")
            print("6. Exit")

            choice = input("Choose an option: ")

            if choice == "1":
                self.add_employee()
            elif choice == "2":
                self.view_employees()
            elif choice == "3":
                self.update_employee()
            elif choice == "4":
                self.delete_employee()
            elif choice == "5":
                self.search_employee()
            elif choice == "6":
                print("Goodbye!")
                break
            else:
                print("Invalid choice.")


if __name__ == "__main__":
    manager = EmployeeManager()
    manager.menu()
