# Feature: Attendance and Engagement 

## User Stories 

### U.S-3.1 

**As a** Church usher, **I want to** record a total headcount for each worship service broken down by translations and primary languages **so that** administration knows the total attendance numbers and the language specific needs. 
**Priority** P.1 
**Independent test** Submit a headcount of 120 english attendees and 35 spanish attendees and make sure they are accurately displayed in the service summary. 
**Acceptance Criteria** See US-3.1 under Gherkin AC 

### U.S 3-2

**As a** children's ministry worker, **I want to** check in children into Sunday school classes and record their attendance **so that** teachers have an accurate roster of minors present during the class sessions. 
**Priority** P.1
**Independent test** Select a child's profile from a class roster and mark them as "Present" for the 10.AM class and ensure that their attendance sheet has the correct timestamp. 
**Acceptance Criteria** See US-3.2 under Gherkin AC 

### U.S 3-3

**As a** Pastor, **I want to** view a list of members who have been absent for three or more weeks **so that** I can reach out to check on their well being and offer support. 
**Priority** P.2
**Independent test** Filter the member list by absent >= 3 weeks and ensure that the only members who appear are those who haven't logged-in in that time frame. 
**Acceptance Criteria** See US 3.3 under Gherkin AC 

### U.S 3-4 

**As a** Ministry leader, **I want to** view attendance reports by service, dates, or ministry programs **so that** I can evaluate the changes throughout time and see if we need to update staff or room sizes. 
**Priority** P2 
**Independent test** Generate an attendance report for the past 30 days and make sure it returns the total of all services 
**Acceptance criteria** See US 3.4 under Gherkin AC

# Initial Data Model 

### Service Headcount 

| Field | Type | Rules | 
| :--- | :--- | :---|
|'headcount_id' | String | Unique ID, Required |
|'service_id' | String | Links to Service ID, Required |
|'english_count' | Integer | Required, 0 and greater | 
| 'spanish_count' | Integer | Required, 0 and greater |
|'recorded_by' | String | Links to Member ID, Required | 
|'recorded_at | Timestamp | auto-generated| 

### Class Attendance

|Field |Type | Rules|
| :--- | :--- | :--- |
|'attendance_id' | String | Unique ID, Required| 
|'member_id' | String | Links to Member ID, Required |
|'class_name' | String | Required |
|'attendance_date' | Date | Required |
| 'status' | Enum | Values: PRESENT, ABSENT |
|'check_in_time' | Timestamp | Auto-generated when present|

## Gherkin AC 

'''gherkin 
    Feature: Attendance and Engagement 

    Scenario: US 3.1 - Record service headcount by language 
    Given an usher is logged in and viewing the service attendance sheet
    When they submit a headcount of 120 for English and 35 for Spanish
    Then the headcount record is saved 
    And the service summary displays 120 English attendees and 35 spanish attendees. 

    Scenario: US 3.2 - Check in a child to Sunday School 
    Given a teacher is viewing the roster for 10 AM Sunday school class, 
    When they mark a child's status as "PRESENT" 
    Then the child's status updates to "PRESENT"
    And an attendance entry is created with the date and timestamps.

    Scenario: US 3.3 - Filter list for members absent three or more weeks. 
    Given active members are in the church directory, 
    When the pastor filters the member list for members absent for 3 or more consecutive weeks
    Then only members who have no recorded attendance in the past 3 weeks are displayed. 

    Scenario: US 3.4 - Access attendance summary report over a date range 
    Given worship services and class have recorded attendance over the past 30 days
    When a ministry leader runs an attendance report for the past 30 days
    Then the system shows the added attendance totals across all services within that time range. 

'''