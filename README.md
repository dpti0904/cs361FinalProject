# Communication Contract

How to Request Data: 

To programmatically request data from the microservice, send a POST request to the /format_chess_log endpoint with the JSON data containing the chess log. The JSON data should be structured as a list of dictionaries, where each dictionary represents a move in the chess game. Each move dictionary should contain the following fields:

"turn": The player's turn (e.g., "white" or "black").
"piece": The type of chess piece making the move (e.g., "pawn", "knight", "bishop", "rook", "queen", "king").
"starting square": The square from which the piece is moving (e.g., "e2").
"ending square": The square to which the piece is moving (e.g., "e4").
"piece captured": A boolean indicating whether a piece is captured during the move (True or False).

Example call to request data:

import requests
import json

# Define the JSON data representing the chess log
json_data = [
    {"turn": "white", "piece": "pawn", "starting square": "e2", "ending square": "e4", "piece captured": False},
    {"turn": "black", "piece": "pawn", "starting square": "e7", "ending square": "e5", "piece captured": False},
    # Add more moves as needed
]

# Send a POST request to the microservice
response = requests.post('http://localhost:5000/format_chess_log', json=json_data)

# Process the response
formatted_log = response.json()['formatted_log']
print(formatted_log)

How to Receive Data:
The microservice responds to POST requests sent to the /format_chess_log endpoint. It returns the formatted chess log as a JSON object containing a single field: "formatted_log", which holds the formatted moves of the chess game.


# How to receive data



![Screenshot 2024-03-11 171652](https://github.com/dpti0904/cs361FinalProject/assets/133840526/5d375f6b-02c3-48e7-b667-4499a51a70ab)


Example of receiving data:

import requests

# Send a POST request to the Flask microservice with the JSON data
response = requests.post('http://localhost:5000/format_chess_log', json=json_data)

# Get the formatted log from the response
formatted_log = response.json()['formatted_log']

# Print the formatted log
print(formatted_log)
