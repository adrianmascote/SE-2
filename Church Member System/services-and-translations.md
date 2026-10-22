# Feature : Services and Translations

## User Stories

### U.S-4.1:

**As a** church administrator 
**I want to** schedule worship services in several languages  with their specific language tag 

**so that** members and visitors are up to date about different services with translation support 
**Priority** P.1 
**Independent test** create a service tagged in "Spanish", save it, and ensure it shows with the correct language tag in the public Calendar.
**Acceptance Criteria** See US 4.1 under Acceptance Criteria

### U.S -4.2

**As a** church translator, **I want to** view the services and translation requirements before the service **so that** I can prepare before the service appropriately. 
**Priority** P.1
**Independent test** create a service and tag it with it's translation requirements, save it, and ensure it shows up in the Calendar along with the translation requirements.
**Acceptance Criteria** See US 4.2 under Acceptance Criteria

### U.S-4.3

**As a** member or guest, **I want to** filter services by languages **so that** I can attend services in my preferred language. 
**Priority** P.1
**Independent test** after a service is created in a specific language, I should be able to filter events in the Public Calendar by a language and only see events in my preferred language. 

### U.S-4.4

**As a** church service coordinator, **I want to** get an alaert or a notification if no translator has been assigned to a specific service 48 hours in advance.
**Priority** P.2
**Independent test** create a service with the spanish translation feature on, advance the service to 48 hours and ensure that a warning appears on the admin's screen.  

### U.S-4.5 

**As a** volunteer translator, **I want to** be able to access uploaded sermons and key scriptures before that particular service **so that** I can review the biblical terms and translate accurately. 
**Priority** P.2
**Indpendent test** Upload a PDF to a sermon regarding the concepts that specific sermon will discuss, and verify that the portal can be accessed through the translator's portal. 
**Acceptance Criteria** See U.S 4.5 under Acceptance Criteria

### U.S-4.6

**As a** church administrator, **I want to** send an automated notification to members if a specific language service was canceled **so that** members are informed of changes before arriving at church. 
**Priority** P.2
**Independent test** Mark a spanish translation service as "Canceled" for a service and ensure it sends a email/SMS to all affected members. 
**Acceptance Criteria** See U.S 4.6 under Acceptance Criteria

## Functional Requirements 

* **FR-1** The system must allow administrators to create, edit, and remove scheduled church services along with it's date, start time, end time, address, primary language, and translation tags. 
* **FR-2** The system must display translation requirements, such as if headsets or a transltion booth is required in the event details. 
* **FR-3** The system must include a public calendar that allows users to filter events by their preferred language. 
* **FR-4** The system must generate an alert on the coordinator's dashboard if no translator has been assigned in 48 hours in advance
* **FR-5** The system must allow administrators to upload and update sermon notes and scripture reference files in a service record 
* **FR-6** The system must restrict who views the attatchment of sermons to assigned translators and administrators 
* **FR-7** The system must triggern an atomatic email/SMS to all the attendees of a certain event when it is marked as canceled. 


## Initial Data Model 

### Service 

| Field | Type | Rules |
|:-- | :--- | :--- |
| 'service_id' | String | Primary Key, Required, Unique |
| 'service_title' | String | Required |
| 'start_time' | Timestamp | Required | 
| 'end_time' | Timestamp | Required, Must be after 'start_time' |
| 'primary_language' | String | Required |
| 'translation_languages' | List<String> | Optional | 
| 'service_status' | Enum| Required, Values: 'SCHEDULED', 'IN_PROGRESS' , 'COMPLETED' , 'CANCELED' |
| 'equipment_requirements' | Enum | Optional, Values: 'HEADSETS', 'BOOTH_ONLY', 'NONE' |
| 'notes_document_url' | String | Optional, Valid URL or file path | 
| 'created_at' | Timestamp | Required, System-generated |

### Service Translation Assignment 

| Field | Type | Rules |
| :--- | :--- | :--- |
| 'assignment_id' | String | Primary Key, Required, Unique | 
| 'service_id' | String | Links to Service ID, Required|
| 'translator_id' | String | Links to Member ID, Required | 
| 'language' | String | Required | 
| 'confirmation_status' | Enum | Values: PENDING, CONFIRMED, DECLINED |
| 'assigned_at' | Timestamp | Auto-generated | 

## Gherkin AC 

'''gherkin 
Feature: Services and Translations 

    Scenario: US 4.1 - Schedule a service with a langauge tag
    Given the administrator is logged in and on the service scheduling page, 
    When they enter the service title "Sunday Morning Worship" 
    And they set the primary language to "English" 
    And they select "Spanish" as a translation language 
    And they save the service 
    Then the service appears on the public church calendar 
    And the service displays the "Spanish" language tag
'''
