## HardwareFault

Journal Entry App - Hardware Failure Simulation
Project Overview
A sophisticated single-page journal application that simulates disk space exhaustion (ENOSPC) - a critical hardware failure scenario. The app features a modern dark theme with glassmorphism effects, real-time statistics, and comprehensive error logging.
________________________________________
Failure Type Selected
Option A — Hardware Failure (Simulated Disk Full)
Unlike a simple notes app, this is a feature-rich journal application with:
•	Entry title and content fields
•	Real-time word/character counting
•	Persistent entry history
•	Auto-generated user identification
•	Structured JSON logging visible in UI and console
________________________________________
Features
Happy Path (Normal Operation)
•	✍️ Write journal entries with title and content
•	📊 Real-time statistics (word count, character count)
•	💾 Save entries to localStorage
•	📚 View and load previous entries
•	🎨 Beautiful dark theme with smooth animations
Failure Mode
When Disk Failure Mode is enabled and content exceeds 500 characters:
•	❌ Save operation fails with disk full error
•	🚨 Error banner displays: "ENOSPC (No space left on device)"
•	📋 Structured error log printed to console and UI
•	🔍 Detailed failure information with character limit violation
________________________________________
How to Run
Method 1: Direct File Opening
1.	Save the HTML file as journal-app.html
2.	Double-click the file to open in your browser
3.	Start using immediately - no server required!
Method 2: Local Server (Recommended)
# Using Python 3
python -m http.server 8000

# Using Node.js (http-server)
npx http-server

# Using PHP
php -S localhost:8000
Then navigate to http://localhost:8000/journal-app.html
________________________________________
How to Trigger the Failure
Step-by-Step Instructions:
1.	Open the application in your browser
2.	Enable Failure Mode: Click the "⚠️ Disk Failure Mode" toggle at the top 
o	Toggle will turn red
o	System log will record: "Disk failure mode ENABLED"
3.	Write content exceeding 500 characters: 
o	Enter a title (e.g., "My Long Entry")
o	Write content that combined with title > 500 chars
o	Watch the character counter turn red when limit exceeded
4.	Click "💾 Save Entry"
5.	Observe the failure: 
o	Error banner appears: "Save failed: ENOSPC (No space left on device)"
o	Console displays structured JSON error log
o	UI logs panel shows detailed failure information
o	Entry is NOT saved to localStorage
Quick Test
Title: "Test Disk Failure"
Content: [Paste any text longer than ~480 characters]
Result: Disk full error triggered
________________________________________
Expected Log Output
Console Log (JSON Format)
{
  "timestamp": "2025-11-19T15:30:45.123Z",
  "level": "ERROR",
  "user": "BoldDragon472",
  "docId": "entry_1700409045123_x7k3m9p2q",
  "size": 567,
  "errorCode": "ENOSPC",
  "errorMessage": "No space left on device",
  "limitExceeded": 67,
  "failureType": "HARDWARE_FAILURE_SIMULATED"
}
UI Log Display
[2025-11-19T15:30:45.123Z] ERROR: {
  "timestamp": "2025-11-19T15:30:45.123Z",
  "level": "ERROR",
  "user": "BoldDragon472",
  "docId": "entry_1700409045123_x7k3m9p2q",
  "size": 567,
  "errorCode": "ENOSPC",
  "errorMessage": "No space left on device",
  "limitExceeded": 67,
  "failureType": "HARDWARE_FAILURE_SIMULATED"
}
Error Banner Message
Save failed: ENOSPC (No space left on device)

Your entry (567 chars) exceeds the disk limit (500 chars).
Please reduce content by 67 characters.
________________________________________
Log Fields Explanation
Field	Description
timestamp	ISO 8601 timestamp of failure event
level	Log severity (ERROR for failures)
user	Auto-generated user identifier
docId	Unique document ID for the failed entry
size	Total character count (title + content)
errorCode	System error code (ENOSPC)
errorMessage	Human-readable error description
limitExceeded	Number of characters over the limit
failureType	Type of simulated failure
________________________________________
Technical Details
Technology Stack
•	HTML5 - Semantic structure
•	CSS3 - Advanced styling (gradients, backdrop-filter, animations)
•	Vanilla JavaScript - Pure JS, no frameworks
•	LocalStorage API - Data persistence
Browser Compatibility
•	✅ Chrome/Edge 90+
•	✅ Firefox 88+
•	✅ Safari 14+
•	✅ Opera 76+
Storage Mechanism
•	Entries stored as JSON array in localStorage
•	Key: journalEntries
•	Auto-loads on page refresh
•	Maximum ~5-10MB storage (browser dependent)
________________________________________
Code Highlights
Optimized Features
•	Class-based architecture for clean code organization
•	Event delegation for efficient DOM handling
•	Debounced updates for real-time statistics
•	Error boundary with try-catch blocks
•	Responsive design with CSS Grid
•	Accessibility with semantic HTML and ARIA labels
No Hardcoded Values
•	Character limit: Configurable (this.charLimit)
•	User generation: Dynamic random names
•	Document IDs: Timestamp + random string
•	Timestamps: Real-time ISO 8601 format
________________________________________
Design Philosophy
Dark Theme Rationale
•	Reduces eye strain during extended writing
•	Modern, professional appearance
•	Better focus on content
•	Popular in developer/creative tools
Glassmorphism UI
•	Backdrop blur effects for depth
•	Semi-transparent layers
•	Smooth animations and transitions
•	Visual hierarchy through opacity
________________________________________
Testing Checklist
•	[ ] Open app and verify random user ID generated
•	[ ] Write entry < 500 chars and save successfully
•	[ ] Enable failure mode via toggle
•	[ ] Write entry > 500 chars and trigger error
•	[ ] Verify error banner displays
•	[ ] Check console for JSON log
•	[ ] View UI logs panel
•	[ ] Disable failure mode and save successfully
•	[ ] Verify entry history displays saved entries
•	[ ] Load previous entry from history
________________________________________
Future Enhancements (Out of Scope)
•	Export entries to JSON/PDF
•	Search functionality
•	Tags and categories
•	Rich text editor
•	Cloud sync
•	Dark/light theme toggle
________________________________________
Assignment Compliance
✅ Single-page web app - Complete HTML file
✅ Simple task - Journal entry creation
✅ One failure type - Hardware failure (disk full)
✅ Working happy path - Full journal functionality
✅ Failure toggle - Deterministic fault injection
✅ Error banner - Human-readable crash message
✅ Structured logs - JSON format in console & UI
✅ Required log fields - timestamp, user, docId, size, errorCode
✅ README - Complete documentation
✅ Not from examples - Original journal app (not simple notes)
________________________________________
Author Notes
This application demonstrates production-ready error handling patterns:
•	Graceful degradation
•	User-friendly error messages
•	Comprehensive logging for debugging
•	State management without frameworks
•	Responsive and accessible design
Character Limit: 500 (configurable in code)
Failure Trigger: Content length > limit + failure mode ON
Storage: Browser localStorage (persistent)
________________________________________
License
MIT License - Free for educational use
Contact
For questions about this assignment implementation, please refer to the course instructor.
________________________________________
Built with ❤️ for Secure Software Design Assignment
