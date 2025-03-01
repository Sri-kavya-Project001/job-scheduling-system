CSUbatch-Job-Scheduling-System

CSUbatch is a batch job scheduling system designed to simulate job submission, scheduling, and execution using multiple scheduling policies (FCFS, SJF, and Priority). The system allows users to submit jobs via a web interface, view job statuses and performance metrics (execution duration and turnaround time), and monitor system performance through a dedicated dashboard.

Project Overview
CSUbatch is built to address the need for an efficient, modular batch scheduling system. It consists of four main modules:

Job Submission and User Interface:
Provides a web-based form for job submissions and displays the list of submitted jobs along with their statuses and performance metrics.

Job Scheduling Algorithm and Core Logic:
Implements scheduling algorithms (FCFS, SJF, Priority) to order the jobs and dispatch them for execution asynchronously.

Database and Backend Integration:
Uses MySQL (via mysql.connector) to store job data, including submission details, scheduling policy, and performance metrics. Connection pooling is used for efficient database operations.

Monitoring and Logging System:
Provides a dashboard to view performance metrics (e.g., execution duration, turnaround time) and logs key system events.

Additional features include an automated performance evaluation route that simulates bulk job submissions and calculates throughput and average turnaround time.

Installation Instructions
Prerequisites
Python 3.x
MySQL Server
pip (Python package installer)
