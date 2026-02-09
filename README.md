The CEO Office Murder - A SQL Detective Story
On October 15, 2025, a serious incident occurred at the TechNova CEO Office. As the Lead Data Analyst, your mission is to use SQL to trace digital footprints—keycard swipes, phone calls, and alibis—to identify the culprit among the employees.

🕵️ Project Overview
This project is an interactive SQL-based mystery where you act as a detective. By querying various database tables, you will cross-reference human claims with system logs to uncover inconsistencies and build a case against the primary suspect.

Database Schema
The investigation provides access to a database containing the following tables:

Employees: Basic information about TechNova staff.

Keycard_logs: Timestamps of entry and exit for various rooms.

Calls: Records of phone calls, including duration and participants.

Alibis: Statements provided by employees regarding their location during the incident.


Evidence: Specific clues found at crime scenes (e.g., fingerprints, unusual access patterns).

🔍 Investigation Steps
The mystery is solved through a series of structured SQL queries:


Evidence Collection: Checking the evidence table to identify crime scenes (CEO Office and Server Room).


Access Logs: Filtering keycard_logs to see who was in the CEO Office during the critical window (20:50–21:00).


Alibi Verification: Comparing employee statements against system logs to find mismatches.


Communication Patterns: Analyzing phone call frequency and duration during the time of the incident.


Multi-Room Linking: Connecting suspects to multiple rooms where evidence was discovered.

🧪 Example Query: Alibi vs. Keycard (Truth Test)
To catch a lie, we join the alibis table with keycard_logs to see if an employee's claimed location matches the system record:

SQL
SELECT e.NAME, a.claimed_location, a.claim_time, k.room AS actual_room
FROM alibis a
INNER JOIN employees e ON e.employee_id = a.employee_id
INNER JOIN keycard_logs k ON k.employee_id = a.employee_id
AND a.claim_time BETWEEN k.entry_time AND k.exit_time
WHERE a.claimed_location != k.room;


⚖️ Final Conclusion
After analyzing the data, the evidence points to a single suspect:


Only person logged in the CEO Office at night (20:50–21:00).


Contradictory Alibi: Claimed to be in the Server Room while logs placed them in the CEO Office.


Suspicious Activity: Made multiple calls during the incident window and was linked to both evidence-related rooms.


Suspect Identified: David Kumar (Employee ID 4).


