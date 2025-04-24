# CSUbatch: Multithreaded Batch Job Scheduler

---

## 🧩 Overview

**CSUbatch** is a multithreaded batch job scheduling system developed using Python (Flask) and MySQL. It simulates real-time job scheduling with three classical scheduling algorithms:
- First-Come, First-Served (FCFS)
- Shortest Job First (SJF)
- Priority Scheduling

The system supports automatic job execution, process logging, and performance evaluations.

---

## 🧑‍💻 Target Users

| User Type         | Background Assumed                           | Purpose                                     |
|-------------------|----------------------------------------------|---------------------------------------------|
| End Users         | Basic Python, browser use                    | Submit, monitor jobs                        |
| User-Developers   | Familiar with Flask, HTML, CSS               | Extend UI, add validations                  |
| Developers        | Python (Flask), threading, MySQL, Linux CLI | Modify scheduling algorithms, logging       |

---

## 📚 Resources and Documentation

- [Project Repository (GitHub)](https://github.com/your-repo-link)
- [Installation Guide](#-installation)
- [Getting Started Tutorial](#-quick-start-guide)
- [Developer Guide](#-developer-guide)
- [FAQs](#-faq)
- [Changelog](CHANGELOG.md)

---

## ✅ Features

- Web-based job submission form
- Automatic job execution
- Supports FCFS, SJF, and Priority
- Real-time job tracking
- MySQL backend
- Modular codebase
- Platform independent (tested on Windows & Ubuntu)

---

## 🚀 Quick Start Guide

### Prerequisites

- Python 3.10+
- MySQL Server 8+
- pip (Python package installer)

### 1. Clone Repository

```bash
git clone https://github.com/your-repo-link/csu_batch_project.git
cd csu_batch_project

### 2. Create and Activate Virtual Environment

```bash
python -m venv venv
venv\Scripts\activate
 
### 3. Install Dependencies

```bash
pip install -r requirements.txt

### 4. Set Up MySQL Database

sql
CREATE DATABASE csu_batch_db;
USE csu_batch_db;
-- Run the SQL from schema.sql provided in /sql folder

### 5. Run Application

```bash
python app.py
The app runs at: http://127.0.0.1:5001/

🖥️ What You’ll See
Landing page with a job submission form

Job listing with status updates

Color-coded progress and result feedback

🛠 Installation
From GitHub (recommended)
```bash
git clone https://github.com/your-repo-link/csu_batch_project.git
Uses plain directory structure.

All files are located inside the main csu_batch_project directory.

Includes a README.md with:

Project name

License

Version

Website and help contact

🧪 Testing
To run unit tests for the application:

```bash
python -m unittest test_app.py
This runs test cases defined in test_app.py.

Make sure your virtual environment is activated and dependencies installed.

Tests validate:

Job submission and response

Scheduling logic flow

Database connectivity
🧱 Build Instructions
Platform: Ubuntu 22.04 / Windows 11

Build System: Manual + virtual environment

Dependencies:

Flask, mysql-connector-python, threading, pytest

Dependency Management: pip

Build Verification: Run app.py, use the UI, and check job flow

📂 Directory Structure
plaintext
Copy
Edit
csu_batch_project/
│
├── app.py                  # Main Flask app
├── scheduler.py            # Scheduling algorithms
├── db.py                   # Database connector
├── templates/
│   ├── index.html          # Main UI
├── static/
│   ├── style.css           # UI styles
├── tests/                  # Test cases
├── README.md               # This file
├── sql/

🧑‍💼 Developer Guide
Modifying scheduling algorithms: Edit scheduler.py

Adding new fields to job form: Edit templates/index.html and app.py

Logging: Implemented using basic Python logging in future enhancements

🔐 Licensing & Governance
License: MIT

Project Maintainers:

Contributor 1(Sri kavya) - UI and Backend

Contributor 2(Chaitanya) - Scheduling Logic

Contributor 3(Hemanth) - Testing & Performance

Contributor 4(ISha) - Database & Docs

🧠 Learnability
✅ Basic usage covered in Getting Started

✅ Advanced use (e.g. performance metrics logging) explained in comments

✅ Full UI and API are documented

✅ Example use cases with screenshots to be added soon

🔍 Accessibility
✅ Freely accessible binary and source via GitHub

✅ No login or registration required

✅ Hosted on GitHub for long-term availability

🧪 Testability
✅ Unit tests using pytest

✅ Tests cover job submission, scheduling behavior

❌ No GUI automation tests yet (future)

✅ Easy test script: pytest

🔄 Portability

Platform	Status
Windows 10/11	✅
Ubuntu 20.04+	✅
MacOS	✅
Chrome, Firefox	✅
🔬 Analysability
✅ Modular source structure

✅ Descriptive function names

✅ Code is commented

✅ Auto-generated code is separated (none currently)

✅ No commented-out legacy code

🔁 Changeability
✅ Easy to modify form and logic

✅ Well-structured Flask app

✅ Team GitHub contribution workflow


### ❗ Common Errors & Troubleshooting

### 🔌 Database Connection Error

**Error:** `mysql.connector.errors.InterfaceError: 2003: Can't connect to MySQL server on 'localhost:3306'`  
**Cause:**  
MySQL service is not running or host/port is misconfigured.  

**Solution:**  
Start MySQL:

```bash
sudo systemctl start mysql
```

Check connection parameters in `db.py`:

```python
connection = mysql.connector.connect(
    host='localhost',
    user='yourusername',
    password='yourpassword',
    database='csu_batch'
)
```

---

### 📝 Form Submission Error

**Error:** `Missing required form fields`  
**Cause:**  
One or more required fields (`Job Name`, `Burst Time`, `Priority`) were left empty.  

**Solution:**  
Ensure all fields are filled before clicking **Submit**. Both client-side and server-side validations are included.

---

### ⚙️ Job Execution Issue

**Error:** `Job executes but does not update the status to 'Completed'`  
**Cause:**  
Missing status update logic in job execution function.  

**Solution:**  
Ensure your execution code calls:

```python
update_job_status(job_id, 'Completed')
```

And that `update_job_status()` is defined in `db.py`:

```python
def update_job_status(job_id, status):
    cursor.execute("UPDATE jobs SET status = %s WHERE id = %s", (status, job_id))
    connection.commit()
```

---

### 🗃️ Database Schema Error

**Error:** `mysql.connector.errors.ProgrammingError: 1146 (42S02): Table 'csu_batch.jobs' doesn't exist`  
**Cause:**  
The `jobs` table hasn't been created yet.  

**Solution:**  
Create the table in MySQL:

```sql
CREATE TABLE jobs (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100),
  burst_time INT,
  priority INT,
  status VARCHAR(50),
  submission_time TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---

### 🎨 UI & Styling Issue

**Error:** `CSS not applied to HTML page`  
**Cause:**  
CSS file not correctly linked in the HTML.  

**Solution:**  
Ensure the following is in the `<head>` section of your HTML:

```html
<link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
```

And that `style.css` is inside the `static/` folder.

---

### 🧵 Multithreading Error

**Error:** `Threads not synchronizing properly`  
**Cause:**  
Missing `Lock` or `Condition` around shared resources.  

**Solution:**  
Wrap critical sections with:

```python
with condition:
    # critical section
    condition.notify()
```

And initialize using:

```python
condition = threading.Condition()
```

---

### sql

CREATE DATABASE csubatch;

🛠️ Basic Use Cases
1. Submit a Job
Fill in Job Name, Priority (1–10), Execution Time, and choose Scheduling Algorithm

Click Submit

You’ll be redirected to the job list, where new jobs appear with status “Pending.”

2. Monitor Job Status
On the homepage, status updates automatically every 5 seconds

Pending → Running → Completed in real time

Execution duration & turnaround time populate once complete

3. View Dashboard Logs
Visit http://127.0.0.1:5000/dashboard

See the last 50 log entries and overall metrics (total jobs, average turnaround)

4. Reset Database (for testing)
sql
Copy
Edit
DELETE FROM jobs;
DELETE FROM logs;
Clears all job & log tables so you can start fresh

🚀 Advanced Use Cases
Bulk Job Simulation
Hit the test endpoint to auto-create & execute jobs:

arduino
Copy
Edit
http://127.0.0.1:5001/test?num_jobs=10&min_time=1&max_time=5&policy=FCFS
Use different policy values: FCFS, SJF, Priority

Cancel & Restart a Job
(Future enhancement example)

Abort: Send a DELETE or custom /cancel/<job_id> request

Restart: Re-submit via UI or call /submit with original parameters

Execution time resets to current time on restart

Performance Evaluation
After simulation, compare throughput & turnaround time in the dashboard

Export metrics by querying SELECT * FROM jobs; and analyzing externally



📌 FAQ
Q: Does CSUbatch run jobs automatically?
A: Yes, jobs are executed immediately upon submission.

Q: Can I switch between FCFS, SJF, and Priority?
A: Yes, just select from the scheduling dropdown in the form.

Q: Is there a monitoring dashboard?
A: All job statuses are visible on the homepage UI.

📩 Contact
Email:kavyadev2012@gmail.com/chaitanyachikka.2302@gmail.com

GitHub Issues: Submit here

📅 Version
Version:  3.12.3

Date: April 2025

