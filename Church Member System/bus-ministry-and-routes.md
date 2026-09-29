# Feature: Bus Ministry and Routes 

## User Stories

### U.S-2.1 

**As a** bus ministry director **I want to** create and manage bus routes with their corresponding stop locations and assigned cars **so that** there is no confusion and vans do not become overcrowded.
**Priority** P.1
**Independent test** Create a new route labeled "South Route- Van 2" set capacity to 14, add three stop addresses, save them, and ensure that the route and it's stop order is showing correctly in the route overview page. 
**Acceptance Criteria** See US 2.1 under Acceptance Criteria 

### U.S -2.2 

**As a** church member or parent **I want to** request Sunday bus pickup for myself or for my family by providing a pickup address and service time **so that** my family has transportation to and from church services. 
**Priority** P.1
**Independent test** Request a bus ride for two family members with a specific address for the 10 am service and ensure that the request appears on the bus roster. 
**Acceptance Criteria** See US 2.2 Under Acceptance Criteria 

### U.S -2.3 

**As a** bus ministry coordinator, **I want to** assign members and families to the closest available bus route **so that** drivers have an pickup route rather than moving across town. 
**Priority** P.1 
**Independent test** Assign a rider to the "North Route" and ensure that the rider appears on the driver's route in the right sequence. 
**Acceptance Criteria** See U.S 2.3 under Acceptance Criteria 

### U.S-2.4 

**As a** bus driver, **I want to** view a pickup schedule showing a list of passenger names, pickup addresses, and times for my route **so that** I know the driving order and destination for each stop on a service morning. 
**Priority** P.1 
**Independent test** Assign three stops to a route, open the driver's route page, and ensure that the stops and passenger names are shown in the same sequence. 
**Acceptance Criteria** See US 2.4 under Acceptance Criteria 

### U.S-2.5 

**As a** bus driver, **I want to** accessthe primary language and emergency contact information for each passenger on my route schedule **so that** I can communicate with the riders or contact them if there is a missed stop or a delay. 
**Priority** P.2 
**Independent test** Open the driver route schedule, select a stop containing a passenger who's a minor and ensure that the paren't phone number and primary language are shown. 
**Acceptance Criteria** See US 2.5 under Acceptance Criteria 

### U.S-2.6 

**As a** church member or parent, **I want to** cancel or pause a scheduled bus pickup **so that** the bus driver does not make an unnecessary stop at our home. 
**Priority** P.2 
**Independent test** Choose a pickup assignment for an upcoming service and change the status to "Not riding this rideJ"J and ensure that the corresponding address is removed from the driver's route schedule for that day. 
**Acceptance Criteria** See US 2.6 under Acceptance Criteria 


## Initial Data Model 

### Bus Route 

| Field | Type | Rules |
| :--- | :--- | :--- |
| 'route_id' | String | Unique ID, Required |
| 'route_name' | String | Required |
| 'vehicle_name' | String | Required | 
|'max_capacity' | Integer | Required, must be greater than 0 |
|'driver_id' | String | Links to Member ID, Optional | 
|'created_at' | Timestamp | Auto-generated | 

### Route Stops 

| Field | Type | Rules | 
| :--- | :--- | :--- |
|'assignment_id' | String | Unique ID, Required | 
|'route_id' | String | Links to Route ID, Required |
| 'member_id' | String | Links to Member ID, Required |
|'pickup_address' | String | Required |
|'stop_order' | Integer | Required |
|'pickup_time' | String | Required | 
| 'ride_status' | Enum | Values: ACTIVE, NOT_RIDING |

## Gherkin AC 

'''gherkin 
Feature: Bus Ministry and Routes 

    Scenario: US 2.1 - Create a new bus route with stops 
    Given the bus ministry director is logged in  
    When they create a route named "South Route" with capacity 14
    And they add three stop addresses in order
    And they save the route, 
    Then the route appears on the route overview page with the 3 stops. 

    Scenario: US 2.2 - Request a bus pickup for Sunday service 
    Given a church member is logged in 
    When they request a pickup for 2 passengers at "123 Main St" for the 10:00 AM service 
    Then the ride request shows status "ACTIVE"
    And the request appears on the coordinator's pending route roster. 

    Scenario: US 2.3 - Assign a rider to a route  
    Given an approved ride request exists for "Adrian Mascote" 
    When the coordinator assigns "Adrian Mascote" at stop sequence 2 
    Then "Adrian Mascote" appears as stop 3 on the Route driver sheet. 

    Scenario: US 2.4 - View driver pickup schedule. 
    Given "South Route" has three assigned stops in chronological order
    When the bus driver opens the driver route page, 
    Then the passenger names and pickup addresses are displayed in the corresponding sequence. 

    Scenario: US 2.5 - Access language and emergency info for a minor on a bus route
    Given a passenger on the route is a minor with primary language "Spanish" and emergency phone "405 555-5555"
    When the driver views the stop details 
    Then the driver can see "Spanish" as the appropiate language and "405 555-5555" as the emergency contact. 

    Scenario: US 2.6 -Cancel a pickup for a sunday service
    Given a passenger is assigned to a stop on "North Route" 
    When the passenger updates their status to "Not Riding" for the upcoming Sunday 
    Then that passenger's stop is excluded from the driver's schedule for that particular service. 

'''



