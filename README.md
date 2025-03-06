# Questions and Notes about infraction processor

## Question #1 - Processor Deployment Date
When is your preferred go-live date? I have heard it will be at the start of the next school year, but have also picked up that it may need to be sooner.

## Question #2 - Conditional Emailing/Notifications
You had mentioned the need for conditional emailing of infraction form submissions the other day when sent the infraction form you had worked on. This can be done, but I have a couple questions for you about what exactly you're needing (mainly around silent lunch teachers). For instance, silent lunch teachers should be emailed on the student's 3rd infraction (in a given set), and Adam on the 4th. In regards to silent lunch teachers being emailed, I have the following questions on how they are scheduled/rotated: 

_Note: I'm curious about silent lunch teacher rotations so as to reduce email spam for teachers that are not currently on silent lunch duty._
1) What are their schedules like? Do silent lunch teachers revolve on and off on a weekly / monthly rotation? If so, the following options can be done: 1) import a calendar schedule into a sheet (this depends on some factors), or 2) someone will need to update the list of silent lunch teachers when they need to change. Rotation of the lunch schedule can be automated with a CRON job, so as long as  there are teachers setup in a queue, the teachers will be rotated around without anyone needing to touch anything / run a script. This queue can be created via a calendar schedule, some other type of list, or manually.
2) I assume not all grades eat lunch at the same time, so are silent lunch teachers grade-specific? As in a 7th grade silent lunch teacher should only care about a 7th grade student's 3rd infraction (3rd in their current set).

## Question #3 - Office Referrals & Infraction Sets
When a student receives an office referral, does that automatically count as maxing out an infraction set?

- For example: If John has 2 infractions on his first infraction set (out of 4 total sets), and he is given an office referral, should his infraction count be bumped to the next set, so that the next infraction will start the second infraction set?

## Quesiton #4 - PDF Reports
I plan on making Infraction report documents dynamic in the sense that they are updated upon each new infraction per set.

The reports will be in PDF format and stored in a Google Drive directory relating to a specific student. If the form response data changes for any reason after the form is submitted and report has been generated, we can easily generate a new report PDF.

If an office referral is given for a student, should the referral be placed in the same report with the other infractions for that set?
  - For example:  If John has 2 current infractions on his first infraction set (out of 4 total sets), and he is given an office referral, the office referral report will be at the top of a sheet (or bottom, it's your choice), followed by the other 2 infractions.

I believe this idea can keep infraction set reports simple and in one place, but I can also keep the two types separate if that is what you all prefer.

## Question #5 - Importing Student Data

To get things up and running outside of a development environment, we will need to import a list of students per grade level. Depending on the service the school uses to house and manage student information, there could be a handful of ways to export the student data that will be used for populating student data in the infraction list spreadsheet / forms. 

To start, the spreadsheet for student information only needs a student's full name and a unique ID. If a unique ID is not available, we can probably generate one during the import. The unique ID is how we can guarantee that we only update one student during processing.

Here are some export formats they may offer, ordered by easiest to process.

1) JSON. This would be the easiest way to import student data
2) CSV. This would almost be as easy as JSON
3) XML. A little outdated, but not terrible.
4) TXT. Not ideal; This would be a bit complex, as I would have to study the data and create a custom parser
