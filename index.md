<img width="2880" height="1556" alt="image" src="https://github.com/user-attachments/assets/ec6d0859-3cda-48f8-8da2-1174ac1da487" /># RIBows

## Table of Contents
- [Overview](#overview)
- [Admin Features](#admin-features)
- [Deployment](#deployment)
- [User Guide](#user-guide)
- [Pages](#pages)
- [Community Feedback](#community-feedback)
- [Developer Guide](#developer-guide)
- [Development History](#development-history)
- [Team](#team)

## Overview
RIBows is a website built by University of Hawaii at Manoa (UHM) students, for UHM students, to easily search for, discover, and join Registered Independent Organizations (RIOs). RIBows gives users the flexibility to browse trending RIOs or search for specific RIOs based on interests or keywords. If a user sees an RIO that interests them, they can use the bookmarking feature to save the RIO for easy future reference. Once a user finds an RIO they want to join, simply clicking the "apply" button allows them to send an application to the RIO admin.

## Admin Features
Via an admin account, RIO admins can edit their RIO, allowing them to customize its image, description, and more. 

## Deployment
The RIBows application was deployed on Vercel through this [link](https://ri-bows.vercel.app/)

## User Guide
This section provides a walkthrough of the RIBows user interface and its capabilities.

## Pages
### Landing
The landing page is presented to users when they visit the top-level URL of the site. This page explains basic usage of the website and displays currently trending RIOs.

![](images/landingPage.png)

### Sign In / Sign Up
Users can access the sign in page via the "Sign In" button on the navbar. There, the user has the option to either sign in or create a new account.

![](images/signIn.png)

On the sign up page, users are able to create their account and specify the types of RIOs they are interested in.

![](images/signUp.png)

### Edit Profile
![](images/editProfile.png)
On this page, users are able to update their first and last names, change their club interests, and see a simple preview of how their profile information will appear.

### Bookmarked
Logged in users can view RIOs they've bookmarked by pressing "Saved" on the navbar.

![](images/bookmarks.png)

### Search
The "Search" page accessible from the navbar allows users to search for RIOs with keywords of their choice. Users also have the option to filter RIOs based on interests, date added, and more.

![](images/search.png)

### Admin
If the user signs in with an admin account, they will be able to add their RIO's details from the admin page.

![](images/addRio.png)

## Community Feedback
We have also added a feedback page. If the user would like, they could take a couple of minutes to fill out the [RIBows Feedback Form](https://ri-bows.vercel.app/feedback). The form asks for the user's email address and a text area to include feedback/improvements for our app.

![](images/feedback.png)

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
Run Prisma migrations: <pre><code>npx prisma migrate dev</code></pre>

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
      - Create a new folder under <code>src/app</code> (e.g. <code>about</code>)
      - Add a <code>page.tsx</code> file and export a React component

 ### 6. Linting and tests
Run ESLint to catch issues before committing: <pre><code>npm run lint</code></pre>

## Development History

### Milestone 1: Mockup development
The goal of Milestone 1 was to create a minimal set of mockup pages to provide a skeleton for the final website. The page designs are still ongoing and most functionality has not been implemented.

Milestone 1 was managed using [RIBows GitHub Project Board M1](https://github.com/orgs/RI-Bows/projects/2):

![](images/M1.png)

### Milestone 2: Database implementation
The goal of Milestone 2 was to finish up the mockup pages, connect the spreadsheet of RIOs to the database, and begin to implement database functionalities.

Milestone 2 is managed using [RIBows GitHub Project Board M2](https://github.com/orgs/RI-Bows/projects/6)

![](images/M2.png)

## Team
RIBows is designed, implemented, and maintained by UHM students [Gerric Abe](https://g3rr1c.github.io/), [Tyler Jordan Acasio](https://tjlacasio.github.io/), [Charles Brown III](https://cbxiii.github.io/), [Ethan Chiu](https://ethnchiu.github.io/), and [Kate Hamada](https://katehamada.github.io/)

Here is the link to our [team contract](https://docs.google.com/document/d/15l0wCt8EKYHtAWk8A6nEZsd7tPoo2wtClHtCA2XVC9Y/edit?usp=sharing), which outlines criteria we adhere to to effectively work together and develop this website.
