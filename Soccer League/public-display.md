# Feature 8: Public Display

## User Stories 


### US-8.1: View Schedules and Scores
**As a** Public User
**I want to** view league schedules and games cores
**So that** I can stay updated on game results and upcoming matches.

**Priority:** P1 
**Independent test:** Verify an unauthenticated user can navigate to a season and see a list of all games and their scores. 
**Acceptance scenarios:** see ### US-8.1 - View Schedules and Scores under Acceptance Criteria 

### US-8.2: View Teams and Players
**As a** Public User (People)
**I want to** browse through teams and view their player rosters
**So that** I can see who is actively playing in the league. 

**Priority:** P2
**Indpendent test:**  Verify clicking on a team name displays a list of its active players and their assigned roles. 
**Acceptance scenarios:** see ### US-8.2 - View Teams and Players under Acceptance Criteria 

### US-8.3: View Player Statistics
**As a** Public User (People)
**I want to** view individual player statistics 
**So that** I can track performance events such as the different types of flags raised. 

**Priority:** P2 
**Indpendent test:** Verify a player's public profile correctly displays the stats logged by Managers
**Acceptance scenarios:** see ### US-8.3 - View Player Statistics under Acceptance Criteria 



## Functional Requirements 
* **Public Access:** The system must allow people not logged in to view the system's data on teams and leagues
* **Read-Only Data:** The system must display the different Leagues, Stats, Players, and Schedules without allowing them to be changed
* **Real-Time Synchronization:** The public view must reflect the live score and stats updated by managers during a live game. 




## Key Entities 
* League 
* Season 
* Team 
* Player
* Game 
* PlayerStat


## Initial Data Model 

* **GameResult Table:** Read-only access to display live and final scores.
* **Team & Player Tables:** Read-only access to display team names and player rosters.
* **PlayerStat Table:** Read-only access to display individual player achievements (like flags raised).

## Initial Data Model

*(Note: The public portal securely reads from existing tables)*

| Field | Type | Rules |
| --- | --- | --- |
| `game_id` | String | Links to Game ID, Read-only |
| `home_team_name` | String | Read-only |
| `away_team_name` | String | Read-only |
| `game_date` | Timestamp | Read-only |
| `home_score` | Integer | Read-only, has Live updates |
| `away_score` | Integer | Read-only, has Live updates |


### Acceptance Criteria 

### US-8.1 - View Schedules and Scores

#### Scenario: Public user views a season schedule
* **Given** the user is an unauthenticated public user 
* **When** the user goes to the public portal and selects a season
* **Then** the system should display a list of all of the scheduled games
* **And** show the live or final scores for games that have started

### US-8.2 - View Teams and Players

#### Scenario: System emails team managers
* **Given** the user is viewing the public standings
* **When** the user clicks on a specific team name 
* **Then** the system should navigate to the team's public profile 
* **And** display a list of all active players on that roster


### US-8.3 - View Player Statistics

#### Scenario: Public user views a player's flag history 
* **Given** the user is viewing a team roster
* **When** the user clicks on a player's name
* **Then** the system should display the player's added stats
* **And** include a breakdown of specific events like "Flags Raised"


## Screen Requirements 

### [View: Public Portal Home]
* Heading / purpose: Main page for people to view leagues, standings, and recent scores.
* Primary action: **Select Season** 
* Fields, dialogs, icon actions: 
 * Dropdown to filter by Sport and Season
 * Data table displaying team's standings (Wins/Losses).
 * List view of recent and live games with scores.
* **Empty state:** "No active seasons available to display."
* **Loading / error:** Standard loading spinner / Text error messages for failures 

### [View: Public Team Profile]
* Heading / purpose: View a team's scheduled games and player roster
* Primary action: N/A Read Only 
* Fields, dialogs, icon actions: 
 * Data table listing active players and roles
 * Data table listing the team's 18-game schedule and results
* **Empty state:** "No roster information available for this team."
* **Loading / error:** Standard loading spinner / Text error messages for failures 

* **App chrome** 
* The public views completely hide the admin menu bar. The publiv view only contains links to "Home," "Standings," and "Teams."