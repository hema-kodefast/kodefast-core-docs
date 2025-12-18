# Webhook Payload & Expiry/Reminder Processing

When a document is **sent**, based on **company settings** or **document settings**, we need to send a payload to the **webhook service** as shown below.

---

## Sample Payload

```json
{
  "doc_id": "6942595283d5a7636054ff0b",
  "document_settings": {
    "expiration_settings": {
      "expired_notification_sent": false,
      "first_reminder_sent": false,
      "first_reminder_sent_at": null,
      "expire_date": "2026-01-06T07:23:41.921Z",
      "expire_after_days": 20,
      "send_first_reminder": {
        "days_before_expiration": 2,
        "enabled": true
      },
      "repeat_reminder": {
        "interval_in_days": 2,
        "enabled": true,
        "reminder_times": [16, 22],
        "time_zone": "Asia/Calcutta"
      }
    }
  },
  "expiry_link": "https://v2-dev-api.esigns.io/company-documents-v2/update/document-status/6942595283d5a7636054ff0b",
  "reminder_link": "https://v2-dev-api.esigns.io/templates-v2/responses/6942595283d5a7636054ff0b/send-reminders"
}
```

---

## Properties

### `doc_id`

- Unique document identifier.

### `document_settings`

- Configuration object related to the document.

#### `expiration_settings`

- Controls expiry and reminder behavior for the document.

##### `expire_date`

- **Mandatory** field.
- Date and time when the document expires.
- Expiry notifications are triggered based on this value.

##### `send_first_reminder`

- `enabled`: Indicates whether the first reminder should be sent.
- `days_before_expiration`: Number of days before `expire_date` when the first reminder should be triggered.

> If `send_first_reminder.enabled` is `true`, `days_before_expiration` determines the first reminder time.

##### `repeat_reminder`

- `enabled`: Enables recurring reminders.
- `interval_in_days`: Interval between reminders.
- `reminder_times`: List of hours (24-hour format) when reminders should be sent.
- `time_zone`: Time zone used to trigger reminders.

> If `repeat_reminder.enabled` is `true`, reminders are sent daily based on `reminder_times` and `time_zone`.

---

### `expiry_link`

- URL to be called when the document is expired.

### `reminder_link`

- URL to be called based on the configured reminder schedule.

---

## Required Parameters for This API

- `document_id`
- `expire_date`
- `expiry_link`
- `reminder_link`
- `timezone`

---

## How This Works

1. Based on the incoming payload, the system calculates **time slots** according to the provided **time zone**.
2. These calculated time slots are stored as **schedules in the database**.

---

## Cron Jobs Design

For each supported **time zone**, two cron jobs will be configured.

### 1. Expiry Cron

- Runs **once daily** (start or end of the day) for a specific time zone.
- Example: Indian Time Zone (Asia/Calcutta)
- Fetches all documents whose expiry schedules match the day.
- Triggers the corresponding `expiry_link`.

### 2. Reminder Cron

- Runs **hourly**, at the start of every hour, for a specific time zone.
- Example: Indian Time Zone (Asia/Calcutta)
- Fetches reminder schedules matching the current hour.
- Triggers the corresponding `reminder_link`.

---

## API Documentation

https://documenter.getpostman.com/view/8457557/2sB3dVP7rJ
