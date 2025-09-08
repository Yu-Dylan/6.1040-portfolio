# Assignment 1

## Domains

### Ten Domains of Interest

1. **Calendar and Event Management**: Natural language scheduling, automated reminders (e.g. via texts), and smart calendar integration
2. **Photo Organization and Search**: Semantic photo discovery, intelligent tagging, and memory preservation
3. **Poker Performance Tracking**: Session tracking and performance visualization
4. **Personal Finance Management**: Expense and investment tracking and budgeting
5. **Fitness and Workout Planning**: Exercise routines and progress tracking
6. **Recipe and Meal Planning**: Recipe to meal organization and ingredients
7. **Language Learning**: Practice vocabulary and grammar
8. **Social Event Coordination**: Planning and RSVP management
9. **Digital Note Organization**: Knowledge management and cross-referencing
10. **Sleep Tracking**: Sleep duration and quality tracking

### Three Selected Domains (Detailed)

#### 1. Calendar and Event Management
Something that annoys me is having to manually translate my thoughts into properly formatted calendar events. When someone says "let's meet next Tuesday at 3," it takes multiple steps to actually get this into my calendar with proper details, location, and reminders. I'm interested in this domain because scheduling friction causes me to either over-rely on memory (and ultimately forget the events) or spend a lot of energy on calendar management. A natural language calendar agent that could understand context and automatically set appropriate reminders would eliminate this friction.

#### 2. Photo Organization and Search
I have thousands of photos across multiple devices and cloud services, but finding specific memories is nearly impossible. Current photo apps rely on basic metadata like date/location, but I think that having a semantic search system could transform photos from digital clutter into an accessible personal memory archive.

#### 3. Poker Performance Tracking
As someone who plays poker regularly, I struggle to track my performance across different games and stakes. I currently track manually, but I think that having a system that could automatically track and visualize my performance would be very helpful.

## Problems

### Calendar and Event Management Problems
1. **Friction from Manual Entry**: Converting casual speech into structured calendar events with proper details and timing
2. **Reminder Optimization**: Setting appropriate reminder timing based on event type, location, and personal patterns (e.g. birthdays should be a day or two in advance, appointments should be an hour or two in advance)
3. **Calendar Synchronization**: Managing events across multiple calendar systems and devices

### Photo Organization and Search Problems
1. **Semantic Search**: Finding photos based on content, people, and context rather than just metadata
2. **Photo Fragmentation**: Photos scattered across devices, cloud services, and social media platforms
3. **Tagging**: Tagging photos with relevant keywords and context to improve searchability

### Poker Performance Tracking Problems
1. **Manual Data Entry Burden**: Time-consuming and error-prone session logging and bankroll tracking
2. **Different Game Types**: Understanding win rates, variance, and profitability across different game types
3. **Behavioral Pattern Recognition**: This is a bit more complex, but I think it's important to track how I play in different conditions and over time.

## Selected Problems and Justifications

### Three Selected Problems

#### 1. Friction from Manual Entry (Calendar and Event Management)
**Problem:** Converting casual speech into structured calendar events requires multiple manual steps, creating friction that leads to forgotten appointments or over-reliance on memory.

**Why Selected:** This problem affects virtually everyone who uses calendars. The friction is universal but solvable now thanks to AI! It has high impact potential since scheduling is a daily activity.

#### 2. Semantic Search (Photo Organization and Search)
**Problem:** Finding specific photos based on content, people, events, and context is nearly impossible with current metadata-based search systems.

**Why Selected:** This addresses a growing problem as people accumulate thousands of photos but can't access their memories effectively. It's technically challenging but achievable now with AI.

#### 3. Manual Data Entry Burden (Poker Performance Tracking)
**Problem:** Poker players must manually log session details, results, and game conditions, leading to incomplete or inaccurate performance tracking.

**Why Selected:** This problem has a clear user base with demonstrated willingness to track performance. The manual burden prevents many players from getting valuable insights into their game (or at least makes it more time-consuming to log performance).

### Excluded Problems and Justifications

**Reminder Optimization:** While useful, this is more of an enhancement to existing calendar systems rather than solving a fundamental problem. Smart reminder timing is already being addressed by major calendar providers.

**Calendar Synchronization:** This is largely a solved problem with existing methods.

**Photo Fragmentation:** This is already being addressed by cloud storage providers.

**Tagging:** This is important but secondary to the basic findability problem. Once photos are searchable, manual tagging becomes less necessary.

**Different Game Types:** While important for serious players, this is more of a visualization challenge rather than a data collection problem, which is the more fundamental issue.

**Behavioral Pattern Recognition:** This requires significant data collection first, making it dependent on solving the manual entry problem.

## Stakeholders

### Friction from Manual Entry Stakeholders

**Calendar User**: Primary user who needs to quickly capture and schedule events from natural language
**Meeting Participants**: People who receive calendar invites and need accurate event details
**Personal Assistant/Scheduler**: Professional who manages calendars for executives or busy professionals
**Calendar App Developer**: Companies building calendar applications who could integrate NLP features
**Voice Assistant Provider**: Companies like Google, Apple, Amazon who handle voice-based scheduling requests

**Impact Analysis:** Calendar users experience daily friction and cognitive load from manual event creation, leading to missed appointments or scheduling errors. Meeting participants suffer from unclear or incorrect event details when manual entry introduces errors. Professional schedulers could dramatically increase efficiency with natural language processing. Calendar app developers could differentiate their products and increase user engagement. Voice assistant providers could offer more seamless scheduling experiences across their ecosystems.

### Semantic Search Stakeholders

**Photo Owner**: Primary user trying to find specific photos from their personal collection
**Family Members**: People who want to access shared family photos and memories
**Social Media Users**: People who want to reshare or reference old photos on social platforms
**Cloud Storage Provider**: Companies providing photo storage who face support costs from search frustrations
**Computer Vision Companies**: AI companies who could provide semantic search technology

**Impact Analysis:** Photo owners lose emotional connection to memories and waste significant time searching through thousands of photos. Family members can't easily access or contribute to shared family history when photos are unfindable. Social media users miss opportunities to share meaningful content when they can't locate relevant photos. Cloud storage providers face customer churn and support costs when users become frustrated with search limitations. Computer vision companies have a market opportunity to provide semantic search solutions.

### Manual Data Entry Burden Stakeholders

**Recreational Poker Player**: Casual players who want to track performance but find manual logging tedious
**Professional Poker Player**: Serious players who need accurate data for bankroll management
**Poker Room/Casino**: Venues that could provide automated tracking as a player service
**Poker Training Site**: Companies offering poker education who could integrate performance tracking

**Impact Analysis:** Recreational players often abandon tracking due to manual burden, missing opportunities to improve their game and understand their true performance. Professional players face significant time costs and potential errors in manual tracking that affect their livelihood. Poker rooms could increase player loyalty and differentiate their services with automated tracking features. Training sites could provide more comprehensive player development with integrated performance data.

## Evidence

### Friction from Manual Entry Evidence



### Semantic Search Evidence



### Manual Data Entry Burden Evidence



## Features

### Friction from Manual Entry Features

#### 1. Voice-to-Calendar Agent
**Description:** Mobile app and voice assistant integration that converts natural language speech into properly formatted calendar events, automatically extracting time, location, participants, and setting appropriate reminders.

**Why it helps:** Eliminates the multi-step process of manual event creation by allowing users to simply say "Schedule lunch with Sarah next Tuesday at noon at the Italian place." Calendar users save cognitive load and time, meeting participants get accurate invites, and voice assistant providers can offer more seamless scheduling experiences.

#### 2. Smart Context Recognition
**Description:** AI system that understands scheduling context from conversation history, location data, and personal patterns to automatically fill in missing details like specific times, locations, and reminder preferences.

**Why it helps:** Reduces the need for users to specify every detail when creating events. When someone says "dentist appointment next week," the system can suggest appropriate times based on the user's schedule and typical appointment patterns. Personal assistants and schedulers benefit from reduced back-and-forth communication.

#### 3. Proactive SMS Reminder System
**Description:** Intelligent text messaging system that sends contextual reminders based on event type, location, traffic conditions, and user behavior patterns, with natural language summaries of upcoming events.

**Why it helps:** Ensures users never miss appointments by providing timely, relevant reminders via their most-checked communication channel. Meeting participants benefit from better attendance rates, and calendar app developers can increase user engagement and retention through valuable reminder services.

### Semantic Search Features

#### 4. Natural Language Photo Search
**Description:** Search interface that allows users to find photos using descriptive queries like "photos of me and Sarah at the beach last summer" or "pictures from my graduation party" using computer vision and natural language processing.

**Why it helps:** Transforms photo collections from digital clutter into accessible memory archives. Photo owners can quickly find specific memories without scrolling through thousands of photos. Family members can easily locate shared memories, and social media users can find relevant content to reshare.

#### 5. Automatic Memory Tagging
**Description:** AI system that analyzes photos for people, objects, locations, events, and emotions, then creates searchable tags and suggests meaningful album organization based on detected patterns and relationships.

**Why it helps:** Makes photos searchable without requiring manual tagging effort from users. Computer vision technology automatically identifies content, making memories findable years later. Cloud storage providers can reduce support costs by improving user satisfaction with search capabilities.

#### 6. Cross-Platform Memory Unification
**Description:** Service that connects to multiple photo storage platforms (Google Photos, iCloud, social media) to create a unified search interface across all user's photos, eliminating duplicates and creating comprehensive memory timelines.

**Why it helps:** Solves the fragmentation problem by bringing scattered photos into one searchable system. Photo owners get complete access to their memories regardless of storage location. Family members can access shared photos from any platform, and cloud storage providers can differentiate their services.

### Manual Data Entry Burden Features

#### 7. Automated Session Detection
**Description:** Mobile app that uses location services, calendar integration, and manual check-ins to automatically detect poker sessions, track duration, and prompt for results entry with minimal user input required.

**Why it helps:** Eliminates the burden of remembering to start/stop session tracking. Recreational players can effortlessly track their performance, while professional players get accurate session data for tax reporting. Poker rooms could integrate this as a player service to increase loyalty.

#### 8. Smart Result Entry Interface
**Description:** Streamlined mobile interface that uses voice input, photo capture of chips/receipts, and intelligent defaults to minimize the time and effort required to log session results and game details.

**Why it helps:** Reduces data entry time from minutes to seconds per session. Professional players save significant time on record-keeping, tax professionals get more accurate client data, and poker training sites can integrate performance tracking with educational content.

#### 9. Visual Performance Dashboard
**Description:** Interactive dashboard that automatically generates charts, graphs, and insights from tracked poker data, showing win rates, variance, profitable game types, and bankroll trends over time.

**Why it helps:** Transforms raw data into actionable insights without requiring spreadsheet skills. Recreational players can understand their true performance and identify areas for improvement. Professional players get sophisticated analysis tools, and training sites can provide personalized coaching based on actual performance data.

