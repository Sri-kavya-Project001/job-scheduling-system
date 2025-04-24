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

❗ Common Errors & Troubleshooting
🔌 Database Connection Errors
---Error: Could not connect to MySQL database
Cause:
MySQL server is not running

Invalid credentials or incorrect database name in db.py

Solution:

Ensure MySQL server is running:

```bash
sudo service mysql start
Verify your credentials in db.py:

python
connection = mysql.connector.connect(
    host="localhost",
    user="your_username",
    password="your_password",
    database="csubatch"
)
text

pymysql.err.OperationalError: (1049, "Unknown database 'csubatch'")
Cause:

The csubatch database hasn't been created yet.

Solution:

Log into MySQL and run:
📝 Form Submission Errors & UI Issues
text

Error: Missing required form fields
Cause:

One or more fields (Job Name, Burst Time, Priority) were left empty before submission.

Solution:

Ensure all fields are filled before clicking Submit.

Client-side validation is already added, but server-side validation also exists for safety.

text

Error: Burst Time and Priority must be positive integers
Cause:

The form was submitted with non-integer values or negative numbers in numeric fields.

Solution:

Only input positive integers for:

Burst Time (e.g., 5, 10, 25)

Priority (e.g., 1 for highest priority, 2 for lower)

text

Form appears unresponsive / button doesn’t seem to work
Cause:

JavaScript or server-side error, or the Flask server might not be running.

Solution:

Make sure Flask server is running using:

```bash
flask run
Open the browser and navigate to http://127.0.0.1:5001

Use browser developer tools (F12 → Console/Network tab) to debug further.
⚙️ Job Execution & Scheduler Issues
text

Error: Job execution seems stuck or not updating
Cause:

Scheduler thread might not be triggering properly, or job execution logic encountered a deadlock or exception.

Solution:

Check the Flask server logs for any traceback.

Confirm that your scheduler is running inside a background thread.

Ensure threading.Condition() and threading.Lock() objects are used correctly in the scheduler.py.

text

Error: Job executes but does not update the status to ‘Completed’
Cause:

Status update in the database might be missing or incorrect inside the job execution logic.

Solution:

Verify your job execution function includes a database update like:

python

update_job_status(job_id, 'Completed')
Ensure db.py has the update_job_status() function implemented correctly.

text

Scheduler Policy Error: Invalid scheduling algorithm selected
Cause:

Invalid or unsupported algorithm value passed (not FCFS/SJF/Priority).

Solution:

Ensure your HTML <select> or radio buttons pass one of the valid strings:

text

'FCFS', 'SJF', 'Priority'
Handle default fallback in case of missing or unrecognized input.

text

Error: Jobs not executing in correct order
Cause:

Possible bug in sorting logic or comparison function for the selected scheduling algorithm.

Solution:

Review your sorting logic in scheduler.py. For example:

FCFS → sort by submission time

SJF → sort by burst time

Priority → sort by priority value (lower value = higher priority)

🗃️ Database & Backend Errors
text

mysql.connector.errors.ProgrammingError: 1146 (42S02): Table 'csu_batch.jobs' doesn't exist
Cause:

The jobs table has not been created in your MySQL database.

Solution:

Run the table creation script provided in db.py or execute manually:

sql

CREATE TABLE jobs (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100),
  burst_time INT,
  priority INT,
  status VARCHAR(50),
  submission_time TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
text

mysql.connector.errors.InterfaceError: 2003: Can't connect to MySQL server on 'localhost:3306'
Cause:

MySQL service might not be running or the host/port is misconfigured.

Solution:

Start MySQL with:

bash

sudo systemctl start mysql
Check db.py connection parameters:

python

connection = mysql.connector.connect(
    host='localhost',
    user='yourusername',
    password='yourpassword',
    database='csu_batch'
)
text

mysql.connector.errors.ProgrammingError: 1049 (42000): Unknown database 'csu_batch'
Cause:

The csu_batch database does not exist yet.

Solution:

Create it using:

sql

CREATE DATABASE csu_batch;
Then run the table creation script.

text

Error: Job status not updating in database
Cause:

Either the update_job_status() method is missing, or the SQL update query has syntax/logic errors.

Solution:

In db.py, ensure you have something like:

python

def update_job_status(job_id, status):
    cursor.execute("UPDATE jobs SET status = %s WHERE id = %s", (status, job_id))
    connection.commit()
🎨 UI & Styling Errors
text

CSS not applied to HTML page
Cause:

The style.css file is not being correctly linked to your HTML.

Solution:

Make sure your HTML <head> includes:

html

<link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
Also, confirm style.css is placed inside the static/ folder.

text

HTML form fields not aligned properly
Cause:

CSS flex/grid is not configured correctly, or parent container lacks layout styling.

Solution:

Wrap form rows in a flex container:

html

<div class="form-row">
  <label>Job Name:</label>
  <input type="text" name="job_name">
</div>
And apply CSS:

css

.form-row {
  display: flex;
  gap: 10px;
  align-items: center;
  margin-bottom: 10px;
}
text

Submit button not visible / clickable
Cause:

It might be hidden under another element due to absolute positioning or overflow.

Solution:

Check for z-index, overflow, and container size.

css

button {
  z-index: 10;
  position: relative;
}
text

Table rows overlap or are hard to read
Cause:

Missing padding, inconsistent widths, or borders not defined.

Solution:

Improve with:

css

table {
  border-collapse: collapse;
  width: 100%;
}

th, td {
  border: 1px solid #ccc;
  padding: 10px;
  text-align: center;
}

tr:nth-child(even) {
  background-color: #f9f9f9;
}
text

Job status not changing color dynamically
Cause:

No dynamic class or styling based on job status.

Solution:

Use Flask templating:

html

<td class="{{ 'status-' + job.status|lower }}">{{ job.status }}</td>
And in CSS:

css

.status-pending { color: orange; }
.status-running { color: blue; }
.status-completed { color: green; }

---- Job Scheduling Errors
text

Error: Scheduling algorithm not executing correctly
Cause:

Incorrect handling of the scheduling queue or missing thread synchronization.

Solution:

Ensure the scheduling logic is correctly implemented with proper mutex/condition variable usage.

text

Error: Job not dispatched after submission
Cause:

Job is inserted into the queue but not picked up by the dispatcher.

Solution:

Verify the dispatcher thread is correctly polling and executing jobs.

---  Database Errors
text

Error: Cannot connect to the database
Cause:

Incorrect database credentials or the database server is down.

Solution:

Check the credentials in the configuration and ensure MySQL is running.

text

Error: Data not inserting into the database
Cause:

Missing connection.commit() after executing an insert query.

Solution:

Ensure to call commit() after any data insertion or modification:

python

connection.commit()
--- UI Errors
text

Error: UI not updating after job submission
Cause:

Missing page refresh or state update after job is submitted.

Solution:

Use JavaScript to trigger a UI refresh or redirect to a confirmation page after submission.

text

Error: Form submission fails due to validation issues
Cause:

Missing or incorrect form validation.

Solution:

Ensure all required fields are validated before submitting the form. Use JavaScript or Flask validation.

--- Multithreading Errors
text

Error: Threads not synchronizing properly
Cause:

Missing mutexes or condition variables when accessing shared resources.

Solution:

Ensure that all shared resources are protected with appropriate synchronization mechanisms.

text

Error: Deadlock detected in threads
Cause:

Circular dependencies between threads when locking resources.

Solution:

Refactor thread synchronization to avoid circular locks and ensure proper ordering of lock acquisition.

--- Performance Issues
text

Error: Slow job execution time
Cause:

Jobs not being scheduled efficiently or high overhead in scheduling algorithms.

Solution:

Profile the application and optimize scheduling logic, focusing on algorithm complexity.

text

Error: High CPU usage during scheduling
Cause:

Inefficient use of threads or unnecessary context switches.

Solution:

Reduce the number of active threads and optimize for better resource utilization.

--- Testing Errors
text

Error: Unit tests failing for job submission
Cause:

Test data not matching expected values or database not properly initialized.

Solution:

Ensure that the test environment is correctly set up with the appropriate test data and database.

text

Error: UI components not being tested correctly
Cause:

Missing mock data or incomplete UI test scenarios.

Solution:

Add mock data to UI tests and ensure all UI components are covered by tests.

🔧 pyvenv.cfg File
The pyvenv.cfg file, located at the root of the virtual environment, contains metadata about the environment. Here's the content of the pyvenv.cfg file:
version: Denotes the Python version used to create the virtual environment. Here, it is 3.12.3.


``sql

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

