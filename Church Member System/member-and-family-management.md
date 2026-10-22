# Feature: Member and Family management 

## User Stories 

### U.S 1.1 

**As a** church admistrator, **I want to** create and update an individual member's profile with their contact information, address, and membership status, **so that** the church has an updated directory.
**Priority** P.1
**Independent test** create a new member with their full name, phone number, email, address, and status "Active". Save it, and ensure the member appears with the correct information in the member list. 

### U.S 1.2 

**As a** church administrator, **I want to** group individual members into household units and assign a primary head of household **so that** communication with the family is facilitated. 
**Priority** P.1 
**Independent test** Create a family unit called the "Hernandez" family, assign two adult profiles and two child profiles to it, ensure that the household view lists all four members grouped together. 

### U.S 1.3 

**As a** church administrator or volunteer, **I want to** see the preferred primary and secondary languages for each household and member, **so that** administration knows how to better communicate with each family. 
**Priority** P.2.
**Independent test** Open a member's profile, set primary language to "Spanish" and secondary to "English", save, and make sure that the members appear with their corresponding language. 
**Acceptance Criteria** See U.S 1.3 under Acceptance Criteria 

### U.S-1.4 

**As a** children's ministry worker, **I want to** view a child's linked parents or gaurdians, emergency contact numbers, and medical notes **so that** parents can be reached immediately in case of an emergency. 
**Priority** P.1 
**Independent test** Loook up a child's profile, 
**Acceptance Criteria** See US 1.4 under Acceptance Criteria 

### U.S-1.5 

**As a** church administrator **I want to** filter the member list by last name, membership status or address **so that** admin can quickly pull up records during check in's. 
**Priority** P.2
**Independent test** Search in the directory with a partial last name and ensure that only matching active and inactive records are returned. 
**Acceptance Criteria** See U.S-1.5 under Acceptance Criteria 

### U.S-1.6 

**As a** church administrator, **I want to** be able to mark a member's status as "Visitor", "Active", or "Inactive" instead ofo deleting their record **so that** the church saves historical records and attendance while keeping the active roster clean. 
**Priority** P.2 
**Independent test** Change an existing member's status from "Active" to "Inactive" and make sure that they don't appear in the "Active " roster. 
**Acceptance Criteria** See U.S-1.6 under Acceptance Criteria 

## Functional Requirements 

* **FR-1** The system must store the member's first name, last name, phone number, email, address, and membership status.
* **FR-2** The system must validate email address formatting if an email is provided.
* **FR-3** The system must allow one to group individual member records into household family units with a head of household. 
* **FR-4** The system must store primary and optional secondary languages for both members and the household records
* **FR-5** The system must store the emergency contact phone numbers and medical/allergy notes for any member marked as a minor. 
* **FR-6** The system must allow members to be searched and filtered in the directory by last name, membership status, addresss, or language. 
* **FR-7** The system must not permanently delete member records and instead turn it 

## Initial Data Model 

### Family Household 

| Field | Type | Rules | 
| :--- | :--- | :--- |
|'family_id' | String | Unique ID, Required |
|'family_name' | String | Required | 
|'primary_address' | String | Required |
| 'primary_phone' | String | Optional |
| 'created_at' | Timestamp | Auto-generated |

### Member 

| Field | Type | Rules |
|:---| :---| :--- |
| 'member_id' | String | Unique ID, Required |
|'family_id' | String | Links to Family ID, Optioal |
|'first_name | String | Required |
| 'last_name' | String | Required | 
|'role_in_family' | Enum | Values: HEAD_OF_HOUSEHOLD, SPOOUSE, CHILD, OTHER   |
| 'membership_status' | Enum | Values: VISITOR, ACTIVE, INACTIVE |
|'primary language' |String | Required | 
| 'secondary_language' | String | Optional |
|'phone_number' | String | Optional |
| 'phone_number' | String | Optional |
| 'email' | String | Optional, Valid email format|
|'is_minor' | Boolean | Required |
| 'medical_notes' | String | Required if is_minor is true | Timestamp | Auto-generated|

## Gherkin AC 

'''gherkin 

Feature: Member and Family Management 

    Scenario: US 1.1 - Create a new member profile
    Given an administrator is logged into the system
    When they enter "Adrian" as a first name, "Mascote" as a last name, and set the status to active
    And they save the profile
    Then the system creates a new member profile 
    And "Adrian Mascote" appears with an "Active" tag in the directory. 

    Scenario US 1.2 - Group members into a family household
    Given that there are existing member profiles for two adults and two children 
    When the administrtor creates a family unit named "Mascote" 
    And assignes the four members to the "Mascote" family unit
    And designates one member as the head of household
    Then all four members are linked under the "Mascote" houshold view. 

    Scenario US 1.3 - Set and view language preferences. 
    Given an administreator is editing a member's profile
    When they select "Spanish" as the primary langiage and "English as the secondary laanguage 
    And they save the profile
    Then the member's profile displays "Spanish" as primary and "English" as secondary. 

    Scenario US 1.4 - View safety and emergency notes for a minor. 
    Given a member's profile is marked as a minor with an emergency phone " 405 777 - 7777" and a medical note tagged with "Asthma"  
    When a children's ministry worker opes the child's profile
    Then the emergency phone number as well as the medical note "Asthma" is visible. 

    Scenario US 1.5 - Search the directory by partial last name
    Given there are active and inactive members in the member list, 
    When an administrator searchers for partial last name "Mas" 
    Then the search results shows matching active and inactive records containing "Mas" 

    Scenario US 1.6 - Deactivate a member instead of deleting them. 
    Given a member profile exists with status "Active" 
    When the administrator updates the status to "Inactive" 
    Then the member is saved with the status "Inactive" 
    And the member no longer shows on the "Active" member roster
'''



