🏃‍♂️ Trail Running AI Agent (n8n Workflow)

An automated trail-running decision system powered by an n8n AI Agent.
This workflow uses real-time weather, air quality, calendar events, and trail data to determine whether it's safe to run today — and automatically emails the best trail recommendation.

🌟 Features

✅ Checks today’s Google Calendar events for “Trail Run”

✅ Fetches live weather data for Pune, India

✅ Fetches PM2.5 → AQI using an HTTP Request (OpenAQ or similar)

✅ Loads trail data (Google Sheets) including distance, shade, elevation, and time

✅ Determines if running is safe based on temperature, rain, storms, and AQI

✅ Selects the best trail based on weather conditions and trail attributes

✅ Automatically emails the full recommendation to email.

✅ Runs manually or on a schedule (via Schedule Trigger)

✅ Fully modular and customizable


<img width="1919" height="919" alt="Screenshot 2025-11-29 204752" src="https://github.com/user-attachments/assets/c1e1535e-cc97-4946-bf90-1d5bd47dac16" />


🧠 Tech Stack

This workflow uses the following n8n components:

Tool / Node	Purpose
AI Agent (OpenAI)	Core reasoning and decision logic
Calender	Reads today’s Google Calendar events
Weather	Retrieves current weather for Pune
HTTP Request	Fetches PM2.5 → AQI data
Data (Google Sheets)	Stores trail information
Receiver (Gmail)	Sends the final email
Brain + Simple Memory	Context handling
Schedule Trigger	Automates daily run evaluations
📊 Data Flow Overview

Calendar Check
Reads Google Calendar to find a “Trail Run” event.

Weather Check
Retrieves temperature & conditions for Pune.

Air Quality Check
Converts PM2.5 to AQI and categorizes it (Good → Hazardous).

Trail Selection
Loads trail list and selects the best fit based on:

Shade

Distance

Elevation Gain

Estimated Time

Temperature

AQI

Final Output

Sends an email summarizing the conditions and recommended trail.

Sends a short confirmation reply in chat (if triggered via n8n Chat).

📝 Example Email Output
Recommendation: YES — it is safe to run today.

Trail: Sinhagad Fort Trail
Distance: 6.2 km
Estimated Time: 90 minutes
Elevation Gain: 520 m
Shade Level: Shady

Weather (Pune): 24°C, Clear Skies
AQI: Moderate (PM2.5 = 22 µg/m³)

Calendar: No Trail Run event found today.


OR (if unsafe):

Recommendation: NO — Running is not safe today.

Reason:
- Heavy rain
- AQI: Unhealthy (PM2.5 = 98 µg/m³)

Weather (Pune): 26°C, Thunderstorms
Calendar: Trail Run event found today.

📁 Project Structure
/n8n-ai-trail-agent
│
├── workflows/
│   └── trail-running-agent.json
│
├── docs/
│   └── prompt.md
│   └── logic-overview.md
│
├── assets/
│   └── screenshots/
│
└── README.md

🚀 Getting Started
1. Import Workflow

Download trail-running-agent.json and import it into n8n:

n8n → Workflows → Import from File

2. Configure Credentials

You will need:

Google Calendar credentials

Gmail OAuth (for sending emails)

Google Sheets access

OpenWeather API key

OpenAQ (Free, no key needed) or another PM2.5 API

OpenAI API key (for the AI Agent)

3. Update Email Address

Edit the Receiver node and add your target email address.

4. (Optional) Change Location

Update the Weather node if you want a city other than Pune.

🧩 Customization

You can easily modify:

Running thresholds (temperature, AQI, weather conditions)

Trail ranking logic

Destination email

Weather/AQI providers

Trail dataset (simple Google Sheet)

🛡 Disclaimer

This project is for educational and personal automation use.
Weather and air quality data may vary; always check conditions before running.

📬 Support / Contributions

Open a GitHub issue or submit a Pull Request if you'd like to improve or extend this AI agent.
