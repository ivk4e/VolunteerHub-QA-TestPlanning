# VolunteerHub Documentation

## Project: VolunteerHub

## Table of Contents

1. [System Purpose](#1-system-purpose)
2. [Geographical Scope](#2-geographical-scope)
3. [User Roles](#3-user-roles)
   - [Volunteer](#31-volunteer-regular-user)
   - [Organization](#32-organization)
4. [System Modules](#4-system-modules)
   - [Authentication](#41-module-authentication)
     - [Login](#411-screen-login-home-page)
   - [Initiatives](#42-module-initiatives)
     - [All Initiatives](#421-screen-all-initiatives)
     - [Initiative Details](#422-screen-initiative-details)
     - [Our Initiatives](#423-screen-our-initiatives)
     - [Create Initiative](#424-screen-create-initiative)
     - [Edit Initiative](#425-screen-edit-initiative)
   - [Groups](#43-module-groups)
     - [Group Feed](#431-group-feed-wall)
     - [Group Chat](#432-group-chat)
   - [Organizations](#44-module-organizations)
   - [User Profile](#45-module-user-profile)
   - [Notifications](#46-module-notifications)

---

> **Note:** All screenshots in this documentation are **illustrative** and were created using **Bootstrap Studio**.

## 1. System Purpose
**VolunteerHub** is a platform that enables different organizations to publish volunteer initiatives, while users (volunteers) can browse and participate in them.  
The system facilitates communication between volunteers and organizers through specialized groups for each initiative, where messages, event information, and updates are published.

---

## 2. Geographical Scope
VolunteerHub is designed for the territory of **the Republic of Bulgaria**. All functionalities, location fields, and validations are aligned with this limitation.

### Scope includes:

- **Initiatives:** can only be created with a location in Bulgaria (city/town)  
- **List of settlements:** dropdown menus containing only Bulgarian settlements  
- **Organization registration:** requires:  
  - Bulgarian registration number (EIK/Bulstat)  
  - Official email  
  - Address in Bulgaria  
- **Phone numbers:** format `+359XXXXXXXXX`  
- **Interface:** Bulgarian  
  - Localization to other languages is not planned for the first version

### Module-specific integration notes:

- **Authentication/Registration (Organizations)**  
  - EIK/Bulstat validation  
  - Address validation  
  - Phone number validation  

- **Initiatives/Create Initiative**  
  - Settlement selection only within Bulgaria  

- **Initiatives/List & Filters**  
  - Location filters show only Bulgarian settlements  

---

## 3. User Roles

### 3.1 Volunteer (regular user)

**Role description:**  
A volunteer is a regular user who browses initiatives and can participate in them. They do not have administrative rights.

**Main capabilities of a volunteer:**

1. **Browsing initiatives**  
   - Volunteers can see a list of all active initiatives published by various organizations.  

2. **Filtering initiatives**  
   - Status (Upcoming, Ongoing, Past – not shown)  
   - Date from  
   - Date to  
   - Category (ecology, social activities, education, etc.)  
   - Tags  
   - City  

3. **Viewing initiative details**  
   - Description (detailed description)  
   - Date from  
   - Date to  
   - Time  
   - City  
   - Location  
   - Participants  
   - Category  
   - Contact  
   - Tags  
   - Attached files  

4. **Signing up for an initiative**  
   - By clicking the "Sign Up" button, the user confirms participation.  

**After signing up:**  
- The volunteer is automatically added to the initiative's group.  
- As part of the group, they can:  
  - Receive notifications for new activity  
  - Publish posts after approval from administrator/moderator  
  - View posts from administrators/moderators  
  - Participate in the group chat  

**What they CANNOT do:**  
- Cannot edit others' posts (except their own)  
- Cannot delete others' posts (except their own)  
- Cannot delete the initiative  

---

### 3.2 Organization

**Role description:**  
An organization is a legal entity or an organizer group that can create and manage initiatives. After registration, the organization may have multiple members, divided into roles.

**Roles within an organization:**

#### Administrator
- Creates the initiative (the group is automatically created with it)  
- Full rights:  
  - Publish and edit posts  
  - Delete posts  
  - Manage volunteers signed up for the initiative  
  - Delete the initiative  
  - Change the roles of organization members (e.g., moderator → administrator)  

#### Moderator
- Maintains activity in the group  
- Can:  
  - Publish posts  
  - Edit posts they have published  
  - Monitor and delete inappropriate content  
- Cannot change roles of other users  
- Cannot delete the initiative  

#### Member
- Can publish and delete own posts in the initiative  
- Can like and comment on posts  
- Can participate in the group chat  
- Cannot edit or delete others' posts  
- Cannot change roles of other users  
- Cannot delete the initiative  

**Special case: user with multiple roles**  
- A user may have more than one role (e.g., volunteer and member of an organization)  
- Active role depends on login method (e.g., if "Log in as organization" checkbox is checked on login form)  

**Restriction:**  
- A user who is a member of an organization **cannot** sign up as a volunteer for initiatives created by the same organization  
- Can only sign up as a volunteer for initiatives created by other organizations  

---

## 4. System Modules

VolunteerHub consists of several main modules, each responsible for a specific part of the functionality. Each module includes one or more screens (pages).

---

## 4.1 Module: Authentication

### 4.1.1 Screen: Login (Home Page)

The home page contains an authentication form, organized in three tabs:  
- **Login**  
- **Register (Volunteer)**  
- **Register (Organization)**  

**Navigation:**  
The home page has no additional navigation. Users can only navigate to:  
- Login/Register tabs  
- "Forgot password" (from Login tab)  

---

### Tab: Register (Volunteer)
![Volunteer Registration](Screenshots/Authentication/register-volunteer.jpg)  
Fields:  
- First Name*  
- Last Name*  
- Email*  
- Phone  
- Password*  
- Confirm Password*  

---

### Tab: Register (Organization)
![Organization Registration](Screenshots/Authentication/register-organization.jpg)  
Organization registration requires more information, as it functions as a “business profile.”

**Required fields:**  
- Organization Name*  
- Contact Email*  
- Password* + Confirm*  
- EIK* / Bulstat  
- Organization Type*:  
  - NGO  
  - School  
  - Private Company  
  - Municipal Structure  
  - Other  
- Location / Address*  
- Official Contact Phone*  

**Contact person (administrator):**  
- First Name*  
- Last Name*  
- Phone*  

**Additional fields:**  
- Short description of the organization (mission/vision)  

**Additional fields available in organization settings:**  
- Website  
- Logo (upload)  
- Social networks  

**Special scenarios:**  
- During organization registration, the system checks if the contact email already exists as a user.  
- If the email exists:  
  - The existing user is assigned **Administrator** role for the new organization.  
- If the email does not exist:  
  - The system automatically creates a new user profile;  
  - The profile receives:  
    - Base role **Volunteer**;  
    - **Administrator** role for the registered organization.  
- Each organization always has at least one administrator.  

---

### Tab: Login
![Login](Screenshots/Authentication/login.jpg)  
Users can log in as:  
- Volunteer  
- Organization  

Checkbox:  
☐ "Log in as organization"  

If checked, the system verifies in the organization roles table.

**Login fields:**  
- Email*  
- Password*  

**Additional functions:**  
- "Forgot password" → send recovery email  
- Show/hide password  

**Special scenarios:**  
- Volunteer may be added to an organization via email and receive a new role  
- Volunteer may create own organization and receive Administrator role  
- Member/Moderator/Administrator can log in as Volunteer without checking "Log in as organization"  

---

## 4.2 Module: Initiatives

This module allows:  
- Volunteers – to browse and participate in initiatives  
- Organizations – to create, edit, and manage initiatives  

### Navigation

**Volunteer:**  
- Initiatives  
  - My Initiatives  
  - All Initiatives  

**Organization:**  
- Initiatives  
  - Our Initiatives  
  - Create Initiative  

---

### 4.2.1 Screen: All Initiatives
![All Initiatives](Screenshots/Initiatives/all-initiatives.jpg)  

Accessible to: volunteers and organizations

**Functionality:**  
- List of all active initiatives  
- Filters: Status, Date from, Date to, Category, Tags, City  
- Button "View Details"  

---

### 4.2.2 Modal: Initiative Details
![Initiative Details Modal](Screenshots/Modals/details-initiative.jpg)  
Shows:  
- Title, description  
- Date from  
- Date to  
- Time  
- City  
- Location  
- Participants  
- Category  
- Contact  
- Tags  
- Attached files  

**Actions by role:**  

- **Volunteer**  
  - Button "Sign Up"  
  - After signing up: "Group" button + "Signed Up" indicator  

- **Organization**  
  - View only  
  - Management is done from "Our Initiatives"  

---

### 4.2.3 Screen: Our Initiatives
![Our Initiatives](Screenshots/Initiatives/Organization/our-initiatives.jpg)  

Accessible to: organizations

Includes:  
- Status  
- Date from  
- City  
- Name  
- Short description  

**Buttons on each initiative:**  
![Initiative Buttons](Screenshots/Initiatives/Organization/our-initiatives-card.jpg)  

- Group  
- Details (opens modal with more information and option to cancel initiative if user is admin)  
![Our Initiative Details Modal](Screenshots/Initiatives/Organization/our-initiatives-details-modal.jpg)  
- [Edit](#425-screen-edit-initiative) (leads to initiative edit screen)  
- Participants (opens modal showing signed-up participants)  
![Participants Modal](Screenshots/Initiatives/Organization/our-initiatives-participant-modal.jpg)  

---

### 4.2.4 Screen: Create Initiative
![Create Initiative](Screenshots/Initiatives/Organization/create-initiative.jpg)  

**Fields:**  
- Title  
- Description  
- Date from  
- Date to  
- Time  
- City  
- Location  
- Category  
- Tags  
- Max participants (optional)  
- Contact  
- Attach files  
- Moderator/Admin settings – can add if logged-in user is admin  

**Buttons:**  
- Create Initiative  
- Clear  
- Back  

**Validations:**  
- Required fields  
- Date to ≥ Date from  

---

### 4.2.5 Screen: Edit Initiative
![Edit Initiative](Screenshots/Initiatives/Organization/edit-initiative.jpg)  

Accessible to: organizations (only own initiatives)

**Buttons:**  
- Save Changes  
- Delete Initiative (admin only)  
- Back  

When deleted, the group is archived and read-only.

---

## 4.3 Module: Groups

Groups are the main communication space. When an initiative is created, its group is automatically created.

### Role-based permissions:
- **Administrator:** full rights  
- **Moderator:** limited admin rights  
- **Volunteer:** posts require approval  

---

### 4.3.1 Group Feed (Wall)
![Group Feed](Screenshots/Groups/group-feed.jpg)  

Includes:  
- Posts  
- Comments  
- Likes  
- Attachments  

---

### 4.3.2 Group Chat

The group chat provides fast and direct communication among all initiative members. It can be accessed via the group sidebar in a compact view.  
![Sidebar Chat](Screenshots/Groups/chat-sidebar.jpg)  

It can be expanded via a modal window.  
![Chat Modal](Screenshots/Groups/chat-big.jpg)  

#### Functionality
- Send/receive text messages among all group members  
- Display sender information for each message:  
  - User name  
  - Role within the initiative (admin/moderator/volunteer)  
- Show system-generated messages  

#### System messages – examples
- "Iva Stoyanova joined the group"  
- "Petar Ivanov left the initiative"  
- "The initiative was archived"  

#### Access rights
- Administrator: can read and send messages  
- Moderator: can read and send messages  
- Member: can read and send messages  
- Volunteer: can read and send messages  

#### Notes
- The role displayed for a message is the user's role within the initiative  
- First version does NOT support:  
  - Editing chat messages  
  - Deleting chat messages  
  - Attaching files in chat  

---

## 4.4 Module: Organizations
![Organization Profile](Screenshots/Profile/Organization/our-profile.jpg)  

### Screen: Organization Profile

Must include:  
- Organization Name  
- Logo  
- Description  
- Active Initiatives  
- Team  

**Buttons:**  
- [Add Initiative](#424-screen-create-initiative)  
- Invite Member (opens modal to enter new member's email – admin role required)  
- Generate Report (participation/activity report)  
- Delete Organization (admin only)  

---

## 4.5 Module: User Profile
![User Profile](Screenshots/Profile/Volunteer/my-profile.jpg)  

### Screen: My Profile

- Name  
- Email  
- Change Password  
- Signed-up Initiatives  
- Groups  

---

## 4.6 Module: Notifications
![Notifications](Screenshots/notifications.jpg)  

### Bell
- Badge showing number of unread notifications  
- Dropdown with latest notifications  

### Examples:
- "New post in group"  
- "New message in chat"  
- "Successfully signed up for initiative"  
- "Reminder for upcoming initiative"  

---
