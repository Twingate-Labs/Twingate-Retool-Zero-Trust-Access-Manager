# Prerequisites
* A [Twingate](https://www.twingate.com/) account (Signup for free at https://auth.twingate.com/signup)
* A [Retool](https://retool.com/) account
* A [Google Drive](https://drive.google.com/) space

# Setup Steps
Follow the steps below.

### Create New Google Sheet
• Create new Google Sheet with name `Twingate Zero Trust Access Manager Google Sheet` 
• Create two tabs in the sheet `Owners` and `Requests`
• Alternatively, make a copy of this [Google Sheet](https://docs.google.com/spreadsheets/d/1PqlsEM5fML0RZpjA8ZNfd2Im6F6EuUiIalGgPoZVhOo/edit?usp=sharing)

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

<img width="370" alt="Screenshot 2022-09-07 at 11 40 22" src="https://user-images.githubusercontent.com/26305563/188858743-63b1ba94-5275-4954-993a-f24b8ed58de9.png">

### Setup The Apps

