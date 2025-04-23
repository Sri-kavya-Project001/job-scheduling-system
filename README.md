# CSUbatch - Job Scheduling System

CSUbatch is a multithreaded batch job scheduling system that simulates job submission, scheduling, and execution using three key scheduling policies: **FCFS**, **SJF**, and **Priority**. It provides a web interface for users to submit jobs, view their status, monitor execution metrics, and assess performance.

---

## 📌 Project Overview

The system is built with four major modules:

1. **Job Submission and User Interface**  
   - HTML/CSS interface for submitting jobs and selecting a scheduling algorithm.  
   - Displays real-time job status and performance metrics.

2. **Job Scheduling Algorithm and Core Logic**  
   - Implements First-Come-First-Serve (FCFS), Shortest Job First (SJF), and Priority-based scheduling.  
   - Supports multithreaded execution using Python's threading module.

3. **Database and Backend Integration**  
   - Uses MySQL to store and manage job data.  
   - Backend powered by Flask and `mysql-connector-python`.

4. **Monitoring and Logging System**  
   - Logs key events and execution details.  
   - Provides metrics like execution duration, turnaround time, and throughput.

---

## 🛠 Features

✔ Job submission and real-time status updates  
✔ FCFS, SJF, and Priority scheduling  
✔ Monitoring dashboard for job metrics  
✔ Log tracking and performance analysis  
✔ Automatic job execution on submission  
✔ Bulk job testing and performance simulation  
✔ Option to abort and restart jobs (future enhancement)

---

## ⚙️ Technologies Used

- **Backend**: Flask (Python)
- **Database**: MySQL
- **Frontend**: HTML, CSS, JavaScript
- **Multithreading**: Python `threading`
- **Dev Environment**: PyCharm + Ubuntu (WSL)

---

## 🧱 Setup & Installation

### ✅ Prerequisites

- Python 3.x  
- MySQL Server  
- pip (Python Package Manager)  
- Git  
- PyCharm or any IDE (Optional)

### 📥 Clone the Repository

git clone https://github.com/Sri-kavya-Project001/job-scheduling-system.git

cd job-scheduling-system

###📦 Create & Activate Virtual Environment
  cd /mnt/c/Users/User/PycharmProjects/PythonProject2/csu_batch_project
.\.venv\Scripts\activate

### On Ubuntu/Linux (WSL):
cd /mnt/c/Users/User/PycharmProjects/PythonProject2/csu_batch_project
source .venv/bin/activate


⚡ Run the Application
python app.py

Visit http://127.0.0.1:5001 in your browser.

🛠 MySQL Setup
🔐 Log in to MySQL
 mysql -u shivani -p

📁 Use the database
USE csu_batch_scheduler;

🧹 Reset jobs table (for testing)
DELETE FROM jobs;

🧪 Testing & Simulation
🧪 Run Unit Tests

python -m unittest test_app.py


🚀 Simulate Job Load
Submit 10 jobs (1 to 5 seconds) using FCFS:

http://127.0.0.1:5001/test?num_jobs=10&min_time=1&max_time=5&policy=FCFS

📚 Development Cycles
✅ Cycle 1
Requirements analysis

Initial UI and Flask setup

Created MySQL schema

Implemented basic FCFS scheduling

✅ Cycle 2
Added SJF and Priority scheduling

Implemented logging and dashboard

UI enhanced with CSS

Jobs auto-execute on submission

✅ Cycle 3
Improved modularity and code structure

Extended test coverage

Added performance simulation tool

Prepared reports and documentation

🚧 Future Enhancements
Abort and restart job functionality

Graph-based performance visualization

Admin control panel for job management

Support for parallel job clusters

Deploy with Docker

🙌 Authors
Sri Kavya, Hemanth, Chaitanya, Isha

Team CSUbatch

📂 Repository Structure

├── app.py               # Flask backend
├── scheduler.py         # Scheduling logic
├── db.py                # Database connection
├── index.html           # Job submission UI
├── dashboard.html       # Monitoring UI
├── style.css            # CSS styling
├── test_app.py          # Unit tests

📝 License
This project is for academic and educational purposes under the MIT License.



  
