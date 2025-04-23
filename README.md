CSUbatch-Job-Scheduling-System

# CSUbatch - Job Scheduling System

**CSUbatch** is a batch job scheduling system designed to simulate job submission, scheduling, and execution using classic CPU scheduling policies: **FCFS**, **SJF**, and **Priority Scheduling**. It features a real-time job submission interface, execution tracking, logging, and performance monitoring, tailored for educational and research purposes.



##  Table of Contents
- [Project Overview](#project-overview)
- [Key Features](#key-features)
- [System Architecture](#system-architecture)
- [Technologies Used](#technologies-used)
- [Setup & Installation](#setup--installation)
- [Usage Guide](#usage-guide)
- [Development Cycles](#development-cycles)
- [Future Enhancements](#future-enhancements)
- [Contributors](#contributors)
- [License](#license)

---

##  Project Overview

CSUbatch is divided into four modular components:

### 1️⃣ Job Submission & User Interface
- A web-based form to submit jobs (name, burst time, priority, scheduling algorithm).
- Jobs are stored in a MySQL database and visualized in a table with real-time status updates.

### 2️⃣ Job Scheduling Algorithms & Execution
- Implements FCFS, SJF, and Priority scheduling.
- Jobs are executed using Python’s threading for concurrency.
- Turnaround time and execution duration are recorded for each job.

### 3️⃣ Database Integration
- MySQL is used to persist job data.
- `mysql-connector-python` handles queries and connection pooling.

### 4️⃣ Monitoring & Logging
- Logs job lifecycle events.
- Performance metrics such as throughput and average turnaround time are computed.
- A dashboard provides visual insights into job queue status and logs.

---

## ✨ Key Features

-  Submit and track jobs in real-time
-  Automatic scheduling and asynchronous job execution
-  Track turnaround time and execution duration
-  Supports FCFS, SJF, and Priority scheduling algorithms
-  Logging and performance evaluation tools
   Simple, clean, and responsive web interface

---

##  Technologies Used

| Area        | Technology           |
|-------------|----------------------|
| Backend     | Python, Flask        |
| Frontend    | HTML, CSS, JavaScript|
| Database    | MySQL                |
| Scheduling  | Multithreading, Custom Algorithms |
| Tools       | PyCharm, VS Code, Git, Ubuntu    |

---
 Build and Content
✅ Project Modules: Job Submission, Scheduling Logic, Backend/Database, Monitoring

✅ Architecture Overview under “Project Overview” and “System Architecture”

✅ What the system does (end-to-end flow described)

✅ Web-based interface and execution flow

## Setup & Installation

###  Prerequisites
- Python 3.x
- MySQL Server
- pip

###  Steps

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Sri-kavya-Project001/job-scheduling-system.git
   cd job-scheduling-system
   
2. Configure MySQL Database:
    Create a database and required tables (jobs, logs).
    Update db.py with your MySQL credentials.

3. Run the application:
   python app.py
4. Access the UI: Open your browser and go to:
    http://localhost:5001
5. Usage Guide:
    Use the main form to submit jobs.
    
    Select the scheduling algorithm (FCFS, SJF, or Priority).
    
    Submitted jobs will automatically be scheduled and executed.
    
    Monitor job statuses and logs from the dashboard.
    
    Use the /simulate endpoint to auto-generate bulk jobs for testing performance.

###  Development Cycles
✅ Cycle 1 - Planning & Initialization
Project goals defined

Modules and responsibilities allocated

Initial GitHub setup and issue tracking

✅ Cycle 2 - Core Development
Flask app structure

Job submission form and job table UI

Scheduling logic (FCFS, SJF, Priority)

Job execution with threading

✅ Cycle 3 - Testing & Enhancements
Performance evaluation module

Logging and job status tracking

UI and CSS improvements

Automated execution upon submission

Removal of unused dashboard.py

Report and presentation preparation

### Contributors
  Sri Kavya
  Chaitanya
  Hemanth
  Isha

### Team Members of CPSC6179 - Spring 2025

### License
This project is licensed for educational use under MIT License.
