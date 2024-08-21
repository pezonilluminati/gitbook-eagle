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
      "url": "https://eaglestatus.io/services/service_key",
      "icon": "https://assets.eaglestatus.io/services/service_key.png"
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
