
# Travel Planning Assistant

This project implements a Travel Planning Assistant that helps users create detailed travel itineraries for any destination. Powered by the phi library with Gemini and Groq models, the assistant uses the DuckDuckGo search tool to provide up-to-date information on destinations, attractions, accommodations, transportation, and budget estimates. The script supports generating travel plans for specified destinations and durations, such as a 7-day trip to Tokyo, Japan.
Features

Destination Research: Provides current information on travel destinations using DuckDuckGo search.
Itinerary Generation: Creates detailed travel plans, including:
Best time to visit
Top attractions and activities
Accommodation recommendations (hostels) across different price ranges
Local transportation options and tips
Estimated daily budget breakdown


Dual Model Support: Integrates with both Gemini (gemini-2.0-flash) and Groq (mixtral-8x7b-32768) models for flexible processing.
Interactive Planning: Generates Markdown-formatted travel plans for easy readability.
Environment Configuration: Supports secure API key management for Google and Groq services.

Prerequisites

Python 3.8 or higher
Required libraries: phi, google-colab (for Colab environments)
API keys for Google (Gemini) and Groq
Internet access for DuckDuckGo search functionality

Installation

Clone the repository:git clone https://github.com/yourusername/your-repo.git
cd your-repo


Create a virtual environment (optional but recommended):python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate


Install dependencies:pip install -r requirements.txt


Set up environment variables:
Replace 'your-api-key' in the script with your actual Google and Groq API keys, or set them as environment variables:export GOOGLE_API_KEY='your-google-api-key'
export GROQ_API_KEY='your-groq-api-key'


For Google Colab, update the userdata section with your Groq API key.



Usage

Run the Script:
python travel_assistant.py

The script will:

Initialize two travel agents using Gemini and Groq models.
Generate a 7-day travel plan for Tokyo, Japan (or any specified destination).
Output the plan in Markdown format, including best time to visit, attractions, accommodations, transportation, and budget estimates.


Example Function Call:Modify the destination and duration in the script to generate a custom travel plan:
generate_travel_plan("Paris, France", 5)


Example Output:
## 7-Day Travel Plan for Tokyo, Japan

### Best Time to Visit
Spring (March-May) for cherry blossoms or autumn (September-November) for mild weather.

### Top Attractions and Activities
- **Day 1**: Visit Shibuya Crossing and Meiji Shrine.
- **Day 2**: Explore Asakusa and Senso-ji Temple.
- ...

### Recommended Hostels
- **Budget**: Khaosan Tokyo Kabuki ($30/night)
- **Mid-range**: Sakura Hostel Asakusa ($50/night)
- **Premium**: Nui Hostel & Bar Lounge ($80/night)

### Local Transportation
- **Tokyo Metro**: Efficient subway system; get a Suica/Pasmo card.
- **JR Lines**: Ideal for longer trips, e.g., to Odaiba.

### Estimated Daily Budget
- Accommodation: $30-$80
- Food: $20-$40
- Transport: $10-$15
- Activities: $15-$30
- Total: $75-$165/day



Code Example
from phi.assistant import Assistant
from phi.model.groq import Groq
from phi.tools.duckduckgo import DuckDuckGo

# Initialize travel agent with Groq model
travel_agent = Assistant(
    name="Travel Agent",
    model=Groq(model_name="mixtral-8x7b-32768"),
    tools=[DuckDuckGo()],
    instructions=[
        "You are a travel planning assistant...",
        "Always verify information is current before making recommendations"
    ]
)

# Generate travel plan
def generate_travel_plan(destination: str, duration: int):
    prompt = f"""
    Create a detailed travel plan for {destination} for {duration} days.
    Includes:
    - Best time to visit
    - Top attractions and activities
    - Recommend hostels in different price ranges
    - Local transportation options and tips
    - Estimated daily budget breakdown
    """
    return travel_agent.print_response(prompt, markdown=True)

generate_travel_plan("Tokyo, Japan", 7)

Repository Structure
your-repo/
│
├── travel_assistant.py        # Main script for travel planning
├── requirements.txt           # Project dependencies
├── README.md                 # Project documentation
└── LICENSE                   # License file

Requirements
The required Python libraries are listed in requirements.txt:
phidata
google-colab

Note: The phidata package includes dependencies for both Gemini and Groq models, as well as DuckDuckGo search. You must configure valid API keys for Google and Groq to use the assistant.
API Key Setup

Obtain API keys from:
Google Gemini API
Groq API


Set the keys in your environment or directly in the script:os.environ['GOOGLE_API_KEY'] = 'your-google-api-key'
os.environ['GROQ_API_KEY'] = 'your-groq-api-key'


For Google Colab, use:from google.colab import userdata
userdata.put('GROQ_API_KEY', 'your-groq-api-key')



Contributing
Contributions are welcome! To contribute:

Fork the repository.
Create a new branch (git checkout -b feature/your-feature).
Commit your changes (git commit -m 'Add your feature').
Push to the branch (git push origin feature/your-feature).
Open a pull request.

See CONTRIBUTING.md for more details.
License
This project is licensed under the MIT License - see the LICENSE file for details.
Contact
For questions or suggestions, open an issue or contact [your email or GitHub handle].
