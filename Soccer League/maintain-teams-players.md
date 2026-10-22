# Feature 3: Maintain Teams Players 

## User Stories 

### US-3.1: Manage Teams 
**As an** Owner 
**I want to** add, update, and remove teams within a league 
**So that** the league has active teams for the schedule. 

**Priority:** P1 
**Independent test:** Verify the Owner can create a new team, assign it ot a league, and assign a Manager to it.
**Acceptance scenarios:** see ### US-3.1- Manage Teams under Acceptance Criteria


### US-3.2: Manage Player Rosters
**As a** Manager
**I want to** add an unlimited number of players to my team and define their roles 
**So that** the system can accurately track stats based on each player's specific role 

**Priority:** P1
**Independent test:** Verify a Manager can add a new player with a specific role to their assigned team 
**Acceptance scenarios:** see ### US-3.2 - Manage Player Rosters under Acceptance Criteria

### US-3.3: Track Team Payments 
**As an** Owner
**I want to** track the payment status of each team 
**So that** I can ensure every team has fulfilled their one-time registration fee. 

**Priority:** P1
**Independent test:** Verify a Manager can add a new player with a specific role to their assigned team 
**Acceptance scenarios:** see ### US-3.3 - Track Team Payments under Acceptance Criteria


## Functional Requirements
* **Team CRUD:** The system must provide the Owner with the ability to create, read, update, and delete team records 
* **Player CRUD:** The system must allow Owners and Managers to add, update, and remove players on a roser. There is no limit to the number of players that can be added to a team. 
* **Role-Based Stats Preparation:** Player profiles must include a "role" designation, as their future stats will be dependent on this role. 
* **Payment Tracking:** The system must track a boolean value (true/false) for team payments, as teams only pay once per season. 


## Key Entities
* Team
* Player
* User (Owner, Manager)

## Initial Data Model

### Team

| Field | Type | Rules |
| --- | --- | --- |
| `team_id` | String | Unique ID, Required |
| `league_id` | String | Links to League ID, Required |
| `manager_id` | String | Links to User ID, Required |
| `name` | String | Required |
| `has_paid` | Boolean | Required, Defaults to False |
| `is_active` | Boolean | Required |

### Player 

| Field | Type | Rules |
| --- | --- | --- |
| `player_id` | String | Unique ID, Required |
| `team_id` | String | Required (e.g., North Field, Gym A) |
| `name` | String | Optional |
| `is_active` | Boolean | Required |

## Acceptance Criteria

### US-3.1 - Manage Teams 

#### Scenario: Owner successfully creates a team (happy path)
* **Given** the user is logged in as an "Owner"
* **And** the user is on the Maintain Teams dashboard
* **When** the user enters a team name, selects a League, and selects a Manager
* **And** the user clicks "Save Team"
* **Then** the new team should be saved in the database
* **And** the team should appear in the active teams list 

### US-3.2 - Manage Player Rosters 

#### Scenario: Manager adds a player to their team
* **Given** the user is logged in as a "Manager" 
* **And** the user is viewing their assigned team's roster 
* **When** the user clicks "Add Player", enters the player's name, and selects their role
* **And** the user clicks "Save Player" 
* **Then** the player should be added to the team roster

### US-3.3 - Track Team Payments 

#### Scenario: Owner updates a team's payment status 

* **Given** the user is logged in as "Owner" 
* **When** the user views the Maintain Teams list 
* **And** clicks the "Mark as Paid" toggle for a specific team
* **Then** the team should update the team's 'has_paid' status to true
* **And** the visual indicator icon should show the team is in good standing

## Screen Requirements

### [View: Maintain Teams]
* Heading / purpose: Manage league teams, assign managers, and track payments 
* Primary action: **Add Team** 
* Fields, dialogs, icon actions:
  * Dropdown menu to select the League
  * Dropdown to assign a Manager 
  * Text field for Team Name
  * Payment status toggle (Paid/Unpaid)
  * Edit Icon or Button
  * Delete icon or button 
* **Empty state:** "No teams have been created. Click Add Team to begin."
* **Loading / error:** Standard loading spinner / Text error message for failures

### [View: Team Roster]
* Heading / purpose: Manage unlimited amount of players assigned to a specific team
* Primary action: **Add Player**
* Fields, dialogs, icon actions:
  * Text field for Player Role
  * Dropdown for Player Role
  * Data table listing active players
  * Edit icon or button
  * Delete icon or button
* **Empty state:** "No locations have been added yet."
* **Loading / error:** Standard loading spinner / Text error message for failures

**App chrome** (if this feature adds or changes it)
* The main menu bar adds "Maintain Teams" (Owner only) and "My Roster" (Manager only)