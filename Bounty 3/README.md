# Bounty 3: YouTube Analytics Pipeline

This bounty expands Pleblab's analytics system by adding automated data collection from the YouTube API. The goal is to pull channel-level statistics and store them in the PostgreSQL database for future visualization and reporting.

## Objective

Build a pipeline that retrieves YouTube channel metrics such as views, subscribers, and video count, and stores them in the analytics database on a scheduled basis.

## Deliverables

- Create a new table in the analytics PostgreSQL database (`youtube_pleblab`)
- Set up a scheduled Zapier pipeline that:
  - Calls the YouTube API
  - Parses the channel statistics
  - Stores them with a timestamp in the database
- Create a basic Looker Studio dashboard to confirm data ingestion

## Scope

- This bounty focuses on backend data automation only
- No frontend or interface development required
- The pipeline should be designed to run automatically on a schedule (e.g., daily)

## Timeline

- Deadline: Tuesday, April 12
- Reward: $70 USD

## Database Schema

SQL for the target table:

```sql
CREATE TABLE youtube_pleblab (
  date DATE,
  timestamp TIMESTAMPTZ DEFAULT NOW(),
  view_count BIGINT,
  subscriber_count BIGINT,
  video_count BIGINT
);
```

## YouTube API Endpoint

Data is retrieved from:

```
https://www.googleapis.com/youtube/v3/channels?part=statistics&id=CHANNEL_ID&key=YOUR_API_KEY
```

- Replace `CHANNEL_ID` with Pleblab’s actual YouTube channel ID
- Replace `YOUR_API_KEY` with the generated key from Google Cloud

## Dashboard

To view the collected data, visit the Looker Studio dashboard:  
[https://lookerstudio.google.com/reporting/c7222b3c-70cd-4471-8481-d50021e2e522](https://lookerstudio.google.com/reporting/c7222b3c-70cd-4471-8481-d50021e2e522)
```