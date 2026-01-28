<img src="https://beta.zenithscheduler.com/favicon.ico" width="128" />

# Zenith Scheduler
Schedule generator that takes the wants and needs of students into account.

## Table of Contents
* Quickstart Guide
* Feature List
* Architecture Diagram
* Usage examples
* FAQ

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

## Architecture Diagram
![Architecture Diagram](https://raw.githubusercontent.com/hardy-ethan/ZenithREADME/refs/heads/main/architecture_diagram.png)

## Usage Examples
### Generating a Simple First Year Engineering Schedule
![Generating a Simple First Year Engineering Schedule](https://raw.githubusercontent.com/hardy-ethan/ZenithREADME/refs/heads/main/simple_first_year.gif)
### Having the Scheduler Choose Classes from a Course Expression
![Having the Scheduler Choose Classes from a Course Expression](https://raw.githubusercontent.com/hardy-ethan/ZenithREADME/refs/heads/main/course_expression.gif)

## FAQ
* Q: Why use Zenith over the Atlas Schedule Builder?
    * A: Zenith has every capability the Atlas Schedule Builder has, as well as features to optimize your schedule. You will simply only gain functionality by using Zenith.
* Q: What data do you collect about me?
    * A: We do process your logins with your UMich Google Account, but we never store your email, and no schedules are ever associated with an user identifiers.
