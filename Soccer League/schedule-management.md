# Feature 4: Schedule Management 

## User Stories 

### US-4.1: Auto-Generate Season Schedule 
**As an** Owner 
**I want to** generate a schedule where each team plays 18 games
**So that** I do not have to create every game individually for the season

**Priority:** P1 
**Independent test:** Verify the system generates exactly 18 games per team only on Tuesdays and Fridays throughout the corresponding season.  
**Acceptance scenarios:** see ### US-4.1- Auto-Generate Season Schedule under Acceptance Criteria


### US-4.2: Update Scheduled Games 
**As an** Owner
**I want to** be able to change the location or date of a game after it has already been
**So that** I can accommodate field closures or weather delays 

**Priority:** P1
**Independent test:** Verify the Owner can succesfully edit an existing game and save a new location. 
**Acceptance scenarios:** see ### US-4.2 - Update Scheduled Games under Acceptance Criteria

### US-4.3: Restrict Schedule Changes 
**As a** system administrator 
**I want to** ensure that only the role can change the schedule 
**So that** Managers and other users cannot change game times or locations. 

**Priority:** P1
**Independent test:** Verify the edit game options are hidden or disabled for users logged in as a manager.
**Acceptance scenarios:** see ### US-4.3 - Restrict Schedule Changes under Acceptance Criteria


## Functional Requirements
* **Schedule Algorithm:** The system must automatically generate the schedules with each team playing exactly 18 games, 2 games per week, on Tuesdays and Fridays.
* **Manual Overrides:** The system must allow the Owner to change the location and time of a game when it has already been planned 
* **Access Control** Only the Owner (David North) is authorized to change the schedule. Managers and other users only have read-only access to the schedule.  



## Key Entities
* Game
* Season
* Team 
* Location 
* User(Owner)

## Initial Data Model

### Game

| Field | Type | Rules |
| --- | --- | --- |
| `game_id`| String | Unique ID, Required |
| `season_id` | String | Links to Season ID, Required |
| `home_team_id`| String | Links to Team ID, Required |
| `away_team_id` | String | Links to Team ID, Required |
| `location_id` | String | Links to Location ID, Required |
| `game_date` | Timestamp | Requirede |
| `status` | Enum | Values: SCHEDULED, COMPLETED, CANCELED |


## Acceptance Criteria

### US-4.1 - Auto-Generate Season Schedule

#### Scenario: Owner generates schedule for a season
* **Given** the user is logged in as an "Owner" 
* **And** a Season has been created with registered Teams
* **When** the user clicks "Generate Schedule"
* **Then** the system should create 18 games for each team
* **And** all generated games should fall on a Tuesday or Friday

### US-4.2 - Update Scheduled Games  

#### Scenario: Owner changes a game location 
* **Given** the user is logged in as an "Owner" 
* **And** a game is already scheduled at "Main Soccer Fied"
* **When** the user edits the game and selects "North Field" as the location
* **And** clicks "Save Game" 
* **Then** the game's location should be updated in the database.

### US-4.3 - Restrict Schedule Modifications

#### Scenario: Manager attempts to edit a game

* **Given** the user is logged in as a "Manager" 
* **When** the user views the Schedule Dashboard
* **Then** the "Edit Game" action should not be visible 
* **And** the user should not be able to change game locations or dates

## Screen Requirements

### [View: Schedule Dashboard]
* Heading / purpose: View the season Schedule and auto-generate games 
* Primary action: **Generate Schedule** (Only visible to the owner) 
* Fields, dialogs, icon actions:
  * Dropdown filter for Season and League 
  * Data table or calendar view listing all games 
  * Edit Game icon or button (Visible only to Owner)
  * Dialog for editing game date, time, and location
  * Edit Icon or Button
  * Delete icon or button 
* **Empty state:** "No games scheduled for this season. Click Generate Schedule to begin."
* **Loading / error:** Standard loading spinner / Text error message for failures

**App chrome** (if this feature adds or changes it)
* The main menu bar includes a "Schedule" link. The "Generate Schedule" and "Edit Game" controls within that screen are hidden from non-Owner users.

