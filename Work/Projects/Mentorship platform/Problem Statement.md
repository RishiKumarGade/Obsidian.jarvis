
PalTech runs a mentorship initiative across functions and grade levels, but the entire programme is managed manually. Mentor-mentee pairing is owned by HR and done through spreadsheets and direct conversations, with no way for a mentee to browse who is available or what a mentor can coach on. Senior employees willing to mentor have no way to declare their skills, preferred domains, availability, or mentee capacity on any platform.  
  
Once a match is made, the engagement has no infrastructure behind it. Sessions are coordinated over email, notes stay in personal inboxes, and action items agreed in one session are rarely tracked into the next. Mentees lose sight of the goals they set at the start and have no way to measure progress. Feedback is not collected after sessions, so mentors receive no signal on session effectiveness and the HRBP has no aggregate view of engagement quality.  
  
As PalTech grows, this model does not scale. The HRBP cannot see at any point how many active relationships exist, how many sessions have happened, or which engagements are at risk. Programme outcomes are invisible to the Programme Owner, and HR coordination effort increases with every participant added.


Build a self-service internal Mentorship Experience Platform for PalTech where mentees discover and request mentors by skill and domain, mentors manage their own availability and capacity, and every engagement runs through the platform from kickoff to closure. The HRBP and Programme Owner will have live visibility into programme health, participation rates, and engagement outcomes. Grade-based eligibility, reporting-chain exclusion, and capacity limits will be enforced by the system. The platform will replace all manual HR coordination in the current model and make PalTech's mentorship programme measurable, repeatable, and scalable across all functions.



Hi Lokesh, this is the summary of requirements for the mentioned features I worked on today

1.Session Management

1.Integrate with Teams System to display mentors calender to find available slots

2.Integrate with Teams System to allow mentors and mentees to schedule sessions directly from this application and store meetings link

3.Both mentees and mentors should be able to reschedule or cancel a booked session

3.Session Details

Store-

Date, Time, Meeting link, Duration, Status  

Statuses: completed, Upcoming, cancelled, Reflection Pending, Rescheduled

4. Session Notes

After every completed meeting

Capture

Discussion summary

Next session topics

Any to be discussed questions from mentee.

Mentor then reviews it and then can

Approve ,

Edit.

Only after mentor approves this, then the session is marked as completed.

It should be visible to both mentee and mentor.

5. store every session history:

For each session display session date, time, status,ANy milestone updates if there

Statuses: completed,Upcoming,cancelled

2.Milestone Planning

Functional Requirements:

1.Create Milestones

Created during kickoff meeting.

Each milestone contains-

Name

Description

2.After every session, mentor should be asked if that session contributed to any milestone(multi-select also allowed), if yes then mentor selects that milestone and updates the progress of that milestone.

the progress of milestone can be tracked as:

Started

Moderate Progress

Significant Progress

Completed.

The system should automatically calculate and update the milestone progress based on the selected progress level.

3. Milestones should be able to be edited or deleted by the mentor

4.Both mentor and mentee should be able to view these milestones

5.Milestones with completed status should be displayed as completed milestone