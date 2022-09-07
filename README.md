# Introduction
This is an example [Retool](https://retool.com/) project that includes 3 Retool Apps to demonstrate just-in-time access management using the Twingate API. Retool is a low-code software platform designed to allow organisations to create internal apps with minimal effort.

Using these apps an organisation can designate owners for Twingate groups and allow users to request access to those groups. These apps are intended to showcase the capabilities of the Twingate API as well as provide a starting point for organisations to develop Zero Trust access flows according to their bespoke requirements.

# Prerequisites
* A [Twingate](https://www.twingate.com/) account (Signup for free [here](https://auth.twingate.com/signup))
* A [Retool](https://retool.com/) account
* A [Google Sheet Space](https://docs.google.com/spreadsheets) 

# Setup Steps
### Create New Google Sheet
* Create new Google Sheet with name `Twingate Zero Trust Access Manager Google Sheet` 
* Create two tabs in the sheet `Owners` and `Requests`
* Alternatively, make a copy of this [Google Sheet](https://docs.google.com/spreadsheets/d/1PqlsEM5fML0RZpjA8ZNfd2Im6F6EuUiIalGgPoZVhOo/edit?usp=sharing)

### Create New Retool Resource
Create new Google Sheets resource with the following configurations.

<img width="700" alt="Screenshot 2022-09-06 at 16 29 08" src="https://user-images.githubusercontent.com/26305563/188854692-ace3e183-86dd-48d0-9c9d-8e25be857512.png">

Create new GraphQL resource with the following configurations.

<img width="700" alt="Screenshot 2022-09-06 at 16 43 41" src="https://user-images.githubusercontent.com/26305563/188855158-66610a7a-bde7-4ff5-bcd0-fd5cd861750c.png">

Note: The Twingate API key can be generated in the Twingate Admin Console.

### Download The Latest Release
* [Twingate Zero Trust Access Manager - Admin.json](https://github.com/Twingate-Labs/Twingate-Retool-Zero-Trust-Access-Manager/releases/latest/download/Twingate.Zero.Trust.Access.Manager.-.Admin.json)
* [Twingate Zero Trust Access Manager - User Dashboard.json](https://github.com/Twingate-Labs/Twingate-Retool-Zero-Trust-Access-Manager/releases/latest/download/Twingate.Zero.Trust.Access.Manager.-.User.Dashboard.json)
* [Twingate Zero Trust Access Manager - Group Owner Dashboard.json](https://github.com/Twingate-Labs/Twingate-Retool-Zero-Trust-Access-Manager/releases/latest/download/Twingate.Zero.Trust.Access.Manager.-.Group.Owner.Dashboard.json)

### Create New Retool Apps
Create three new apps using the Retool "Create New From JSON", one for each downloaded JSON file.

<img width="400" alt="Screenshot 2022-09-07 at 11 40 22" src="https://user-images.githubusercontent.com/26305563/188858743-63b1ba94-5275-4954-993a-f24b8ed58de9.png">

### Setup The Apps

#### Twingate Zero Trust Access Manager - Admin
Change the resource to the previously created resource `Twingate API` for the following queries:
* getAllGroups
* getAllUsers

<img width="500" alt="Screenshot 2022-09-07 at 11 51 45" src="https://user-images.githubusercontent.com/26305563/188861068-32661443-ca73-4973-8da4-cf4d4510e925.png">

Change the resource to the previously created resource `Twingate Zero Trust Access Manager Database` and spreadsheet to the previously created Google Sheet `Twingate Zero Trust Access Manager Google Sheet` for the following queries:
* getAllOwners
* updateRemoveOwner
* updateAddOwner
* updateAddOwnerNewRow

<img width="800" alt="Screenshot 2022-09-07 at 11 53 59" src="https://user-images.githubusercontent.com/26305563/188862338-a95ea2e7-d064-48b8-958a-36d8c37d48e2.png">
<img width="800" alt="Screenshot 2022-09-07 at 11 56 13" src="https://user-images.githubusercontent.com/26305563/188862385-d259379a-fb08-4339-b2ef-a8faa913f38d.png">

Note: make sure no other configurations of these queries are changed.


#### Twingate Zero Trust Access Manager - User Dashboard
Change the resource to the previously created resource `Twingate API` for the following queries:
* getAllGroups
* getAllUsers

Change the resource to the previously created resource `Twingate Zero Trust Access Manager Database` and spreadsheet to the previously created Google Sheet `Twingate Zero Trust Access Manager Google Sheet` for the following queries:
* getAllOwners
* getAllRequests
* updateAddRequest


#### Twingate Zero Trust Access Manager - Group Owner Dashboard
Change the resource to the previously created resource `Twingate API` for the following queries:
* getAllGroups
* addUserToGroupMutation

Change the resource to the previously created resource `Twingate Zero Trust Access Manager Database` and spreadsheet to the previously created Google Sheet `Twingate Zero Trust Access Manager Google Sheet` for the following queries:
* getAllOwners
* getAllRequests
* updateApproveRequestStatus
* updateDenyRequestStatus

# High Level Architecture
### Twingate Zero Trust Access Manager - Admin
The app is used to add/revoke group ownerships. Only admin users should have the permission to this app. The SYNCED groups (e.g. Okta synced groups) are not shown within this app. The group ownership details are stored in the Google Sheet (Owners tab).

### Twingate Zero Trust Access Manager - User Dashboard
The app can be used by users to request access to Twingate groups. The user can only make a request to groups that:
* they are not a member of
* has at least one owner

The request is stored in the Google Sheet (Requests tab). Further, the user's request status is also shown within this app. 


### Twingate Zero Trust Access Manager - User Dashboard
The app can be used by group owners to approve or reject requests. The group owners can only approve/reject requests that they are owner of.

The Twingate API (GraphQL mutation) is used to add the user to the Twingate group if the request is approved. The Google Sheet would also be updated (Requests tab) to reflex the request is approved/rejected.

