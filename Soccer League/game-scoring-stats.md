# Feature 5: Game Scoring and Statistics 

## User Stories 


### US-6.1: Enter Game Scores 
**As a** Manager
**I want to** enter the final scores for a game
**So that** accurate game results are recorded in the system for the public to view

**Priority:** P1 
**Independent test:** Verify a logged-in Manager can enter and save the home and away scores for a completed game.
**Acceptance scenarios:** see ### US-6.1 - Enter Game Scores under Acceptance Criteria 

### US-6.2: Track Player Stats 
**As a** Manager
**I want to** update player statistics based on their role and track events like flags raised
**So that** individiual performance data is updated accurately.

**Priority:** P1 
**Indpendent test:**  Verify a Manager can add a specific statistic (e.g., "Flag Raised") to a specific player to a specific game.
**Acceptance scenarios:** see ### US-6.2 - Track Player Stats under Acceptance Criteria 

### US-6.3: Assign Referees  
**As a** Manager
**I want to** select referees from a list and assign them to a scheduled game
**So that** the game is properly officiated by qualified individuals.

**Priority:** P1 
**Indpendent test:** Verify a Manager can link an active referee to a scheduled game.
**Acceptance scenarios:** see ### US-6.3 - Assign Referees under Acceptance Criteria 

### US-6.4: Unassigned Referee Alert
**As a** Manager
**I want to** receive an alert when a game does not have a referee asigned within 48 hours of the game. 
**So that** I am reminded to secure an official before the game begins. 

**Priority:** P2 
**Indpendent test:** Verify the system displays a visual alert on a game record that has no referee assignmentss. 
**Acceptance scenarios:** see ### US-6.4 - Unassigned Referee Alert under Acceptance Criteria 


## Functional Requirements 
* **Data Entry Access:**  Only users with the Manager role are authorized to put score and stat information into the system. Owners and the public cannot enter game data. 
* **Score & Stat Tracking:**  The computer system must track the final game scores and individual player events, including the different types of flags raised. 
* **Referee Assignment:** The system must provide a list of available referees for Managers to assign to specific games. 
* **Alert Mechanism:** The system must trigger an automated alert identifying any upcoming game that does not have a referee assignment. 

## Key Entities 
* Game 
* GameResult
* PlayerStat
* RefereeAssignment
* User (Manager)

## Initial Data Model 

### GameResult

| Field | Type | Rules | '=
| --- | | --- | --- | 
| `result_id` | String | Unique ID, Required | 
| `game_id` | String | Links to Game ID, Required | 
| `home_score` | Integer | Required | 
| `away_score` | Integer | Required | 
| `entered_by` | String | Links to Manager ID, Required | 


### Location 

| Field | Type | Rules | 
| --- | --- | --- | 
| `stat_id` | String | Unique ID, Required | 
| `game_id` | String | Links to Game ID, Required |
| `player_id` | String | Links to Player ID, Required |
| `stat_type` | String | Required (e.g., Flag Raised, Goal) | 
| `value` | Integer | Required |

### RefereeAssignments 

| Field | Type | Rules | 
| --- | --- | --- | 
| `assignment_id` | String | Unique ID, Required | 
| `game_id` | String | Links to Game ID, Required | 
| `referee_id` | String | Links to Referee ID, Required | 

## Acceptance Criteria 

### Acceptance Criteria 

### US-6.1 - Enter Game Scores

#### Scenario: Manager saves final game score
* **Given** the user is logged in as a "Manager" 
* **And** a scheduled is currently in progress
* **When** the user updates the home score to "1" 
* **And** clicks "Update Score"
* **Then** the GameResult record should be immediately updated in the database

### US-6.2 - Track Live Player Stats

#### Scenario: Manager records a flag raised during live play
* **Given** the user is logged in as a "Manager" 
* **When** the user is on the Live Game Dashboard 
* **And** selects a player, selects "Flag Raised", and enters a value of "1" 
* **And** clicks "Log Stat" 
* **Then** the individual stat should be permanently linked to that player's profile in real-time


### US-6.3 - Assign Referees 

#### Scenario: Manager assigns a referee to an upcoming game
* **Given** the user is logged in as a "Manager" 
* **When** the user opens a scheduled game record
* **And** selects a referee from the dropdown list 
* **And** clicks "Assign Referee"
* **Then** the RefereeAssignment record should be created. 

### US-6.4 - Unassigned Referee Alert 

#### Scenario: System alerts Manager of missing a referee
* **Given** a game is scheduled in the system 
* **When** the game has no associated records in the RefereeAssignment table 
* **Then** the Manager dashboard should display a "No Refere Assigned" alert icon next to the game. 

## Screen Requirements 

### [View: Live Score and Stat Entry]
* Heading / purpose: Input live scores and track individual player statistics during the game 
* Primary action: **Update Game Data** 
* Fields, dialogs, icon actions: 
 * Number inputs/steppers for Home Score and Awayb Score 
 * Dropdown to select Player
 * Dropdown to select Stat Type (e.g., Flag Raised)
 * Data table listing live stats entered for the current game 


* **Empty state:** "No scores or stats entered for this game yet."
* **Loading / error:** Standard loading spinner / Text error messages for failures 

### [View: Referee Assignment]
* Heading / purpose: Assign officials to scheduled games and monitor alerts 
* Primary action: **Assign Official** 
* Fields, dialogs, icon actions: 
 * Dropdown listing active Referees
 * Red alert badge icon for games missing a referee 
 * Data table listing games and assigned referees

* **Empty state:** "All upcoming games have referees assigned."
* **Loading / error:** Standard loading spinner / Text error message for failures 

* **App chrome** 
* The main menu bar adds a "Game Operations" dropdown visible only to Managers, containing links to "Live Score Entry" and "Referee Assignments".
