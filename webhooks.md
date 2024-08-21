# Webhooks Quick Start


## Overview

The EagleStatus Webhook sends alerts based on the user's configured services. You will receive a JSON payload only when there are changes to report.

## Setting Up

To get started, simply add a valid webhook in the Integration section of Eagle Status. Ensure that your server is configured to handle JSON payloads.

## Webhook Payload

When an alert is triggered, the webhook sends a JSON payload with the following structure:

```json
{
    "checkedAt": "2023-08-21T14:30:00Z",
    "service": {
      "key": "github",
      "name": "Github",
      "status": "UP", 
      "url": "https://eaglestatus.io/services/github",
      "icon": "https//assets.eaglestatus.io/services/github.png"
    },
    "changedComponents": [
      {
        "key": "github/pages",
        "name": "Pages", 
        "status": "UP",
        "fullName": "Github / Pages"
      },
      {
        "key": "github/actions",
        "name": "Actions",
        "status": "DEGRADED_PERFORMANCE",
        "fullName": "Github / Actions"
      }
    ]
}
```
## Field Descriptions

- **checkedAt:** The ISO 8601 string representing the time when the status check was performed (e.g., `"2023-08-21T14:30:00Z"`).
- **service:** An object containing details about the service being monitored:
  - **key:** A unique identifier for the service (e.g., `"github"`).
  - **name:** The name of the service (e.g., `"Github"`).
  - **status:** The current status of the service (`UP`, `DOWN`,`UNDER_MAINTENANCE`, `DEGRADED_PERFORMANCE`,`PARTIAL_OUTAGE`).
  - **url:** The URL of the service’s status page on Eagle Status.
  - **icon:** A URL to the service's icon.
- **changedComponents:** An array of components within the service that have experienced a status change:
  - **key:** A unique identifier for the component (e.g., `"github/actions"`).
  - **name:** The name of the component (e.g., `"Actions"`).
  - **status:** The new status of the component.
  - **fullName:** A full name that combines the service and component names (e.g., `"Github / Actions"`).

