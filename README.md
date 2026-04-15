<img src="https://beta.zenithscheduler.com/favicon.ico" width="128" />

# Zenith Scheduler
Zenith is a schedule generator for University of Michigan students that optimizes your class schedule around your preferences, like avoiding early mornings, minimizing gaps between classes, and ensuring time for lunch.

## Table of Contents
* [Quickstart Guide](#quickstart-guide)
* [Feature List](#feature-list)
* [Usage Examples](#usage-examples)
* [FAQ](#faq)
* [Architecture](#architecture)

## Quickstart Guide
Simply visit https://beta.zenithscheduler.com, click the Login button (make sure you select your UMich Google account), and you're good to go! 

Once logged in, you can optionally elect to join the Discord server, where we discuss potential features, bugs, and suggestions.

<img alt="Location of Discord Server button" src="https://raw.githubusercontent.com/hardy-ethan/ZenithREADME/refs/heads/main/discord_screenshot.png" width="500" />

## Feature List
* Consider preferences, e.g. you like/dislike gaps, starting early in the day, etc.
* Ensure that there is time for lunch on days with many classes
* Specify that you will not attend or are willing to not attend certain section types (e.g. Lecture, Discussion), allowing the generator to use those sections freely
* Special topic sections are clearly separated by topic
* Prohibit the use of sections that have certain instructors
* (Optionally, Advanced), have the generator choose classes for you from a provided expression, based on which would have the best schedule. For example, you can input along the lines of "EECS280, EECS203, and either both PHYSICS140 and PHYSICS141 or CHEM210 and CHEM211).
* Light/dark mode
* Will not generate north/central back to backs, unless you specify that you will not be attending one or both of the classes

## Usage Examples
### Step 1: Enter Your Courses
Add courses to your course expression. Here we add MATH215, ENGR100, and EECS280 for a typical first-year engineering schedule.

![Adding courses to the course expression](https://raw.githubusercontent.com/hardy-ethan/ZenithREADME/refs/heads/main/zenith_select_courses.gif)

### Step 2: Set Your Preferences
Configure time constraints and preferences — such as allowed meeting times, gap preferences, whether you want a late start, and ensuring time for lunch.

![Setting schedule preferences and time constraints](https://raw.githubusercontent.com/hardy-ethan/ZenithREADME/refs/heads/main/zenith_choose_options.gif)

### Step 3: Adjust Objective Weights
Fine-tune how much each preference matters by adjusting the objective weights. For example, increase the gap weight if minimizing breaks between classes is more important to you than starting late.

![Adjusting objective weights with sliders](https://raw.githubusercontent.com/hardy-ethan/ZenithREADME/refs/heads/main/zenith_weigh_options.gif)

### Step 4: Generate Your Schedule
Hit "Generate Schedule" and Zenith will find the optimal schedule that best satisfies your preferences.

![Generating the final optimized schedule](https://raw.githubusercontent.com/hardy-ethan/ZenithREADME/refs/heads/main/zenith_generate_schedule.gif)

## FAQ
* Q: Why use Zenith over the Atlas Schedule Builder?
    * A: Atlas lets you browse and manually build a schedule, but it doesn't optimize for your preferences. Zenith automatically finds the best schedule based on criteria you set, like preferring late starts, minimizing gaps, ensuring a lunch break, and avoiding north/central campus back-to-backs. It can also choose between alternative course combinations for you using expressions (e.g., "PHYSICS 140+141 or CHEM 210+211") and pick whichever yields the better schedule.
* Q: What data do you collect about me?
    * A: We do process your logins with your UMich Google Account, but we never store your email, and no schedules are ever associated with any user identifiers.

## Architecture

![Architecture Diagram](https://raw.githubusercontent.com/hardy-ethan/ZenithREADME/refs/heads/main/architecture_diagram.png)

When a user submits a schedule request, the Web Workers serve the frontend and handle the API. The request is written to a Solver Queue Database and picked up by a Queue Worker, which formulates the scheduling problem as an integer linear program (ILP). The ILP encodes hard constraints (no time conflicts, required section types, banned instructors) and soft objectives (gap preference, late start preference, empty day preference) as a weighted optimization problem. Sections, meeting times, instructors, and enrollment status are fetched from the UMich Schedule of Classes API. Once the solver finds an optimal schedule, the result is sent back to the user over a WebSocket connection.