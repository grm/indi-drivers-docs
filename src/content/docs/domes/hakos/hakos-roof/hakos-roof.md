---
title: Hakos Roll Off Roof
categories: ["domes"]
description: INDI driver for the Hakos Observatory Roll Off Roof system with REST API integration
thumbnail: ./hakos-roof.webp
---

## Overview

The Hakos Roll Off Roof driver is an INDI dome controller for the Hakos Observatory's roll-off roof system. It provides basic roof control through a REST API interface, allowing remote operation of the observatory roof.

It doesn't not direct integration with weather drivers. The weather condition is read through Ekos, so a Danger will trigger roof parking.

**Key Features:**
- Real-time roof status monitoring
- Abort and parking capabilities
- JSON-based configuration


## Operation

### Options Tab

The first step is to configure the access to the Roof Control System:

- **Data Source URL**: The HTTP endpoint for the roof control system (e.g., `http://hakos-roof.local/`)
- **Roof Token**: Security string given for your roof
- **Mount Policy**: Ignore  the mount parking status. USE WITH CARE!

### Main Control Tab

To operate the roof there are commands in the Main Control Tab

**Roof Motion Controls:**
- **Unparked**: Send command to open the roof
- **Parked**: Send command to close the roof
- **Abort**: Stop any in-progress roof movement
- **Open** and **Close**: Do not affect the roof motion (needed in Domes only)

**Roof Data:**
- **Last Command**: Shows the most recent command sent
- **Status**: Current operational status (Opening, Closing, Open, Closed, Error)
- **Position**: Roof position percentage (0-100%), the position is not accurate, don't rely on it.



## Technical Details

### INDI Properties

The driver implements contemporary INDI properties:

- `RoofDataTP`: Text properties for status information
  - `MSG`: Last command sent
  - `STAT`: Internal status code
  - `STEXT`: Human-readable status text
  - `POS`: Roof position percentage

- `DomeMotionSP`: Switch property for roof control
  - `OPEN`: Send open command
  - `CLOSE`: Send close command
  - `ABORT`: Stop movement



## Version History

### Version 1.3 (Current)
- Refactor to use INDI::PropertyText and INDI::PropertySwitch
- Improved macOS compatibility
- Enhanced error handling
- Added JSON parsing for REST responses

### Version 1.2
- Fixed dome connection initialization
- Added status caching

### Version 1.1
- Initial REST API implementation


## License

GNU General Public License v2 (GPLv2)

## Author

Ferrante Enriques  
Copyright (c) 2026 INDI Developers
