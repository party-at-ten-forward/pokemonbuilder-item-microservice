# Pokemon Team Builder item data fetcher microservice

## Overview
This microservice fetches item data for requested items from the PokeAPI service, and sends it to the client requesting it for processing.

## Pre-requisites
- Pokemon Team Builder v0.2 project files
- Streamlit python package
  - manually downgrade pyarrow dependency to 12.0.1.
- PyZMQ python package

## Programmatic Usage

### Start Server
in python terminal simply run `python3 item_fetcher.py`

### Bind Client to server, make requests and receive response

```
# connect to zmq item data service
    context = zmq.Context() # open ZMQ Context
    socket4 = context.socket(zmq.REQ) # create ZMQ REQ socket in context
    socket4.connect("tcp://127.0.0.1:5558") # bind to specified ip:port using tcp protocol

# request
    socket4.send_pyobj(item_sel) # send item request to server
# receive
    item_received = socket4.recv_pyobj() # receive server response
```

## Implementation details
The microservice is implemented as a ZMQ server that listens for item requests made by the web-gui client. The user makes requests to the microservice via the web GUI. There is an item selection dropdown that, upon selection, sends a request to the microservice. Any requests received are sent to the PokeAPI service, and item data is fetched. The data fetched is packaged as a JSON file, and sent to the web gui. The web-gui parses specific data out, and displays it. No interaction with the code is directly required by the end user except to start the project.

![image](https://github.com/party-at-ten-forward/pokemonbuilder-item-microservice/assets/148180063/b9cd869a-06b0-4a00-a6af-244e65fbac5c)


