# Feature 1: Maintain Sports Leagues 



## User Stories 

### US-1.1: Manage Sports 

**As a** owner
**I want to** add, update, and remove sports 
**So that** the system accurately reflects the athletic programs offered. 

**Priority:** P1 
**Independent test:** Verify the owner can create a new sport and see it in the active sports list. 
**Acceptance scenarios:** see ### US-1.1 under Gherkin AC 

### US-1.2: Manage Leagues 

**As an** Owner 
**I want to** create and manage specific leagues under each parent sport 
**So that** teams and schedules can be categorized correctly (e.g., Men's Soccer).

**Priority:** P1 
**Independent test:** Verify the Owner can create a new league linked to an existing sport. 
**Acceptance scenarios:** see ### US-1.2 under Gherkin AC 

### US-1.3: Restrict Maintenance Access 

**As a** system administrator 
**I want to** restrict access to the maintenance screents to only the Owner role
**So that** unauthorized users like managers or the public can't alter details about core league games. 

**Priority:** P1 
**Independent test:** Verify a logged-in manager is denied access and redirected when he or she attempts to log in to the maintenance screen. 

# Functional Requirements 
* **Sport CRUD:** The system MUST provide the Owner with the ability create, read, update, and delete sport records. 
* **League CRUD:** The system must provide the owner with the ability to create, read, update, and delete league records associated with a parent sport. 
* **Access Control:** Only users with the owner role can access the sport maintenance interfaces. Managers, referees, and the public should not have access to those views. 

# Key Entities 
* Sport 
* League 
* User(Owner)

# Initial Data Model 

### Sport 

| Field | Type | Rules | 
| --- | --- | ---|
| `sport_id` | String | Unique ID, Required| 
| `name` | String | Required | 
| `is_active` | Boolean | Required | 

### League 

| Field | Type | Rules | 
| --- | --- | --- | 
| `league_id` | String| Unique ID, Required | 
| `sport_id` | String | Links to League ID, Required |
| `name` | String | Required| 


# Gherkin AC

### US-1.1 - Manage Sports 
#### Scenario: Owner successfully creates a new sport 
* **Given** the user is logged in as an "Owner" 
* **And** the user is on the Maintain Sports dashboard 
* **When** the user enters "Flag" football" into the sport name field 
* **And** the user clicks "Save Sport" 
* **Then** the new sport should be saved in the database
* **And** "Flag" football" should appear in the active sports list

### US-1.2 - Manage Leagues 
#### Scenario: Owner creates a new league under an existing sport
* **Given** the user is logged in as an "Owner" 
* **And** the sport "Basketball" exists in the system 
* **When** the user navigates to Maintain Leagues 
* **And** selects "Basketball" from the sport dropdown 
* **And** enters "Women's" as the league name 
* **And** clicks "Save League" 
* **Then** the "Women's" League should be created and linked to "Basketball" 

### US-1.3 - Restrict Maintenance Access 
#### Scenario: Manager is denied access to maintenance screens 
* **Given** the user is logged in as a "Manager" 
* **When** the user tries to navigate to the Maintain Sports screen 
* **Then** the system should redirect the user to the Manager dashboard 
* **And** display a permission denied error message

## Screen Requirements 

### [View Maintain Sports]
* Heading / purpose: Manage the core sports offered by the organization 
* Primary action: **Add Sport** 
* Fields, dialogs, icon actions: 
 * Textfield for Sport Name 
 * Data table listing active sports 
 * Edit icon or button 
 * Delete icon or button 
* **Emoty state:** "No sports have been created yet. Click Add Sport to begin." 
* **Loading / error:** Standard loading spinner / Text error message for failures 

### [View: Maintain Leagues]
* Heading / purpose: Manage the leagues associated with each sport 
* Primary action: **Add League** 
* Fields, dialogs, icon actions: 
 * Dropdown menu to select the Parent Sport 
 * Text field for League Name (e.g., Men's, Women's) 
 * Datatable listing active leagues 
 * Edit icon or button 
 * Delete icon or button 
* **Empty state:** "No leagues have been created for this sport." 
* **Loading / error:** Standard loading spinner / Text error message for failures 

**App chrome** (if this feature adds or changes it)
* The main menu bar adds a "Maintenance" dropdown menuy visible only to the Owner role containing links / buttons to go to the Maintain Sports and Maintain Leagues screens. 

