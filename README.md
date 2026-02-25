You are operating in GitHub Copilot Agent Mode as a senior autonomous software architect.

Your task is to FULLY bootstrap a self-maintaining AI project system called WeddingOS starting from an empty Visual Studio Code session with no folder open.

You must design, create, and configure the entire system automatically.

Do NOT ask planning questions unless authentication is required.

Act decisively and build the system.

PRIMARY GOAL

Create a LOCAL-FIRST AI wedding management platform where future user prompts automatically:

update project data

update Google Calendar

send FREE email reminders

maintain task tracking

run scheduled project health checks

maintain long-term memory

optionally use local Ollama models

require ZERO paid services

GitHub Copilot Chat is the PRIMARY ingestion interface.

The system must understand future user input without needing instructions each time.

TECHNOLOGY CONSTRAINTS

Use ONLY FREE tools.

Required stack:

Node.js latest LTS
TypeScript
Markdown
JSON databases
Git repository
Google Calendar API (free tier)
Gmail API (free)
node-cron scheduling
Nodemailer email sending
dotenv configuration
Ollama local API support
VS Code + Copilot Agent Mode

DO NOT USE:

Notion
Paid SaaS planners
Twilio
Paid SMS services
Closed ecosystems

Email reminders are allowed.
SMS texting must remain optional and disabled by default.

STEP 1 — CREATE PROJECT

Create folder:

WeddingOS

Initialize:

git init
npm init -y
TypeScript configuration
.env support

Install latest versions of:

typescript
tsx
dotenv
node-cron
googleapis
nodemailer
fs-extra
zod
date-fns
axios

Create npm scripts:

dev
heartbeat
calendar-sync
email-digest
ai-review
ingest

STEP 2 — DIRECTORY STRUCTURE

Create:

WeddingOS/
│
├── ai/
│ ├── copilot_rules.md
│ └── system_prompt.md
│
├── data/
│ ├── tasks.json
│ ├── vendors.json
│ ├── budget.json
│ ├── notes.md
│ └── wedding_config.json
│
├── calendar/
│ └── sync.ts
│
├── automation/
│ ├── heartbeat.ts
│ ├── weekly_review.ts
│ └── email_digest.ts
│
├── ollama/
│ └── client.ts
│
├── scripts/
│ └── ingest.ts
│
├── logs/
│
└── README.md

STEP 3 — COPILOT PERMANENT OPERATING INSTRUCTIONS

Create ai/copilot_rules.md.

This file defines how Copilot behaves forever.

Rules:

You are WeddingOS Project Manager.

Whenever the user provides new wedding information you MUST automatically:

Interpret intent

Update tasks.json

Adjust deadlines

Update budget.json

Append notes.md

Create or modify Google Calendar events

Detect missing planning items

Generate new tasks automatically

Never ask what action to take

Assume user statements are authoritative updates

You proactively maintain project health.

STEP 4 — DATA MODELS

Create strongly structured schemas using Zod.

tasks.json fields:

id
phase
category
task
completed
priority
cost
notes
reference
calendar_event_id

budget.json:

total_budget
overage_limit
current_estimated_total

vendors.json:

vendor
category
contact
status
deposit_paid
balance_due

wedding_config.json:

wedding_date = 2026-10-10
location = TBD
email_notifications = true
ollama_enabled = true

STEP 5 — INGEST INITIAL DATA

Populate tasks.json with the following entries, please clean up the information, do not forget anything.:

**Immediate (Feb/Mar 2026)**	Budget & Planning	Refine detailed budget breakdown	TRUE	High	$3,500 Total	Allocate funds across remaining categories (e.g., dress, catering, photographer). $3,000 base budget, $500 max overage.	N/A																		
**Immediate (Feb/Mar 2026)**	Vendor Booking	Hire Photographer & Videographer	FALSE	High	$800	Research portfolios, check availability for Oct 10th, and secure with a deposit.	[URL]																		
**Immediate (Feb/Mar 2026)**	Attire	Start Wedding Dress Shopping/Ordering	FALSE	High	$600	Allow 6-9 months for production and 2 months for alterations.	[URL]																		
**Immediate (Feb/Mar 2026)**	Vendor Booking	Book Caterer/Finalize Menu	FALSE	High	$750	Since the venue is booked, confirm if catering is included or if an outside vendor is needed. Schedule tasting.	[URL]																		
**Immediate (Mar 2026)**	Vendor Booking	Book Officiant	FALSE	Medium	$100	Need to take a picture and then print/mail them.	Local Court/Clergy																		
**6-7 Months Out (Mar/Apr 2026)**	Guest Management	Send Save-the-Dates	FALSE	High	$0	Take pictures	N/A																		
**6-7 Months Out (Mar/Apr 2026)**	Attire	Select Wedding Party Attire	FALSE	High	$300	Choose colors/styles for bridesmaids/groomsmen. Give them ordering deadlines.	Various Stores																		
**6 Months Out (Apr 2026)**	Registry & Website	Complete Wedding Registry	FALSE	Medium	$0	Register at 1-2 major retailers or online platforms.	Zola/Amazon																		
**6 Months Out (Apr 2026)**	Stationery	**Order Formal Invitations**	FALSE	High	$250	**ACCELERATED: Order invitations, RSVP cards, and envelopes immediately. Need printing/delivery time by early May.**	[URL]																		
**5 Months Out (Early May 2026)**	Stationery	**Mail Formal Wedding Invitations**	FALSE	High	$50	**ACCELERATED: Mail invitations 5 months before the wedding to allow maximum travel notice.** RSVP due date should be early September.	Post Office																		
**4-5 Months Out (May/Jun 2026)**	Vendor Booking	Book DJ/Band/Entertainment	FALSE	Medium	$300	Discuss song lists (must-plays/do-not-plays) for ceremony and reception.	[URL]																		
**4 Months Out (Jun 2026)**	Ceremony	Meet with Officiant	FALSE	Medium	$0	Discuss ceremony flow, readings, and vow structure.	Officiant Name																		
**3 Months Out (Jul 2026)**	Vendor Booking	Order Wedding Cake/Dessert	FALSE	Medium	$150	Schedule a tasting and finalize the design.	Local Bakery																		
**3 Months Out (Jul 2026)**	Guest Management	Arrange Hotel Room Blocks	FALSE	Medium	$0	Reserve blocks of rooms for out-of-town guests at a negotiated rate.	Local Hotels																		
**8 Weeks Out (Aug 2026)**	Attire	Schedule First Dress Alteration	FALSE	High	$50	Bring wedding shoes and necessary undergarments.	Seamstress																		
**6 Weeks Out (Late Aug 2026)**	Logistics	Plan Bar/Beverages	FALSE	Medium	$150	Finalize drink menu and alcohol purchasing/delivery logistics (if not handled by caterer).	Caterer/Vendor																		
**4 Weeks Out (Sep 2026)**	Logistics	Obtain Marriage License	FALSE	High	$50	Research local county/state requirements (usually valid for a limited time).	Probate Court																		
**2 Weeks Out (Late Sep 2026)**	Guest Management	Finalize Seating Chart & Headcount	FALSE	High	$0	Call any guests who have not responded. Provide final count to caterer/venue.	N/A																		
**1 Week Out (Early Oct 2026)**	Final Details	Final Vendor Confirmations	FALSE	High	$0	Confirm arrival times, final payments, and timelines with all vendors.	All Vendors																		
**Day Before (Oct 9th)**	Ceremony	Wedding Rehearsal & Dinner	FALSE	Medium	$0	Run through the ceremony; enjoy the rehearsal dinner.	Venue/Dinner Location																		
**Day Before (Oct 9th)**	Final Details	Prepare Vendor Tips & Final Payments	FALSE	High	$0	Put cash/checks in labeled envelopes to be distributed by a designated person.	N/A																		
																									

Convert TRUE/FALSE into boolean values.

Include all phases, costs, priorities, notes, and references.

Append to notes.md:

bride wont need hair costs or makeup
our officiant is a family friend and free
lower photo cost to half
increase catering by double
no tasting fee for cake
notes, tips, deals, ideas, suggestions, money saving ideas
diy invites, center pieces, misc.

STEP 6 — GOOGLE CALENDAR INTEGRATION

Create calendar/sync.ts.

Capabilities:

OAuth authentication

create/update/delete events

event titles from task names

due dates become calendar reminders

automatic reminder 7 days + 1 day prior

Store credentials in .env.

Add instructions in README explaining Google Cloud Console setup.

STEP 7 — EMAIL AUTOMATION

Create automation/email_digest.ts.

Daily digest email includes:

upcoming tasks
overdue tasks
budget summary
risk warnings

Use Nodemailer with Gmail OAuth.

No paid services.

STEP 8 — HEARTBEAT SYSTEM

Create automation/heartbeat.ts.

Runs daily.

Heartbeat must:

scan tasks
detect overdue items
identify missing vendors
update logs
trigger calendar sync
trigger email digest

Add cron schedule:

8 AM daily.

STEP 9 — OLLAMA LOCAL AI SUPPORT

Create ollama/client.ts.

Connect to:

http://localhost:11434

Allow configurable model name.

Purpose:

local reasoning
risk analysis
task suggestion generation
offline operation

Copilot remains primary interface but may call Ollama for analysis.

STEP 10 — AI REVIEW LOOP

Create automation/weekly_review.ts.

Weekly process:

analyze project health
suggest new tasks
detect timeline risks
summarize progress

Output markdown report in /logs.

STEP 11 — INGEST ENGINE

Create scripts/ingest.ts.

When user pastes natural language into Copilot:

Copilot must run ingest.ts logic:

parse update
modify JSON data
update calendar
append notes

The user must NOT need to explain instructions.

STEP 12 — README

Explain:

setup
Google authentication
Gmail authentication
running heartbeat
adding new information through Copilot Agent Mode

STEP 13 — COPILOT AUTONOMY

Design system_prompt.md describing that Copilot is:

WeddingOS Autonomous Project Manager

Copilot continuously:

plans
organizes
schedules
monitors
alerts
updates data

Copilot must behave as if responsible for successful execution of the wedding.

FINAL REQUIREMENTS

After setup completes:

Running:

npm run heartbeat

must execute full system health evaluation.

The repository must be immediately usable.

Proceed now and build the entire WeddingOS system.
