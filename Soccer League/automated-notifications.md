# Feature 7: Automated Notifications/Alerts

## User Stories 


### US-7.1: Email Referees
**As a** Referee
**I want to** receive an automated email about my upcoming assigned games
**So that** I know exactly when and where I am expected to officiate a game. 

**Priority:** P1 
**Independent test:** Verify the system successfully generates and sends an email to a referee's email address 24 hours before their assigned game.
**Acceptance scenarios:** see ### US-7.1 - Email Referees under Acceptance Criteria 

### US-7.2: Email Managers
**As a** Manager
**I want to** receive an automated email reminder about my team's upcoming games 
**So that** I can make sure my roster is prepared and the required officials are assigned. 

**Priority:** P1 
**Indpendent test:**  Verify the system generates and sends an email to a Manager's email address prior to a scheduled game.
**Acceptance scenarios:** see ### US-7.2 - Email Managers under Acceptance Criteria 

### US-7.3: Email Players
**As a** Player
**I want to** receive an automated email reminder for my upcoming games.
**So that** I arrive at the right location on time. 

**Priority:** P1 
**Indpendent test:** Verify the system succesfully sends an email to all active players on a team's roster for an upcoming game. 
**Acceptance scenarios:** see ### US-7.3 - Assign Referees under Acceptance Criteria 



## Functional Requirements 
* **Automated Email Triggers** The system must automatically generate and send emails to Refs, Managers, and Players about upcoming games.
* **Grouping Recipients:** The system must be capable of identifying all active players on a specific team's roster to send mass notifications.
* **Notification log** The system must maintain a log of emails sent to prevent duplicate emails being sent. 




## Key Entities 
* Game 
* User (Manager, Referee)
* Player
* Notification


## Initial Data Model 

### NotificationLog


| Field | Type | Rules | '=
| --- | | --- | --- | 
| `notification_id` | String | Unique ID, Required | 
| `game_id` | String | Links to Game ID, Required | 
| `recipient_role` | Enum | Values: MANAGER, REFEREE, PLAYER | 
| `sent_at` | Timestamp | Auto-generated, Required | 



### Acceptance Criteria 

### US-7.1 - Email Referees

#### Scenario: System emails assigned referee 
* **Given** a game is scheduled and a Referee is assigned 
* **When** the system clock reaches 24 hours before the game start time 
* **Then** an email containing the game time and location should be sent to the Referee
* **And** a record should be created in the NotificationLog

### US-7.2 - Email Managers

#### Scenario: System emails team managers
* **Given** a game is scheduled between a home team and away team 
* **When** the system clock reaches 48 hours before the game start time 
* **Then** an email reminder should be sent to the Managers of both teams.


### US-7.3 - Email Players

#### Scenario: System emails team rosters
* **Given** a game is scheduled 
* **When** the system triggers the player notifications 
* **Then** all active players on both the home and away team rosters should receive an email reminder. 


## Screen Requirements 

### [View: Notification Logs]
* Heading / purpose: View a history of automated emails sent by the system
* Primary action: **Fiter Logs** 
* Fields, dialogs, icon actions: 
 * Dropdown to filter by Recipient Role (Manager, Referee, Player)
 * Data table listing sent emails, timestamps, and associated games
* **Empty state:** "No automated notifications have been sent yet"
* **Loading / error:** Standard loading spinner / Text error messages for failures 

* **App chrome** 
* The main menu bar adds a "Notification Logs" link under the "Maintenance"dropdown visible to only the owner. 