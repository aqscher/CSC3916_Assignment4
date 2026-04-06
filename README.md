# CSC3916 Assignment 4 - Movie API

A RESTful API for managing movies and reviews, built with Node.js, Express, and MongoDB. Supports user authentication via JWT, CRUD operations on movies, and review aggregation using MongoDB's `$lookup`.

## API Endpoints

### Authentication

| Method | Route | Auth | Description |
|--------|-------|------|-------------|
| POST | `/signup` | No | Register a new user. Body: `{ name, username, password }` |
| POST | `/signin` | No | Sign in and receive a JWT token. Body: `{ username, password }` |

### Movies

| Method | Route | Auth | Description |
|--------|-------|------|-------------|
| GET | `/movies` | JWT | Get all movies. Add `?reviews=true` to include reviews via aggregation. |
| GET | `/movies/:title` | JWT | Get a movie by title. Add `?reviews=true` to include reviews. |
| POST | `/movies` | JWT | Create a new movie. Body: `{ title, releaseDate, genre, actors }` |
| PUT | `/movies/:title` | JWT | Update a movie by title. |
| DELETE | `/movies/:title` | JWT | Delete a movie by title. |

### Reviews

| Method | Route | Auth | Description |
|--------|-------|------|-------------|
| GET | `/reviews` | No | Get all reviews. |
| POST | `/reviews` | JWT | Create a review. Body: `{ movieId, username, review, rating }` |
| DELETE | `/reviews` | No | Delete a review. Body: `{ id }` |

## Installation

1. Clone the repository:
   ```bash
   git clone <your-repo-url>
   cd CSC3916_Assignment4
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Create a `.env` file in the root directory with the following variables:
   ```
   DB=<your-mongodb-connection-string>
   SECRET_KEY=<your-jwt-secret>
   ```

4. Start the server:
   ```bash
   npm start
   ```

   The server runs on `http://localhost:8080` by default.

## Running Tests

```bash
npm test
```  

## Run API Tests in Postman

[<img src="https://run.pstmn.io/button.svg" alt="Run In Postman" style="width: 128px; height: 32px;">](https://app.getpostman.com/run-collection/28607556-fcec2f0f-9fc2-4ee8-9108-ddc043677b15?action=collection%2Ffork&source=rip_markdown&collection-url=entityId%3D28607556-fcec2f0f-9fc2-4ee8-9108-ddc043677b15%26entityType%3Dcollection%26workspaceId%3D67aa54f6-b050-4e6f-bb0b-5bae3e50a40c#?env%5BScher-hw4%5D=W3sia2V5IjoidXNlcm5hbWUiLCJ2YWx1ZSI6InVzZXJuYW1lMSIsImVuYWJsZWQiOnRydWUsInR5cGUiOiJkZWZhdWx0Iiwic2Vzc2lvblZhbHVlIjoibmV3X3VzZXJuYW1lMTIzIiwiY29tcGxldGVTZXNzaW9uVmFsdWUiOiJuZXdfdXNlcm5hbWUxMjMiLCJzZXNzaW9uSW5kZXgiOjB9LHsia2V5IjoicGFzc3dvcmQiLCJ2YWx1ZSI6InBhc3N3b3JkMSIsImVuYWJsZWQiOnRydWUsInR5cGUiOiJkZWZhdWx0Iiwic2Vzc2lvblZhbHVlIjoibmV3X3Bhc3N3b3JkMTIzIiwiY29tcGxldGVTZXNzaW9uVmFsdWUiOiJuZXdfcGFzc3dvcmQxMjMiLCJzZXNzaW9uSW5kZXgiOjF9LHsia2V5IjoidG9rZW4iLCJ2YWx1ZSI6InRlc3QiLCJlbmFibGVkIjp0cnVlLCJ0eXBlIjoiZGVmYXVsdCIsInNlc3Npb25WYWx1ZSI6IkpXVC4uLiIsImNvbXBsZXRlU2Vzc2lvblZhbHVlIjoiSldUIGV5SmhiR2NpT2lKSVV6STFOaUlzSW5SNWNDSTZJa3BYVkNKOS5leUpwWkNJNklqWTVaRE13WkRnMk5UVTVNelZrWTJFeFlqQmtNakZoT1NJc0luVnpaWEp1WVcxbElqb2libVYzWDNWelpYSnVZVzFsTVRJeklpd2lhV0YwSWpveE56YzFORE01TWpVMUxDSmxlSEFpT2pFM056VTBOREk0TlRWOS53Z09FRDJ3cHNWYTE5R1hQV0p0SUV2WS10WHBoZE9NcjhUeHZzS0JJeTRZIiwic2Vzc2lvbkluZGV4IjoyfSx7ImtleSI6Im1vdmllSWQiLCJ2YWx1ZSI6InRlc3QiLCJlbmFibGVkIjp0cnVlLCJ0eXBlIjoiZGVmYXVsdCIsInNlc3Npb25WYWx1ZSI6IjY5ZDJmZjNlMjcyMWJkYWUxOGU1NjQ0OCIsImNvbXBsZXRlU2Vzc2lvblZhbHVlIjoiNjlkMmZmM2UyNzIxYmRhZTE4ZTU2NDQ4Iiwic2Vzc2lvbkluZGV4IjozfV0=)

### In case environment variables did not get shared properly with the recent postman updates, here they are:
  
```
username : newUser99
password : newPw99
token : null
movieId : null
```  

[<img src="https://run.pstmn.io/button.svg" alt="Run In Postman" style="width: 128px; height: 32px;">](https://app.getpostman.com/run-collection/28607556-fcec2f0f-9fc2-4ee8-9108-ddc043677b15?action=collection%2Ffork&source=rip_markdown&collection-url=entityId%3D28607556-fcec2f0f-9fc2-4ee8-9108-ddc043677b15%26entityType%3Dcollection%26workspaceId%3D67aa54f6-b050-4e6f-bb0b-5bae3e50a40c#?env%5BScher-hw4%5D=W3sia2V5IjoidXNlcm5hbWUiLCJ2YWx1ZSI6InVzZXJuYW1lMSIsImVuYWJsZWQiOnRydWUsInR5cGUiOiJkZWZhdWx0Iiwic2Vzc2lvblZhbHVlIjoibmV3VXNlcjkiLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6Im5ld1VzZXI5Iiwic2Vzc2lvbkluZGV4IjowfSx7ImtleSI6InBhc3N3b3JkIiwidmFsdWUiOiJwYXNzd29yZDEiLCJlbmFibGVkIjp0cnVlLCJ0eXBlIjoiZGVmYXVsdCIsInNlc3Npb25WYWx1ZSI6Im5ld1B3OSIsImNvbXBsZXRlU2Vzc2lvblZhbHVlIjoibmV3UHc5Iiwic2Vzc2lvbkluZGV4IjoxfSx7ImtleSI6InRva2VuIiwidmFsdWUiOiJ0ZXN0IiwiZW5hYmxlZCI6dHJ1ZSwidHlwZSI6ImRlZmF1bHQiLCJzZXNzaW9uVmFsdWUiOiJKV1QuLi4iLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6IkpXVCBleUpoYkdjaU9pSklVekkxTmlJc0luUjVjQ0k2SWtwWFZDSjkuZXlKcFpDSTZJalk1WkRNeE1HSTVOVFU1TXpWa1kyRXhZakJrTWpGaU9DSXNJblZ6WlhKdVlXMWxJam9pYm1WM1ZYTmxjamtpTENKcFlYUWlPakUzTnpVME5EQXdOaklzSW1WNGNDSTZNVGMzTlRRME16WTJNbjAuR3piSWVlN0lqWlY5QmFkNWxmbjFlZng3Y25JeFRpbEFFTGhMaEZONFpCOCIsInNlc3Npb25JbmRleCI6Mn0seyJrZXkiOiJtb3ZpZUlkIiwidmFsdWUiOiJ0ZXN0IiwiZW5hYmxlZCI6dHJ1ZSwidHlwZSI6ImRlZmF1bHQiLCJzZXNzaW9uVmFsdWUiOiI2OWQyZmYzZTI3MjFiZGFlMThlNTY0NDgiLCJjb21wbGV0ZVNlc3Npb25WYWx1ZSI6IjY5ZDJmZjNlMjcyMWJkYWUxOGU1NjQ0OCIsInNlc3Npb25JbmRleCI6M31d)