# Features: Semester Job-Preparation Checklist

## Parent user story

**As a** student,  
**when** I want to do activities that prepare me to get a job when I graduate,  
**I want** a checklist of tasks and events I can do each semester I am in school  
**so that** I am prepared to successfully apply for a job.

---

## Product context

Checklists prepare students to **apply for internships or co-ops while enrolled**, and to **apply for full-time jobs at graduation**. Applying to another degree program is out of scope.

The academic calendar in the app is **fall, spring, and summer**. Each term has its own checklist. Summer is used for internship/co-op work and for late-cycle applications, not only for students taking summer classes.

**Selected checklist items are verified by the career center** (for example workshop attendance or a resume review). Other items the student marks complete themselves.

**Primary users**

- **Students** — undergraduates and graduate students. Each follows a fall, spring, or summer checklist matched to their degree level and remaining time in the program.
- **Career advisors** — maintain the school’s recommended tasks and events, look up any student, and coach from that student’s checklist.

---

## System overview

The system helps undergraduates and graduate students at this school plan and complete career-preparation work over their time enrolled. It organizes career-center-approved tasks and campus events by **fall, spring, and summer** terms, using different default plans for undergraduate vs master’s vs doctoral timelines. Fall and spring emphasize recruiting and campus events; summer emphasizes completing an internship/co-op or continuing late-cycle applications. Later terms emphasize full-time job applications at graduation. It tracks completion and shows whether the student is on track for both internships and a job at graduation. Any signed-in career-center advisor can look up a student and use the same checklist data to coach them. Advisors also keep the default checklists current.

---

## Feature 1: Student profile and academic timeline

The system stores who the student is (degree level, program, expected graduation, current term) so checklists match where they are in school. Undergraduate, master’s, and doctoral students get different default timelines. Students with fewer remaining terms (for example transfers or one-year master’s) see a plan that fits the time they have left. Every year includes **fall, spring, and summer** checklists.

**User stories**

- **As a** student, **I want** to create an account and sign in with my school identity **so that** my checklist is tied to this campus and my progress is saved.
- **As a** student, **I want** to set my degree level (undergraduate, master’s, or doctoral), program/major, expected graduation date, and current term (fall, spring, or summer) **so that** the system can show a plan that fits my remaining time in school.
- **As a** student, **I want** my plan to be based on remaining fall/spring/summer terms until graduation, not only “year 1 / year 2” labels **so that** transfer and short-program students are not stuck on a four-year undergrad template.
- **As a** student, **I want** to update my current term when a new term starts **so that** I always see the right checklist.
- **As a** student, **I want** a summer checklist even if I am not taking summer classes **so that** I can still track an internship, co-op, or late applications.
- **As a** student, **I want** to record whether I am currently targeting an internship/co-op, a full-time job, or both **so that** my current-term checklist matches the application cycle I am in.

---

## Feature 2: Semester-based task and event checklist

The core of the product: a list of career-prep tasks and campus events grouped by **fall, spring, and summer**. Defaults come from the career center, not a generic internet list.

**User stories**

- **As a** student, **I want** to see a checklist of recommended tasks for my current term and degree level **so that** I know what this school expects me to work on now.
- **As a** student, **I want** to see checklists for past and future fall, spring, and summer terms **so that** I can review what I already did and plan ahead.
- **As a** student, **I want** tasks and events to be labeled by type (for example resume, networking, skills, applications) **so that** I can focus on one area at a time.
- **As a** student, **I want** each checklist item to include a short description of why it matters **so that** I understand how it helps me get a job.
- **As a** student, **I want** internship/co-op application tasks to appear mainly in fall and spring **so that** I apply in recruiting season before the internship starts.
- **As a** student, **I want** summer checklist items for completing an internship or co-op (and for late-cycle applications if I do not have one) **so that** summer is a real term in the plan, not a gap.
- **As a** student, **I want** full-time job tasks to appear as I get closer to graduation **so that** internship work and graduation-job work are not mixed into one undifferentiated list.
- **As a** student, **I want** items to show a suggested timeframe within the term (for example early, mid, or late) **so that** I do not leave important work until the last week.

---

## Feature 3: Progress tracking and completion

Students mark self-reported items done. Items the career center has marked as **verified** stay incomplete until staff confirm them (for example attended a workshop or completed a resume review). Advisors use the same progress when coaching (see Feature 8).

**User stories**

- **As a** student, **I want** to check off a self-reported task when I complete it **so that** I can see my progress on work the career center does not need to confirm.
- **As a** student, **I want** to uncheck a self-reported item if I marked it complete by mistake **so that** my list stays accurate.
- **As a** student, **I want** verified items to show as “needs career-center confirmation” instead of a normal checkbox **so that** I know I cannot finish them by checking a box myself.
- **As a** student, **I want** to request verification for a verified item (for example I attended the workshop) **so that** an advisor knows to confirm it.
- **As a** student, **I want** to see when a verified item is confirmed or declined **so that** I know whether it counts as done.
- **As a** student, **I want** to see a progress summary for the current term that separates self-reported completion from verified completion **so that** I know whether I am on track with both kinds of work.
- **As a** student, **I want** to see overall progress toward graduation (all fall, spring, and summer terms) **so that** I know if I am ready to apply for internships and for a job.
- **As a** student, **I want** completed items from earlier terms to stay visible as done **so that** I have a record of what I have already accomplished.

---

## Feature 4: Personalization and custom items

Default recommendations can be adjusted so the plan fits the student, while still starting from the school’s template.

**User stories**

- **As a** student, **I want** to add my own tasks or events to a term checklist **so that** I can include opportunities that are specific to me.
- **As a** student, **I want** to hide or skip a recommended item that does not apply to me **so that** my list is not cluttered with irrelevant work.
- **As a** student, **I want** to move an incomplete item to a later term **so that** I can catch up without losing track of it.
- **As a** student, **I want** recommended items to change based on my degree level, major, and career goal **so that** I am not following a plan that does not fit my program.

---

## Feature 5: Reminders and upcoming deadlines

The system helps students act on time-sensitive tasks and campus events.

**User stories**

- **As a** student, **I want** to see upcoming campus events and due dates on a simple calendar or list **so that** I do not miss career fairs, workshops, or application windows.
- **As a** student, **I want** to receive reminders for incomplete high-priority items as the term goes on **so that** I stay on schedule.
- **As a** student, **I want** campus events to show date, time, and location **so that** I can treat them as things I need to attend, not just to-dos.

---

## Feature 6: Guidance and supporting resources

Checklist items link to help from this school so students can actually complete the work.

**User stories**

- **As a** student, **I want** each task to include campus resources (career-center hours, appointment links, resume examples, interview practice) **so that** I know how to complete it here.
- **As a** student, **I want** a short “what good looks like” note for key items (for example a complete LinkedIn profile) **so that** I can tell when I am actually done.
- **As a** student, **I want** to see which items are most important for internships vs full-time applications **so that** I prioritize the work that employers care about for the cycle I am in.

---

## Feature 7: Job-application readiness snapshot

The student can see whether they are ready to apply for an internship/co-op now, and whether they are ready to apply for a full-time job at graduation.

**User stories**

- **As a** student, **I want** a readiness checklist for internship or co-op applications (resume, LinkedIn, target employers, career-fair plan) **so that** I know what is still missing before I apply while I am still in school.
- **As a** student, **I want** a separate readiness checklist for full-time jobs at graduation (resume or CV, cover letter, portfolio/LinkedIn, references, target list of employers) **so that** I know what is still missing before I apply at the end of my program.
- **As a** student, **I want** the system to highlight remaining must-do items from earlier terms **so that** I can close gaps before the next application cycle or before I graduate.
- **As a** student, **I want** to record internships or co-ops I have already completed **so that** later checklists and advisors can treat that experience as done.
- **As a** student, **I want** to export or print my completed checklist **so that** I can keep a personal record or bring it to an advising meeting.

---

## Feature 8: Advisor lookup and coaching

Any signed-in career-center staff member can look up any student and see that student’s checklists. Students do not opt in or revoke this access.

**User stories**

- **As a** career advisor, **I want** to sign in with a staff account **so that** only career-center staff can look up students and edit school templates.
- **As a** career advisor, **I want** to search for a student by name, school ID, or degree level **so that** I can open their record when they walk in or email me.
- **As a** career advisor, **I want** to view that student’s degree level, remaining terms, checklists, completion status, and readiness snapshot **so that** I can give targeted advice without asking them to recap everything.
- **As a** career advisor, **I want** to leave a short comment or suggested next step on a student’s plan **so that** the student knows what to do after a meeting.
- **As a** student, **I want** to see comments my advisors left on my checklist **so that** I can follow up after an appointment.
- **As a** career advisor, **I want** a queue of verification requests **so that** I can confirm or decline items without opening every student record one by one.
- **As a** career advisor, **I want** to mark a verified item complete or not complete on a student’s checklist **so that** workshop attendance and resume reviews are accurate.
- **As a** career advisor, **I want** a list of students who are behind on required items for the current term, including unverified required events **so that** the career center can reach out before it is too late.

---

## Feature 9: Career-center templates and campus events

Advisors keep the school’s default fall, spring, and summer plans and event list accurate.

**User stories**

- **As a** career advisor, **I want** to create and edit separate default task lists for undergraduate, master’s, and doctoral students for fall, spring, and summer **so that** each degree level starts from this school’s current recommendations.
- **As a** career advisor, **I want** to create and edit the default task list for each remaining-term slot (for example first-year fall, first-year summer, senior spring) **so that** shorter and longer programs both have a sensible sequence.
- **As a** career advisor, **I want** summer templates to include internship/co-op completion tasks and late-cycle application tasks **so that** summer is not an empty term.
- **As a** career advisor, **I want** to publish campus career events (fairs, workshops, info sessions) with date, time, and location **so that** they appear on student checklists and calendars.
- **As a** career advisor, **I want** to tag template items as internship-cycle vs graduation-job-cycle **so that** students see the right work at the right time in their program.
- **As a** career advisor, **I want** to attach different default items by major or program **so that** engineering, business, and other students are not forced onto one identical list.
- **As a** career advisor, **I want** to mark some template items as requiring career-center verification **so that** students cannot self-complete workshops, resume reviews, or similar events.
- **As a** career advisor, **I want** to mark some items as required vs optional **so that** students and other advisors know what the career center considers essential.
- **As a** career advisor, **I want** to update or retire an event or task when it is out of date **so that** students do not follow stale advice.

---

## Feature map (parent story → features)

| Feature | How it serves the parent story |
| --- | --- |
| Student profile and academic timeline | Checklist matches degree level and remaining fall/spring/summer terms. |
| Semester-based task and event checklist | Delivers this school’s list of tasks and events for each term, including summer. |
| Progress tracking and completion | Student can work the list and see they are getting prepared. |
| Personalization and custom items | Plan stays useful for different majors and goals. |
| Reminders and upcoming deadlines | Campus events and time-sensitive tasks actually get done. |
| Guidance and supporting resources | Students can complete items using this school’s help. |
| Job-application readiness snapshot | Outcome: ready to apply for internships while enrolled, and for a job at graduation. |
| Advisor lookup and coaching | Any career-center advisor can open a student’s checklist and coach from it. |
| Career-center templates and campus events | Tasks and events stay current and specific to this school. |
