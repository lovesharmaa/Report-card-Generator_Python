#🎓 #Student Grading System & Report Generator 🐍
This repository features a robust Python implementation for managing student academic records and automating the generation of digital report cards. It demonstrates the power of nested data structures and conditional logic, which are essential for developers building scalable management systems or data-processing pipelines.
🛠️ Tools & Environment
Language: Python 3.x
Environment: Terminal / CLI
Key Concepts: Nested Dictionaries, Data Mapping, Loops & Control Flow, Arithmetic Computation.
## 🗃️ Data Modeling & Mapping
📌 Concept: Utilizing dictionaries to create a structured relationship between unique identifiers (Roll Numbers), student names, and their respective subject scores.
🧾 Code:
Python
# Student database with nested marks
student_scores = {
    "Harsh sharma": {"maths": 11, "Science": 78, "Sst": 53, "Hindi": 65, "English": 75},
    "Shantanu": {"maths": 67, "Science": 58, "Sst": 63, "Hindi": 34, "English": 23},
    "Raghav verma": {"maths": 93, "Science": 89, "Sst": 86, "Hindi": 99, "English": 93},
    "Aditi gupta": {"maths": 81, "Science": 87, "Sst": 94, "Hindi": 99, "English": 98},
    # ... additional records truncated for brevity
}

# Roll Number mapping for O(1) lookup
roll_mapping = {
    1: "Harsh sharma",
    2: "Shantanu",
    14: "Raghav verma",
    18: "Aditi gupta",
    # ... additional mappings
}
📘 Explanation/🎯 Use Case:
How: By using a "Map of Maps" (Nested Dictionary), we store complex attributes under a single key.
Use Case: This structure mimics how NoSQL databases (like MongoDB) store JSON documents, making it a fundamental skill for backend development.
## 📈 Computation & Logic Engine
📌 Concept: A loop-driven interface that calculates academic metrics (Total, Percentage, Division) based on user input.
🧾 Code:
Python
def generate_report():
    while True:
        try:
            roll = int(input("Enter the roll number: "))
            
            # Fetching data using cross-referenced dictionaries
            student_name = roll_mapping[roll]
            subject_data = student_scores[student_name]

            # Logic: Calculate metrics
            total_obtained = sum(subject_data.values())
            percentage = total_obtained / 5

            # Logic: Determine Academic Division
            if percentage >= 60:
                division = "First Division"
            elif percentage >= 45:
                division = "Second Division"
            elif percentage >= 33:
                division = "Third Division"
            else:
                division = "Fail"
                
            display_card(student_name, total_obtained, percentage, division)
            
        except KeyError:
            print("❌ Invalid Roll Number. Please try again.")
            continue

        repeat = input("To check another result, press '2': ")
        if repeat != "2":
            print("Exiting... Have a great day!")
            break
📘 Explanation/🎯 Use Case:
How: sum(z.values()) aggregates scores dynamically, while if-elif-else chains handle multi-tiered grading criteria.
Use Case: Essential for Fintech applications (calculating interest tiers) or E-commerce (applying discounts based on cart value).
## 📄 UI Presentation (Report Card)
📌 Concept: Formatting raw data into a human-readable visual output using string manipulation and delimiters.
🧾 Code:
Python
def display_card(name, marks, per, div):
    print("\n" + "—" * 50)
    print(f"---------------- ⭐ REPORT CARD ⭐ ----------------")
    print(f"Name of student: {name}")
    print("—" * 50)
    print(f"Total marks:      500")
    print(f"Marks obtained:   {marks}")
    print(f"Percentage:       {per}%")
    print(f"Division:         {div}")
    
    if per >= 33:
        print("[ CONGRATULATIONS! ☀️ Have a bright future ]")
    else:
        print("Better luck next time...")
    print("—" * 50 + "\n")
📘 Explanation/🎯 Use Case:
How: Uses formatted print statements to create a clean visual hierarchy in the console.
Use Case: Useful for Command Line Interfaces (CLIs) where generating clear logs or summary tables is required for DevOps or SysAdmin tasks.
Would you like me to refactor this code into a Class-based (Object-Oriented) structure to make it even more professional?
