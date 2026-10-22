# Feature 5: Manage System Users 

## User Stories 

### US-5.1: Auto-Generate Season Schedule 
**As an** Owner 
**I want to** add, update, and remove users and assign their system roles (Owner, Manager, People)
**So that** only authorized individuals have access to specific features like scheduling and score entry.

**Priority:** P1 
**Independent test:** Verify the Owner can make a new user account and assign them the "Manager" role.
**Acceptance scenarios:** see ### US-5.1- Manage System Users under Acceptance Criteria


### US-5.2: Update Scheduled Games 
**As an** Owner
**I want to** maintain a list of referees and assign them multiple certification types
**So that** Managers know which referees are qualified to make specific sports or leagues.

**Priority:** P1
**Independent test:** Verify a referee can be added to the system and assigned more than one certification type (e.g., Flag Football and Soccer)
**Acceptance scenarios:** see ### US-5.2 - Manage Referees and Certifications under Acceptance Criteria


## Functional Requirements
* **User CRUD:** The system must provide the Owner with the ability to read, update, and delete user accounts and assigns them to a specific role (Owner, Manager,Referee, People)
* **Referee CRUD:** The system must provide the Owner with the ability to maintain the list of active referees
* **Access Control** Only the Owner should be able to access users and referee profiles. 



## Key Entities
* User 
* Referee 

## Initial Data Model

### User 

| Field | Type | Rules |
| --- | --- | --- |
| `user_id`| String | Unique ID, Required |
| `name` | String | Required |
| `email` | String | Required, Unique |
| `role` | Enum | Values: OWNER, MANAGER, REFEREE, PEOPLE, Required |
| `is_active` | Boolean | Required |

### Referee 

| Field | Type | Rules |
| --- | --- | --- |
|`referee_id`| String | Unique ID, Required | 
| `user_id` | String | Links to User ID, Required |
| `certification_types` | Array of Strings | Required (e.g., ["Basketball", "Soccer"]) |
| `is_active` | Boolean | Required |

## Acceptance Criteria

### US-5.1 - Manage System Users

#### Scenario: Owner creates a new Manager user
* **Given** the user is logged in as an "Owner" 
* **And** the user is on the Maintain Users dashboard
* **When** the user enters details for a new user and selects "Manager" as the role
**And** clicks "Save User"
* **Then** the new user should be saved in the database
* **And** the new user should have access to Manager-level features

### US-5.2 - Manage Referees and Certifications

#### Scenario: Owner assigns multiple types to a referee
* **Given** the user is logged in as an "Owner"
* **When** the user navigates to the Maintain Referees screen
* **And** adds a new referee profile for an existing user 
* **And** selects both "Flag Football" and "Basketball" from the certification types list 
* **And** clicks "Save Referee" 
* **Then** the referee's profile should show both types of certification in the system 


## Screen Requirements

### [View: Maintain Users]
* Heading / purpose: Manage system access and assign user roles 
* Primary action: **Add User**
* Fields, dialogs, icon actions:
  * Text fields for Name and Email 
  * Dropdown for User Role (Owner, Manager, Referee, People)
  * Data table listing active users and their roles
  * Edit icon or button 
  * Delete icon or button 
* **Empty state:** "No users have been added to the system."
* **Loading / error:** Standard loading spinner / Text error message for failures

### [View: Maintain Referees]
* Heading / purpose: Manage the list of available referees and their certification types.
* Primary action: **Add Referee**
* Fields, dialogs, icon actions:
  * Dropdown to link a system user
  * Multi-select dropdown or checkboxes for certification types 
  * Data table listing active refereees and their types
  * Edit icon or button 
  * Delete icon or button 
* **Empty state:** "No referees have been added to the system."
* **Loading / error:** Standard loading spinner / Text error message for failures

**App chrome** (if this feature adds or changes it)
* The main menu bar includes "Maintain Users" and "Maintain Refs" links under the "Maintenance dropdown, visible to the owner. 


