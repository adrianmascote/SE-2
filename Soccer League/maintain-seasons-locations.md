# Feature 2: Maintain Seasons and Locations 

## User Stories 

### US-2.1: Manage Seasons 
**As an** Owner 
**I want to** add, update, and remove seasons 
**So that** schedules and games can be grouped by specific leagues and time periods. 

**Priority:** P1 
**Independent test:** Verify the Owner can succesfully create a new season linked to a league with valid start and end dates 
**Acceptance scenarios:** see ### US-2.1 - Manage Seasons under Acceptance Criteria 

### US-2.2: Manage Locations 
**As an** Owner 
**I want to** add, update, and remove physical playing locations 
**So that** games can be accurately scheduled at specific fields or courts 

**Priority:** P1 
**Indpendent test:** Verify the Owner can successfully add a new location with a name and address. 
**Acceptance scenarios:** see ### US-2.2 - Manage Locations under Acceptance Criteria 

## Functional Requirements 
* **Season CRUD:** The system must provide the Owner with the ability to create, read, update, and delete season records. 
* **Location CRUD:** The system must provide the Owner with the ability to create, read, update, and delete location records. 
* **Access Control** Only users with the Onwer role can access the Season and Location maintenance interfaces. 

## Key Entities 
* Season 
* Location 
* User(Owner)

## Initial Data Model 

### Season

| Field | Type | Rules | '=
| --- | | --- | --- | 
| 'season_id' | String | Unique ID, Required | 
| 'league_id' | String | Links to League ID, Required | 
| 'name' | String | Required | 
| 'start_date' | Timestamp | Required | 
| 'end_date' | Timestamp | Required | 
| 'is_active' | Boolean | Required | 

### Location 

| Field | Type | Rules | 
| --- | --- | --- | 
| `location_id` | String | Unique ID, Required | 
| `name` | String | Required (e.g., North Field, Gym A) |
| `address` | String | Optional |
| `is_active` | Boolean | Required | 

## Acceptance Criteria 

### Acceptance Criteria 

### US-2.1 - Manage Seasons 

#### Scenario: Owner successfully creates a new season
* **Given** the user is logged in as an "Owner" 
* **And** the user selects a League, enters "Spring 2027", and provides start/end dates 
* **And** the user clicks "Save Season" 
* **Then** the new season should be saved in the database 
* **And** "Spring 2027" should appear in the active seasons list

### US-2.2 - Manage Locations 

#### Scenario: Owner successfully adds a new location 
* **Given** the user is logged in as an "Owner" 
* **And** the user is on the Maintain Locations dashboard 
* **When** the user enters "Main Soccer Field" as the name and enters the address 
* **And** the user clicks "Save Location" 
* **Then** the new location should be saved in the database
* **And** it should be available for selection when scheduling future games 

## Screen Requirements 

### [View: Maintain Seasons]
* Heading / purpose: Manage the active seasons for the leagues 
* Primary action: **Add Season** 
* Fields, dialogs, icon actions: 
 * Dropdown menu to select the League 
 * Text field for Season Name 
 * Date pickers for Start Date and End Date 
 * Data table listing active seasons 
 * Edit icon or button 
 * Delete icon or button

* **Empty state:** "No seasons have been created. Click Add Season to begin." 
* **Loading / error:** Standard loading spinner / Text error messages for failures 

### [View: Maintain Locations]
* Heading / purpose: Manage the physical fields and courts for the organization 
* Primary action: **Add Location** 
* Fields, dialogs, icon actions: 
 * Text field for Location Name 
 * Text field for Address 
 * Data table listing active locations 
 * Edit icon or button 
 * Delete icon or button 
* **Empty state:** "No locations have been added yet." 
* **Loading / error:** Standard loading spinner / Text error message for failures 

* **App chrome** 
* The main menu bar adds a link to the Maintain Seasons and Maintain Locations screens under the "Maintenance" dropdown for the Owner role


