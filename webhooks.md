# Webhooks Quick Start

{% hint style="info" %}
**Good to know:** Webhooks are a powerful way to receive real-time updates from Eagle Status. This quick start guide will help you set up and start receiving alerts via webhook in just a few steps.
{% endhint %}

## Overview

The Eagle Status webhook sends alerts every 5 minutes, based on the user's configured services. You will receive a JSON payload only if there are changes to report during that time period.

## Webhook Payload

When an alert is triggered, the webhook sends a JSON payload with the following structure:

```json
{
    "checkedAt": "2023-08-21T14:30:00Z",
    "service": {
      "key": "service_key",
      "name": "Service Name",
      "status": "UP", 
      "url": "Service url",
      "icon": "Service icon url"
    },
    "changedComponents": [
      {
        "key": "service_key/component_key",
        "name": "Component Name", 
        "status": "UP|DOWN|UNDER_MAINTENANCE|DEGRADED_PERFORMANCE|PARTIAL_OUTAGE",
        "fullName": "Service Name / Component Name"
      },
      {
        "key": "service_key/another_component_key",
        "name": "Another Component Name",
        "status": "UP|DOWN|UNDER_MAINTENANCE|DEGRADED_PERFORMANCE|PARTIAL_OUTAGE",
        "fullName": "Service Name / Another Component Name"
      }
    ]
}
```
## Field Descriptions

- **checkedAt:** The ISO 8601 string representing the time when the status check was performed (e.g., `"2023-08-21T14:30:00Z"`).
- **service:** An object containing details about the service being monitored:
  - **key:** A unique identifier for the service (e.g., `"service_key"`).
  - **name:** The name of the service (e.g., `"Service Name"`).
  - **status:** The current status of the service (`UP`, `DOWN`, etc.).
  - **url:** A link to the service's status page on Eagle Status.
  - **icon:** A URL to the service's icon.
- **changedComponents:** An array of components within the service that have experienced a status change:
  - **key:** A unique identifier for the component (e.g., `"service_key/component_key"`).
  - **name:** The name of the component (e.g., `"Component Name"`).
  - **status:** The new status of the component.
  - **fullName:** A full name that combines the service and component names (e.g., `"Service Name / Component Name"`).

{% hint style="info" %}
**Good to know:** If no components have changed within the 5-minute interval, the webhook will not send any payload.
{% endhint %}
