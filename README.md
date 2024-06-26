# Node.js Distributed Database System

## Introduction

This project is a Node.js application for a distributed database system called ursoDB. It consists of several components, including a reverse proxy server (RP) and a group of logical data nodes (DN). The system architecture is defined by a configuration file `configure.json`, residing in the `ursoDB/etc` subdirectory, and is shared by all HTTP servers.

## Group 4

- Ricardo Soares
- Miguel Moreira

## Requirements

- Node.js ecosystem with:
  - Express
  - Winston module for logging
  - Axios module for executing HTTP requests
- System start/stop/restart via `ursoDB` command
- RP must be kept alive via `forever`

## Endpoints

### Common to ALL servers:

- `/status`: Get the current system status.
- `/stats`: Get the statistics associated with the service.
- `/admin/loglevel`: Change the server debug level.
- `/db/c`: Create a key-value pair in the database.
- `/db/r`: Read and return the value associated with a key in the database.
- `/db/u`: Update a key-value pair in the database.
- `/db/d`: Delete a key-value pair from the database.
- `/stop`: Stop the node.

### RP specific:

- `/set_master`: Used by the elected master of a DN to set the master node.

### DN specific:

- `/election`: Exchange information to establish the master of the DN.
- `/maintenance`: Exchange data to synchronize all data correctly in each DN server.
