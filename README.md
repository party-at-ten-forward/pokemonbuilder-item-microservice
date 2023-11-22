# Pokemon Team Builder item data fetcher microservice

## Overview
This microservice fetches item data for requested items from the PokeAPI service, and sends it to the client requesting it for processing.

## Pre-requisites
- Pokemon Team Builder v0.2 project files
- Streamlit python package
  - manually downgrade pyarrow dependency to 12.0.1.
- PyZMQ python package

## Usage
- start PokemonTeamBuilder using `streamlit run web-gui.py`
- open a browser and navigate to the specified URL in the terminal.
- use the web GUI to select items and display fetched item data

## Implementation details
The microservice is implemented as a ZMQ server that listens for item requests made by the web-gui client. The user makes requests to the microservice via the web GUI. There is an item selection dropdown that, upon selection, sends a request to the microservice. Any requests received are sent to the PokeAPI service, and item data is fetched. The data fetched is packaged as a JSON file, and sent to the web gui. The web-gui parses specific data out, and displays it. No interaction with the code is directly required by the end user except to start the project.

![image](https://github.com/party-at-ten-forward/pokemonbuilder-item-microservice/assets/148180063/b9cd869a-06b0-4a00-a6af-244e65fbac5c)


