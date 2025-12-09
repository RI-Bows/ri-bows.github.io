### RIBows

## Table of Contents
- [Overview](#overview)
- [Deployment](#deployment)
- [User Guide](#user-guide)
- [Community Feedback](#community-feedback)
- [Continuous Integration](#continuous-integration)
- [Developer Guide](#developer-guide)
- [Development History](#development-history)
- [Team](#team)

## Overview
RIBows is a website built by University of Hawaii at Manoa (UHM) students, for UHM students, to easily search for, discover, and join Registered Independent Organizations (RIOs). RIBows gives users the flexibility to browse trending RIOs or search for specific RIOs based on interests or keywords. If a user sees an RIO that interests them, they can use the bookmarking feature to save the RIO for easy future reference. Once a user finds an RIO they want to join, simply clicking the "apply" button allows them to send an application to the RIO admin.

## Deployment
The RIBows application was deployed on Vercel through this [link](https://ri-bows.vercel.app/)

## User Guide
This section provides a walkthrough of the RIBows user interface and its capabilities.

### Landing Page
The landing page is presented to users when they visit the top-level URL of the site. This page explains basic usage of the website and displays currently trending RIOs.

![](images/landingPage.png)

### Sign In / Sign Up Pages
Users can access the sign in page via the "Sign In" button on the navbar. There, the user has the option to either sign in or create a new account.

![](images/signIn.png)

On the sign up page, users are able to create their account and specify the types of RIOs they are interested in.

![](images/signUp.png)

### Edit Profile Page
![](images/editProfile.png)
On this page, users are able to update their first and last names, change their club interests, and see a simple preview of how their profile information will appear.

### Bookmark Page
Logged in users can view RIOs they've bookmarked by pressing "Saved" on the navbar.

![](images/bookmarks.png)

### Search Page
The "Search" page accessible from the navbar allows users to search for RIOs with keywords of their choice. Users also have the option to filter RIOs based on interests, date added, and more.

![](images/search.png)

### About Us Page
There's also an about us page that tells you information about the creators of RIBows.

![](images/aboutUs.png)

### Edit RIO Page
If the user is logged in a club account they will have access to the information that their RIO will display.

![](images/editRIO.png)

### Admin  Privileges
As an admin you can add RIO's to the database:

![](images/addRIO.png)

As well as edit any RIO allowing them to customize its image, description, and more by using the admin search tab and then clicking on the edit button. (currently not done)
![](images/editRIOAdmin.png)

### Feedback Page
We have also added a feedback page. If the user would like, they could take a couple of minutes to fill out the [RIBows Feedback Form](https://ri-bows.vercel.app/feedback). The form asks for the user's email address and a text area to include feedback/improvements for our app.

![](images/feedback.png)

## Community Feedback
These were the [responses](https://docs.google.com/spreadsheets/d/1WJVJc5hPyHeSnU0xMmSv9FGXRyTyEozgusYMW37m28s/edit?usp=sharing) we have so far from our feedback form. It seemed like even though many undergraduate UH students know about RIO's they still were able to learn something new away from our website. 

## Developer Guide
This section explains how to download, install, run, and modify the RIBows system.

### Prerequisites
Before you begin, make sure you have:

- **Git**
- **Node.js** (v20.x recommended) and **npm**
- A **PostgreSQL** database  
  - We use **Neon Postgres** in production, but any Postgres instance works for local dev.
- A GitHub account (if you are collaborating with the RI-Bows organization)

### 1. Getting the source code
  <pre><code>git clone https://github.com/RI-Bows/RIBows.git
cd RIBows
git checkout -b issue-15
</code></pre>

### 2. Environment variables and database

Create a <code>.env</code> file in the project root with values like:
<pre><code>DATABASE_URL="postgresql://USER:PASSWORD@HOST:PORT/DATABASE?sslmode=require" 
DATABASE_URL_UNPOOLED="postgresql://USER:PASSWORD@HOST:PORT/DATABASE?sslmode=require" 
NEXTAUTH_URL="http://localhost:3000"
NEXTAUTH_SECRET="some-random-secret-string"
</code></pre>
    
Install dependencies:
<pre><code>npm install</code></pre>
Run Prisma migrations:<code>npx prisma migrate dev</code>

### 3. Running the app locally
   <pre><code>npm run dev </code></pre>
   <p>Then open <a href="http://localhost:3000">http://localhost:3000</a>.</p>
From there you can visit the landing page, sign in with a test account (e.g. <code>johnson@hawaii.edu</code>).Try search, bookmarks, and admin functionality.

### 4. Project structure 
<ul>
  <li>src/app/page.tsx – Landing page</li>
  <li>src/app/search/page.tsx– Search RIOs</li>
  <li>src/app/trending/page.tsx –  Trending RIOs</li> 
  <li>src/app/bookmarks/page.tsx – Bookmarked RIOs</li>
  <li>src/app/addclub/page.tsx – Admin add-RIO page</li>
  <li>src/app/editClub/page.tsx – Club edit-RIO page</li>
  <li>src/app/feedback/page.tsx – Feedback form</li>
  <li>src/components/ – Shared React components</li>
  <li>src/lib/dbActions.ts– Database helper functions</li>
  <li>prisma/schema.prisma – Prisma data model</li>
  <li>styles/globals.css – Global theme and styling</li>
</ul>

### 5. Making changes
Adding a new page
<br/>
- Create a new folder under <code>src/app</code> (e.g. <code>about</code>)
- Add a <code>page.tsx</code> file and export a React component
  <br/>
Updating the Data model
- Edit <code>prisma/schema.prisma</code>
- Run <code>npx prisma migrate dev -- name your_migration_name</code>
- Update any queries and UI that depend on the changed model.


### 6. Linting and tests
Run ESLint to catch issues before committing: <code>npm run lint</code>

## Continuous Integration

CI badges:
[![ESLint](https://github.com/RI-Bows/RIBows/actions/workflows/eslint.yml/badge.svg)](https://github.com/RI-Bows/RIBows/actions/workflows/eslint.yml)
[![Playwright](https://github.com/RI-Bows/RIBows/actions/workflows/playwright.yml/badge.svg)](https://github.com/RI-Bows/RIBows/actions/workflows/playwright.yml)

RIBows uses [GitHub Actions](https://docs.github.com/en/free-pro-team@latest/actions) to automatically run ESLint and Playwright Tests each time a commit is made to the default branch.  You can see the results of all recent "workflows" at [https://github.com/RI-Bows/RIBows/actions](https://github.com/RI-Bows/RIBows/actions).

The workflow definition files are quite simple and is located at
[.github/workflows](https://github.com/RI-Bows/RIBows/tree/main/.github/workflows).

## Development History

### Milestone 1: Mockup development
The goal of Milestone 1 was to create a minimal set of mockup pages to provide a skeleton for the final website. The page designs are still ongoing and most functionality has not been implemented.

Milestone 1 was managed using [RIBows GitHub Project Board M1](https://github.com/orgs/RI-Bows/projects/2):

![](images/M1.png)

### Milestone 2: Database implementation
The goal of Milestone 2 was to finish up the mockup pages, connect the spreadsheet of RIOs to the database, and begin to implement database functionalities.

Milestone 2 is managed using [RIBows GitHub Project Board M2](https://github.com/orgs/RI-Bows/projects/6)

![](images/M2.png)

### Milestone 3:
The goal of Milestone 3 was to improve our system's functionality from M2, incorporate real data in the system, find at least 5 UH community members to try out the system and provide feedback, and implement acceptance testing.

Milestone 3 is managed using [RIBows GitHub Project Board M3](https://github.com/orgs/RI-Bows/projects/11)

![](images/M3.png)

## Team
RIBows is designed, implemented, and maintained by UHM students [Gerric Abe](https://g3rr1c.github.io/), [Tyler Jordan Acasio](https://tjlacasio.github.io/), [Charles Brown III](https://cbxiii.github.io/), [Ethan Chiu](https://ethnchiu.github.io/), and [Kate Hamada](https://katehamada.github.io/)

Here is the link to our [team contract](https://docs.google.com/document/d/15l0wCt8EKYHtAWk8A6nEZsd7tPoo2wtClHtCA2XVC9Y/edit?usp=sharing), which outlines criteria we adhere to to effectively work together and develop this website.
