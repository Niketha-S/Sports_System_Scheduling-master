# Sports_System_Scheduling-master

Sports System Scheduling

Overview
The Sports System Scheduling application is designed to streamline the process of managing sports events, schedules, and related data. It provides an efficient way to handle event organization, participant information, and schedule optimization. This project uses FastAPI for the backend framework and Python for its core logic.

Features
User-friendly Interface: Simple navigation and interaction.
Dynamic Scheduling: Automated and optimized scheduling for sports events.
Conflict Resolution: Uses interval trees to manage and detect scheduling overlaps.

Project Structure

.
├── .gitignore             # Git ignore rules
├── README.md              # Project documentation
├── bin/                   # Scripts for environment setup and execution
├── core/                  # Core functionality and modules
├── data/                  # Data storage and management
├── main.py                # Main entry point of the application
├── public/                # Static assets (CSS, JS, images)
├── requirements.txt       # Python dependencies
├── routes/                # API route definitions
```

Prerequisites
- Python 3.8 or higher
- `pip` (Python package installer)

 Installation
1. Clone the repository:
   ```bash
   git clone <repository_url>
   ```

2. Navigate to the project directory:
   ```bash
   cd Sports_System_Scheduling-master
   ```

3. Create a virtual environment (optional but recommended):
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

4. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

Usage
1. Run the main script:
   ```bash
   python main.py
   ```

2. Access the application via your browser at `http://localhost:8000` (default).




New Features
Dataframes Created


Team: Contains team-specific information.
Venue: Stores venue details.
League: Manages league-specific data.
Input_Sports Dictionary


A dictionary mapping sports to their respective names, enabling support for multiple sports types.
Venue Object


Fully implemented to handle venue-specific operations.
Generate Class


Successfully schedules and passes all test cases.

Logic Used
Formula for scheduling games:
 Number of Games=Number of Teams×(Number of Teams−1)2\text{Number of Games} = \frac{\text{Number of Teams} \times (\text{Number of Teams} - 1)}{2}
Case 1–4: One match scheduled per week.


Case 5–8: Matches are randomized.


Availability Class


Tracks each day of the week and maintains available time intervals.

Project Modules
1. Api.py
Built with FastAPI for creating a lightweight and efficient web application.
Handles routes and authentication mechanisms.
Includes custom modules for scheduling games.
Runs tests on the generated schedule.
2. Games.py
Manages the organization and display of game data.
3. Interval_Tree
Features:
Insertion of intervals.
Detection of overlapping intervals.
Flattening the tree structure into a list of intervals.
Final time complexity for inserting game slots: O(log⁡n)O(\log n).
Identifies and resolves conflicting time slots efficiently.


Functional Highlights
Scheduler
The scheduler utilizes an Interval Tree to optimize and manage scheduling conflicts effectively. Key functionalities include:
- Flattening trees into intervals.
- Inserting game slots in `O(log n)` complexity.
- Identifying and resolving conflicting time slots.
- Generating game schedules that avoid overlaps across teams, venues, and time slots.

Key Classes and Modules
1. Availability: Tracks team and venue availability.
2. IntervalTree: Implements a binary search tree for time interval management, with added features like conflict detection and overlap management.
3. Game: Encapsulates game attributes like team names, league, venue, and time slots, ensuring consistent data structures for the scheduler.
4. API: FastAPI-based backend for route handling, authentication, and scheduling workflows.

Scheduler Algorithm
The algorithm follows these steps:
1. Group Teams: Organizes teams by leagues for manageable scheduling.
2. Generate Matches: Randomly pairs teams and computes potential match combinations based on constraints.
3. Time Slot Assignment: Allocates matches to available time slots, ensuring non-overlapping schedules for teams and venues.
4. Conflict Resolution: Uses the interval tree structure to detect and resolve overlapping time slots dynamically.

Input Files
Each test case directory contains:
team.csv: Contains details about the teams, such as team names and affiliations.
league.csv: Holds information about leagues, including league names and assigned teams.
venue.csv: Provides venue details, including venue names, field numbers, and time slot availability.

Output File
The scheduler generates a `schedule.csv` file with the following headers:
- team1Name: Name of the first team.
- team2Name:: Name of the second team.
- week: Week number of the year (1–52).
- day: Day of the week (1–7, where Monday = 1).
- start: Match start time (0–23.5, in 30-minute increments).
- end: Match end time (0–23.5, in 30-minute increments).
- season: Year of the season (assume 2024 for all matches).
- league: Name of the league.
- location: Venue description in the format `"<venue_name> Field #<field_number>"`.

Directory Details
- `bin/`: Contains scripts for building and running the environment, including environment setup and testing.
- `core/`: Includes scheduling logic, such as interval tree implementation and game scheduling algorithms.
- `data/`: Stores input and output files, including test case datasets and generated schedules.
- `routes/`: Manages API endpoints for the backend, including routes for retrieving and submitting schedules.
- `public/`: Hosts static assets for the web UI, including CSS and JavaScript files.

Testing
To ensure functionality, the project includes a suite of test cases. Run tests as follows:
1. Execute the test script:
   ```bash
   ./bin/test <case>
   ```
2. Each case evaluates the scheduler's ability to handle varying complexities, including:
   - Case 1: Small-scale scheduling with uniform availability.
   - Case 5: Complex synthetic data with limited venues and availability.
   - Case 9: Randomly generated large datasets with varied constraints.

Test Case Scenarios
- Case 1: 8 Teams, 1 League, 1 venue, 4 fields, uniform availability.
- Case 2: 8 Teams, 3 Leagues, 1 venue, 4 fields, uniform availability.
- Case 3: 16 Teams, 1 League, 1 venue, 1 field, uniform availability.
- Case 4: 24 Teams, 1 League, 1 venue, 1 field, limited availability.
- Case 5: Synthetic data with 52 teams, 3 leagues, limited venues, and limited availability.
- Case 6: Synthetic data with 104 teams, 3 leagues, limited venues, and limited availability.
- Case 7: Synthetic data with 104 teams, 3 leagues, varied games, limited venues, and availability.
- Case 8: Synthetic data with 104 teams, 3 leagues, 1 venue, full availability.
- Case 9: Large randomly generated datasets, incorporating erroneous data for robustness testing.

Contributing
1. Fork the repository.
2. Create a feature branch:
   ```bash
   git checkout -b feature/your-feature
   ```
3. Commit your changes:
   ```bash
   git commit -m "Add your message here"
   ```
4. Push to the branch:
   ```bash
   git push origin feature/your-feature
   ```
5. Create a Pull Request.

License
This project is licensed under the MIT License. See the `LICENSE` file for details.

Acknowledgments
- Special thanks to the contributors and open-source community.
- Inspired by scheduling challenges in sports management systems.

