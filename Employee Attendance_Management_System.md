employees = {
    101: ("Alice Johnson", "HR"),
    102: ("Bob Smith", "IT"),
    103: ("Charlie Brown", "Finance"),
    104: ("David White", "IT"),
    105: ("Eve Black", "Marketing")
}

attendance_records = []

def mark_attendance(emp_id, date, status):
    attendance_records.append((emp_id, date, status))
    print(f"Attendance marked for Employee {emp_id}: {status}")

def search_attendance(emp_id):
    print(f"\nSearching Attendance for Employee ID: {emp_id}")
    for record in attendance_records:
        if record[0] == emp_id:
            print(f"Date: {record[1]} \nStatus: {record[2]}")

def attendance_summary():
    summary = {emp_id: [0, 0] for emp_id in employees}
    for emp_id, _, status in attendance_records:
        summary[emp_id][1] += 1
        if status == "Present":
            summary[emp_id][0] += 1
    
    print("\nAttendance Summary:")
    for emp_id, (present, total) in summary.items():
        percentage = (present / total * 100) if total > 0 else 0
        print(f"{employees[emp_id][0]}: {percentage:.2f}% Present")

mark_attendance(101, "2025-03-01", "Present")
mark_attendance(102, "2025-03-01", "Absent")
mark_attendance(103, "2025-03-01", "Present")
mark_attendance(104, "2025-03-01", "Present")
mark_attendance(105, "2025-03-01", "Absent")

search_attendance(104)
attendance_summary()
