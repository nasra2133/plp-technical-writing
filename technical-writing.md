PLP Technical Writing Assignment

A) User Manual Procedure: How to Create a GitHub Repository and Make Your First Commit

1. Purpose

This procedure explains how a beginner can create a GitHub repository, add a file, and make the first commit.

2. Prerequisites

- A computer with an internet connection.
- A web browser such as Google Chrome.
- A GitHub account.
- Git installed on the computer.
- A text editor such as Visual Studio Code.
- Basic computer literacy.

3. Procedure

Step 1: Open GitHub.

Action: Open a web browser and visit https://github.com.

Expected result: The GitHub homepage appears.

Step 2: Sign in.

Action: Enter your GitHub login details.

Expected result: The GitHub dashboard opens.

Step 3: Start creating a repository.

Action: Click the plus (+) icon and select New repository.

Expected result: The repository creation page appears.

Step 4: Enter a repository name.

Action: Type "my-first-project" in the repository name field.

Expected result: The repository name appears in the field.

Step 5: Select repository visibility.

Action: Select Public.

Expected result: The repository is configured to be publicly accessible.

Step 6: Add a README file.

Action: Select the option to add a README file.

Expected result: The README option is selected.

Step 7: Create the repository.

Action: Click Create repository.

Expected result: The new repository page appears with a README file.

Step 8: Open the README file.

Action: Click README.md.

Expected result: The README file opens.

Step 9: Edit the README file.

Action: Click the pencil icon.

Expected result: The README editor appears.

Step 10: Add a project heading.

Action: Type "# My First Project" in the editor.

Expected result: The heading appears in the editor.

Step 11: Save the changes.

Action: Click Commit changes.

Expected result: A confirmation window appears.

Step 12: Confirm the commit.

Action: Enter the commit message "Add project heading" and confirm.

Expected result: The changes are saved in the repository history.

4. Screenshot Description

Include a screenshot of the repository after the first commit. It should show the repository name, README.md, project heading, and latest commit message. Hide any private information before sharing.

5. Troubleshooting

Problem: The user cannot sign in to GitHub.

Solution: Check the username and password for typing errors. If the password has been forgotten, use GitHub's password-reset process.

6. Conclusion

The repository has been created, the README file has been updated, and the first commit has been saved.









B) API Reference Entry: Create a New Task

1. Overview

HTTP Method: POST

Endpoint: "/api/v1/projects/{projectId}/tasks"

Purpose: This endpoint allows an authenticated user to create a new task in a project management application.

Content Type: application/json

2. Request Parameters

2.1 Path Parameter

Name| Type| Required| Description
projectId| String| Yes| The unique ID of the project where the task will be created.

2.2 Query Parameters

No query parameters are required or supported.

2.3 Request Body Parameters

Name| Type| Required| Description
title| String| Yes| The task title; it must not be empty.
description| String| No| Additional details about the task.
assigneeId| String| Yes| The unique ID of the user assigned to the task.
dueDate| String (date)| Yes| The task deadline in YYYY-MM-DD format.
priority| String| Yes| The priority level: low, medium, or high.

3. Required Request Headers

Header| Required| Description
Authorization| Yes| Contains the access token in the format Bearer YOUR_ACCESS_TOKEN.
Content-Type| Yes| Must be application/json.
Accept| Yes| Specifies that the client expects a JSON response.

4. Example Request

Method and path:

POST "/api/v1/projects/PRJ-101/tasks"

Headers:

Authorization: Bearer YOUR_ACCESS_TOKEN
Content-Type: application/json
Accept: application/json

Request body:

{
  "title": "Prepare project presentation",
  "description": "Create slides for the weekly project meeting.",
  "assigneeId": "USR-205",
  "dueDate": "2026-11-15",
  "priority": "high"
}

5. Successful Response

Status code: 201 Created

The task was created successfully.

Example response body:

{
  "id": "TSK-501",
  "projectId": "PRJ-101",
  "title": "Prepare project presentation",
  "description": "Create slides for the weekly project meeting.",
  "assigneeId": "USR-205",
  "dueDate": "2026-11-15",
  "priority": "high",
  "status": "pending",
  "createdBy": "USR-100",
  "createdAt": "2026-10-25T08:30:00Z"
}

6. HTTP Response Codes

Code| Meaning| When It Occurs
201| Created| The task is created successfully.
400| Bad Request| The JSON is malformed or the request structure is invalid.
401| Unauthorized| The access token is missing, invalid, or expired.
403| Forbidden| The user does not have permission to create tasks in the project.
404| Not Found| The project or assignee cannot be found or accessed.
409| Conflict| The request conflicts with an existing resource or application rule.
415| Unsupported Media Type| The request does not use application/json.
422| Unprocessable Entity| One or more fields fail validation.
429| Too Many Requests| The user has exceeded the request rate limit.
500| Internal Server Error| An unexpected server error occurs.
503| Service Unavailable| The server is temporarily unable to process requests.

7. Validation Rules

- The title must contain non-whitespace text.
- The description is optional.
- The assigneeId must identify a valid, eligible user.
- The dueDate must use YYYY-MM-DD format.
- The priority must be low, medium, or high.
- The user must be authenticated and authorized to create tasks in the project.

8. Additional Notes

- The server generates the task ID, creation timestamp, and initial status.
- The createdBy field identifies the authenticated user who created the task.
- Successful and error responses should use JSON.
- Error responses should contain a clear message explaining the problem.

9. Conclusion

The POST endpoint creates a new task inside a project. The client provides valid task details and an access token. When successful, the API returns 201 Created and the new task's details.
