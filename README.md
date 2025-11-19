# Assignment_1_Jaime_Brieva_9440


import requests
import json

#testing1
APP_TOKEN = 'bo4pPeWZdBf3HaJ9djEHPnRJM'

BASE_URL = "https://data.cityofnewyork.us/api/v3/views/c3uy-2p5r/query.json"

params = {
    "$$app_token": APP_TOKEN, # <-- ADD THE TOKEN HERE
    "$limit": 5000,
    "$where": "indicator_name='Fine particles (PM 2.5)'"
}

try:
    response = requests.get(BASE_URL, params=params)
    response.raise_for_status() # Check for 4xx or 5xx errors
    data = response.json()
    print(f"Success! Fetched {len(data)} records.")

except requests.exceptions.HTTPError as err:
    print(f"Error: {err}. Double-check your App Token.")
except Exception as err:
    print(f"An unexpected error occurred: {err}")
