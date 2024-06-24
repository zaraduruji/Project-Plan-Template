# Project-Plan-Template
Google Doc Link: https://docs.google.com/document/d/1OktIvD47OyR73-KfkBmPp0oqjj7eGf3xwKP1whVLRs0/edit?usp=sharing
Meta University Eng Project Plan Template     
Fill in blanks (enclosed by brackets []) and remove red text as you work through writing your project plan. Your project plan should be a living document and can be changed as you progress through the internship. Make sure to work on this document together with your manager to get feedback, as well as ensuring your project meets the requirements and expectations in the Project Guide.

Intern Link
Intern: Zara Duruji
Intern Manager: Rodrigo Andrade
Intern Director: Carl Taylor
Peer(s): Riddhi Bhave, Akshay Goel
GitHub Repository Link: [Link]

Overview
To create a professional networking platform tailored for students and young professionals seeking internships, offering features to enhance their search and application process.
Category: Professional Networking
Story: InternLink is a professional networking platform tailored for students and young professionals seeking internships. It offers features to enhance their search and application process, including personalized user experiences for both students and employers. The platform aims to simplify the internship search, application tracking, and professional development process.
Market: InternLink targets students and young professionals, as well as companies looking to recruit interns. The platform is aimed at universities, educational institutions, and companies of all sizes seeking to attract fresh talent.
Habit: Students will use InternLink daily to search and apply for internships, track their application progress, and connect with peers and mentors. Employers will use the platform to post internships, manage applicants, and interact with potential candidates.
Scope: The initial scope of InternLink includes user authentication, detailed user profiles, internship listings, application tracking, messaging, and professional development resources. Future enhancements may include advanced analytics, gamified challenges, and virtual interview practice.

Product Spec
Based on the app description, this section goes into more detail about what the app should do, and what functionalities it must provide to the users.
User Stories
User stories are actions that the user should be able to perform in your app.

First, focus and identify functionality that is required for your MVP (Minimum Viable Product) that conforms to all the project requirements and expectations. Make sure your technical challenges are part of your MVP.

You should also identify optional / nice-to-have functionalities that would be done as stretch goals during MU Week 8 and 9. Remember, technical challenges should not be optional features, they must be code complete before the end of Week 8!

User Accounts 
Required 
User can login as student or employer/recruiter
User can create an account as student or employer
Website experience changes based on user type (This would be high complexity technical challenge)
Optional
Employer can “view as student”

User
Student Profile :
Required
User can see their profile
User can upload profile picture
User can update about section
User can add work experience
User can add education

Optional
User can add skills (which can be endorsed by other users)
User can add projects and portfolios
User can upload resume

Company / Employer Profile:
Required
User can see company page
User can upload profile picture
User can update about section
User can edit job listings
User can add contact info and website links

Optional
User can add employee testimonials

Job Listings / Directory (Home Page):
Required
Users can utilize advanced search (location, industry, duration, etc.)

Optional
User can save and share listings

Networking & Connections:
Required
Friending logic
Messaging and chat system? (This would be high complexity technical challenge)

Optional
Alumni network pages (kind of like a group page?)
Employer recruitment messages (like linked inMail)

Application Tracking:
Required
Notifications
Analytics on application success rate (data table or other numerical format)

Optional
Data visualization for application success rate (graphs)
Employer application form creation

Resume / Cover Letter Builder:
Optional
Resume template customization
Export to PDF
Profile integration

Professional Development Resources
Optional
Articles, video, tutorial (external content) - displayed in visually appealing way (maybe using scrolling collection views)

Screen Archetypes
FIGMA: https://www.figma.com/design/Pi94fhY8djdXO6lmg8FC5g/InternLink?node-id=0-1&t=3LiH8WAgXIaS76m5-1 

[Describe the different screens that, together, compose the full experience of your app. You can leverage anything you want, such as diagrams and mocks.]

[Using diagrams you can also describe how navigation and presentation of these screens will work on a high-level.]

[These are just high-level representations though. Don’t spend too much time building mocks.]

Data Model
[Describe the data you’re going to need to back your application. This can include database models (like tables), or external data you’ll require from some API.]

User:
type = STUDENT, EMPLOYER
profile_picture_url
Friends = []

Students:
ID: UUID (Unique identifier for each student)
Name: String (Full name of the student)
Email: String (Email address of the student, used for login)
Password: String (Encrypted password using bcrypt or similar encryption method)
Profile Picture: String (URL to the student's profile picture)
Headline: String (A brief headline describing the student)
Skills: Array<String> (List of skills the student possesses)
Work Experience: Array<Object> (List of work experiences and internships, each object containing position, company, duration, description)
Education: Array<Object> (Educational background, each object containing institution, degree, field of study, start date, end date)
Certifications: Array<Object> (List of certifications, each object containing title, issuing organization, issue date)
Projects: Array<Object> (List of projects, each object containing title, description, technologies used, link)
Applications: Array<UUID> (Foreign Key referencing applications submitted by the student)

Employers:
ID: UUID (Unique identifier for each employer)
Company Name: String (Name of the company)
Email: String (Email address of the employer, used for login)
Password: String (Encrypted password using bcrypt or similar encryption method)
Company Logo: String (URL to the company's logo)
Description: String (Brief description of the company)
Mission: String (Company mission statement)
Internship Listings: Array<UUID> (Foreign Key referencing internships posted by the employer)
Internship Listings:
ID: UUID (Unique identifier for each internship listing)
Company ID: UUID (Foreign Key referencing the company posting the internship)
Title: String (Title of the internship position)
Description: String (Detailed description of the internship)
Requirements: Array<String> (List of requirements and qualifications needed for the internship)
Location: String (Location of the internship, can be a physical address or "Remote")
Duration: String (Duration of the internship, e.g., "3 months", "6 months")
Application Deadline: Date (Deadline for submitting applications)

Applications:
ID: UUID (Unique identifier for each application)
Student ID: UUID (Foreign Key referencing the student who submitted the application)
Internship ID: UUID (Foreign Key referencing the internship applied for)
Status: String (Current status of the application, e.g., "Submitted", "Under Review", "Interview", "Accepted", "Rejected")
Notes: Array<String> (Additional notes or comments related to the application)

Server Endpoints
[Describe the endpoints that your application is going to consume from your server. If you’re using REST, then you’ll probably want to include the method (GET/POST/etc) and the expected parameters (query parameters, body parameters, etc.)]

User Authentication:
POST /signup (Create new account)
POST /login (User login)
POST /logout (User logout)
POST /reset-password (Reset password)

Student Features:
GET /students/
(Retrieve student profile)
PUT /students/
(Update student profile)
GET /students/
/applications (Retrieve student's applications)
Employer Features:
GET /employers/
(Retrieve employer profile)
PUT /employers/
(Update employer profile)
POST /employers/
/internships (Post a new internship)
GET /employers/
/internships (Retrieve employer's internships)
GET /employers/
/applicants (Retrieve applicants for employer's internships)

Internship Listings:
GET /internships (Retrieve all internships)
GET /internships/
(Retrieve internship details)
POST /internships/
/apply (Apply for an internship)

Messages:
GET /messages (Retrieve all messages for user)
POST /messages (Send a new message)
Settings:
GET /settings (Retrieve user settings)
PUT /settings (Update user settings)
Navigation

Project Requirements
[Based on the Project Guide, describe how your project is going to be fulfilling each of the base project requirements.]

Technical Challenges
For your project, you should demonstrate that you can apply what you’ve learned so far and expand on that knowledge to write code and implement features that go beyond the scope of the projects you worked on during CodePath.

Based on the general idea and direction of your project requirements, your intern manager will create at least two (2) Technical Challenges for you. This section is all about explaining what they are and how you’re planning to tackle them - you’ll work together with your manager to fill it out. 

Technical Challenge #1 - User typed based web application
What
There will be more than web experience which will need to be presented based on the type of user that is logged in (student or employer/company). 
How
This will require advanced state management knowledge in order to serve a dynamic webpage based on user type. We don’t want to route to different URLs for “home” for example. We should only have one site home which displays the correct UI per user.

The technical complexity of this will stem from its implementation. I think the best way to manage this is with reducers (which was outside the scope of code path). Reducers also have the benefit of being a transferable skill to Meta since messenger’s RSys is just that, a reducer system.
Technical Challenge #2 - Messaging
What
In order for recruiters and students to chat about internship opportunities we will need a chat system.

How
We will likely need to leverage some sort of pub sub logic, and/or additional libraries so we can integrate this with our users.

Will require knowledge on advanced topics like concurrency.

Database Integration
[Describe what you are using for database storage. For example, Parse, MongoDB, Sequelize, etc.]

Mongo DB. 

External APIs
[Describe at least one external API you’re using for your project. For example, Google Maps, Spoonacular, OpenWeather, etc.]
Maybe linkedin, handshake

Authentication
[Describe how user authentication is handled for your project, including logging in and signing up. Also describe any kind of cookie / session management you’re doing and how you’re implementing it, and how this affects navigation between different screens by the same user.]
* 
Sign Up / Login Screen

Purpose: Allow users to create an account or log in.
Key Elements: Logo, email/username input, password input, role selection (Student or Employer), "Forgot Password?" link, "Sign Up" / "Log In" button.
Navigation: Directs to the User Dashboard upon successful login.
2. User Dashboard

Purpose: Provide a personalized overview for students and employers.
Key Elements: Navigation bar, profile summary (for students), company overview (for employers), quick links, recent activities.
Navigation: Links to Profile, Internship Listings, Messages, Settings, My Applications (for students), My Postings (for employers), Resources, Mentorship, Community.
3. Profile Page

Purpose: Display and edit user profile information.
Key Elements for Students: Profile picture, headline, about section, skills, work experience, education, certifications, projects, "Edit Profile" button.
Key Elements for Employers: Company logo, description, mission, internship postings, employee testimonials, contact information, "Edit Profile" button.
Navigation: Accessible from the User Dashboard and Navigation Bar.
4. Internship Listings Page

Purpose: Allow users to search and apply for internships.
Key Elements: Search bar, filters (location, industry, duration, remote/on-site, paid/unpaid), list of internships, "Save" and "Apply" buttons.
Navigation: Accessible from the User Dashboard and Navigation Bar, links to Internship Detail Page.
5. Internship Detail Page

Purpose: Provide detailed information about specific internships.
Key Elements: Internship title, company name, detailed description, requirements, application deadline, company overview, "Apply" button, "Save" button, contact information.
Navigation: Accessed from the Internship Listings Page.
6. Application Tracker Page (for Students)

Purpose: Track and manage internship applications.
Key Elements: List of applied internships, status of each application, deadline reminders, notes, analytics on application success rates.
Navigation: Accessible from the User Dashboard and Navigation Bar.
7. Applicant Management Page (for Employers)

Purpose: Manage applicants for posted internships.
Key Elements: List of applicants, applicant details (resume, cover letter, profile), application status updates, communication tools, notes and ratings.
Navigation: Accessible from the User Dashboard and Navigation Bar.
8. Messages Page

Purpose: Enable communication between users.
Key Elements: List of conversations, selected conversation, input field for typing messages, attachments option.
Navigation: Accessible from the User Dashboard and Navigation Bar.
9. Settings Page

Purpose: Allow users to customize their account settings.
Key Elements: Account settings (email, password), privacy settings, notification preferences, linked accounts.
Navigation: Accessible from the User Dashboard and Navigation Bar.


Probably with cookies 
Implementation Details:

Logging In:

When a user logs in, their credentials (email and password) will be sent to the server.
The server will verify the credentials and, upon successful authentication, generate a session token.
This session token will be stored in an HTTP-only cookie on the client-side.
Signing Up:

When a user signs up, their information (name, email, password, role) will be sent to the server.
The server will create a new user record and generate a session token.
This session token will be stored in an HTTP-only cookie on the client-side.
Session Management:

The session token stored in the cookie will be sent with each request to the server.
The server will validate the session token to authenticate the user.
If the session token is valid, the server will process the request and send back the appropriate response.
If the session token is invalid or expired, the server will prompt the user to log in again.
Cookie Settings:

The cookie will be set with the HttpOnly and Secure flags to enhance security.
The HttpOnly flag ensures that the cookie cannot be accessed via JavaScript, reducing the risk of XSS attacks.
The Secure flag ensures that the cookie is only sent over HTTPS connections.

Navigation:

With the session token stored in the cookie, the user can navigate between different screens without having to log in again.
The server will validate the session token on each request, ensuring continuous authentication.

Visuals and Interactions
[Provide details on how your app is fulfilling the following UI craft requirements, and how these are technically accomplished.]
Interesting Cursor Interaction
UI Component with Custom Visual Styling
Loading State

Timeline
Project execution will start in Week 4 of MU. Based on the previously defined requirements, user stories and technical challenges, use the following table to scope out and plan a timeline for deliverables over Week 4 - 9. You can be as detailed as you need, ranging from simply mentioning the user stories, or dividing them into sub-tasks.

You are free to modify the table, add / remove rows or columns, whatever fits your style! The important thing here is that you focus and prioritize certain aspects of your project so you don’t get behind and are ready to deliver the MVP - remember your required features should be code complete before the end of Week 8, including both technical challenges!

We also encourage you to leverage project tracking tools such as GitHub Issues or Meta’s internal Tasks / GSD tooling to keep manage individual units of work.

MU Week
Project Week
Focus
User Stories
4
1
Focus on the components that will serve as the skeleton of your project. You will probably be using most of what you learned in CodePath to set up things like the client and server repositories, initial routing, login / registration, creating a database with object models, etc.
Goals for Week 1:
Setup initial backend with node and express
Setup initial routing (for now lets just have login and registration)
Create database with our user model
Basic login screen UI
Basic registration screen UI
Setup our first reducer (let’s schedule a learning session for this)

[Optional] User passwords are encrypted in the database for security
5
2
Week 5 and 6 should be where you focus on the specific requirements of your project.
Finish login/registration logic

Set up directory / home page (using knowledge on reducers)
Profile/Company page
Notifications page i.e. friend requests

Stretch: 
Initial UI for inbox/message part
6
3
By this point, you should be getting started with your technical challenges as well.
Work on message sending logic
7
4
You should focus on finishing your MVP and core requirements. By this point, you should be done with at least one of your technical challenges.


8
5
Continue work on finishing touches and stretch goals for your MVP. By this point, your core functionality and both TAPs should all be in place. It is also a good point to start working on stretch goals that could further expand on the functionality (and technical complexity) of your project.

This week you also have to submit your self-review, make sure you allocate enough time for this alongside your final submission for your project!


9
6
It’s time to show others what you have built! Work on a presentation and demo that you will present to other interns to showcase your work. You are also free to continue polishing and expanding on your project!


10
7
For this week, we have a bunch of extra activities prepared to give you a quick dive of what it is to work at Meta. You will find activities around using internal tools and frameworks, and even committing code to our internal repositories.




