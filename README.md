<div align="center">

# Nexus

**Your academic life, upgraded.**

*A student-built project that is one connected platform for students, instructors, clubs, and university staff. Built to make academic planning, teaching, campus life, and administration easier.*

**Status: Early development - First module release pending**

*⭐!!Coming 2026 December!!⭐️*

*Independent Sub-module: Course Planner*

</div>

---

## The Problem

University life is held together by disconnected portals, course calendars, learning-management systems, email threads, spreadsheets, group chats, and club registration forms. Each tool may do its own job, but they rarely work together.

The result is wasted time and frustration for **everyone on campus**:

- **Students** struggle to understand degree requirements, find reliable course information, track deadlines, and reach the right people.
- **Instructors and teaching staff** repeat answers to the same questions, distribute material across multiple channels, and juggle announcements, discussions, office hours, and course administration.
- **Clubs and student organizations** manage recruitment, membership, events, internal documents, and leadership transitions across scattered services.
- **University administrators and staff** maintain information in multiple systems, coordinate approvals and communications, and answer questions that could be resolved through clearer self-service tools.

Even straightforward tasks become complicated:

> **Student:** “If I fail this course, what can I still take next term?”
>
> **Instructor:** “How do I make sure every student sees the latest announcement and knows where to ask questions?”
>
> **Club executive:** “Where are our member records, event sign-ups, and documents from last year's team?”
>
> **Administrator:** “How can we publish an update once and keep the right people informed?”

**Nexus aims to connect academic information, people, and everyday campus workflows in a singular coherent experience.**

---

## What Is Nexus?

Nexus is an independent, student-built project with a long-term goal: a unified academic and campus platform for universities and colleges across North America.

Instead of building separate tools that force people to switch between systems, Nexus aims to connect the work they already do:
- **Local/cloud AI integration** - ever thought of "If only my chat knows what is coming up and tell me what/how to prepare."?
- **Smarter degree planning** - understand requirements, dependencies, and the impact of course choices.
- **One place for academic information** - find courses, programs, streams, and electives without switching between university portals.
- **Better communication** - a more organized experience for users, including school moderated forums and non school hosted forums.
- **Connected campus resources** - modernized file sharing, discussions, and community tools.
- **Multi-institution support** - an architecture that can eventually accommodate different schools and their academic rules.
- **Academic planning:** Courses, prerequisites, antirequisites, corequisites, electives, degree requirements, and what-if scenarios.
- **Teaching and learning:** Announcements, discussions, resources, common questions, office hours, and instructor–student communication.
- **Clubs and communities:** Organization spaces for recruitment, membership, events, resources, and leadership continuity.
- **University operations:** Tools for publishing consistent information, coordinating requests and approvals, and communicating with students and staff.
- **A shared, organized experience:** A unified interface with access appropriate to each person's role.
- **And so much more...**

Nexus is **not intended to serve students alone**. A campus platform only becomes genuinely useful when everyone involved in campus life can use it too.


---

## Who Is Nexus For?

Nexus is being designed for 

- Students.
- Professors.
- Club managers.
- Faculty Departments.
- The vast public (TBD).

---

## Module 1 — Course Planner

**Current focus: Crawler, Data pipeline, Logic, UI **

The first module tackles course and degree planning. Rather than merely displaying a course list, Nexus aims to understand how a student's completed courses and program requirements affect their future options.

### Planned Student Features

- **Course explorer:** Search and filter courses by institution, faculty, program, and academic year.
- **Degree requirements:** View required courses, unit totals, elective groups, and stream-specific rules together.
- **Prerequisite explorer:** Visualize course dependencies, including alternative prerequisite paths.
- **What-if planning:** Ask what remains possible after failing, dropping, or postponing a course.
- **Progress tracking:** Compare completed coursework against program requirements.
- **Term-by-term planning:** Build a realistic sequence of courses, subject to validated academic rules and offering data.
- **Modern interface:** A fast, accessible experience that replaces manual cross-referencing.

**Final product may remove or add features from the above list**.

---

## Roadmap

The order below ONLY describes the upcoming submodule development priorities.

**Phase 1 — Course Planner Sub-module**

- [x] Establish a staged McMaster calendar crawler due to no api access.
- [x] Store,parse,validate programs, course requirements, and course details etc in SQLite3.
- [ ] Optimize database and build course logics.
- [ ] Build and link the stacks.
- [ ] Beta testing irl.
- [ ] V1.0.0 Release.


---

## For Developers

Any independent developer/student who shares a similar vision is more than welcome to contact me for collaboration.

## FAQ

### You mentioned AI integration. Will the chool/prof be on my ass for leaking their copy-righted materials?

No, local models wil be used to process your copy-righted files.

### Will my inquires get saved to your server?

At the moment, no. Nothing will be saved on first module release, privacy is at the core of this project and a private student profile system is being actively researched.

### When will I see the finished product?

A long time, unfortunately. Considering the scope for this project and only one developer is actively contributing it is simply not feasible to achieve it in a reasonable timeframe.

### Why start with McMaster University?

McMaster University is what the developer most familiar with.

### Can Nexus tell me what I can take if I fail a course?

That is the entire point of the upcoming sub-module release.

### Will you make an Android/IOS/MacOS/Window app in the future?

Yes, this may come earlier than expected :).

### Is Nexus affiliated with McMaster University or any other organization?

Nexus is a personal student-built project using publicly available academic information. It is not presented as an official university service.

---

## Source and Project Notes

- **Initial academic data source:** McMaster.ca , academiccalendars.romcmaster.ca
- **Project stage:** Early development 
- **License and contribution process:** MIT
- **Data access:** Public catalog pages are being collected ethically while a more formal data-access approach is actively being explored.

---

<div align="center">

**Nexus — A less miserable academic life.**


</div>

## Running the academic calendar crawler

The new resumable SQLite pipeline, commands, data dictionary, tests, and coverage limitations are documented in [docs/CRAWLER.md](docs/CRAWLER.md).

```sh
.venv/bin/python -m crawlers run --catalog 65 --wait --output data/crawl-report.json
.venv/bin/python -m crawlers report --catalog 65
.venv/bin/python -m unittest discover -s tests -v
```

Normal requests use a two-second interval approved by school administrators, as confirmed by the user on 2026-11-10. Server-requested retry waits and failure backoff still apply. Source discovery and successful course-detail extraction are counted separately; the database is not complete merely because a bounded test run finished. The `catalog_` tables are the new data model; old prototype tables remain preserved.
