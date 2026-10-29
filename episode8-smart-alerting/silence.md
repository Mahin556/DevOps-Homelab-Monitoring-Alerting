In Prometheus Alertmanager, Silence temporarily suppresses notifications for alerts that match specified conditions. It does not stop Prometheus from evaluating rules, and it does not resolve the alert.

## 1. Create a silence in the Alertmanager dashboard

[Get alerts from your Open Liberty apps in Slack using Prometheus Alertmanager - OpenLiberty.io](https://images.openai.com/static-rsc-4/yIcRptxmoqy3FYpgEawssvLoLRnYGrp_4C931WPY8_v6fMaObVMLcSeBqGhlm2LrzpajZBn3cQZP1fqNlU67n_OycXs_2QtHSbg5bZA7u4EPVI5mCTd5gIvZqEuU_8n-IxReKJNN5lU-SCLVZQlPQ7hYG6khMGnlsbDAA9eDIJs?purpose=inline)

Step 1: Open Alertmanager

Open your Alertmanager URL, commonly `http://<alertmanager-host>:9093`.

[Effective Alerting with Prometheus Alertmanager | Better Stack Community](https://images.openai.com/static-rsc-4/jV50_H6-3DLoub_OZPA_vZZ0BYeSZGbos1UerKXGRglPhF2ccsm885JptiMMyCrba1-ieB2Tto7Sfd5RTjZGGHTELgJoqpJvDrBJ9fL26W6qwjm-Hta4sT4O6LkhESKy88AMhB6uO8kIv61fKIk2wFJ5OSZwe13V5lBJ3-0wc8g?purpose=inline)

Step 2: Create a silence

Go to Silences → New Silence and configure the matchers for the alerts you want to silence.

[Docker - Prometheus and Grafana with Docker-compose - 2020](https://images.openai.com/static-rsc-4/fcM7ff6YdNe0-dLjQkzSihVkpn6ABm-2lzJK5cPk_2L1fjpc4lTL1gRg54Oj8rp5tEjeWbTYr-8Q-RVQ3z58vldJEJ0WpGQx2BH6KqWVklrkimB3lUEiqOEVPItcmubWlBnRoYONntfI4ErS5DqFt1DTNsgo6Ypt1y21b5kdGVM?purpose=inline)

Step 3: Set duration and save

Set the start and end times, add a comment explaining why, and create the silence.

## 2. Silence alerts using the CLI

If `amtool` is installed and configured:

```
# Silence one alert for 2 hours
amtool silence add \
  --duration=2h \
  --comment="Maintenance window" \
  alertname="HighCPUUsage"

# Silence alerts from a specific instance
amtool silence add \
  --duration=1h \
  --comment="Server maintenance" \
  instance="192.168.1.10:9100"

# View existing silences
amtool silence query

# Expire a silence early
amtool silence expire <SILENCE_ID>
```

These commands follow the official Alertmanager CLI documentation.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://github.com\&sz=32)

GitHub+1



## 3. Choose the right silence matcher

| Matcher                    | What it silences                   |
| -------------------------- | ---------------------------------- |
| `alertname="HighCPUUsage"` | Only that alert type               |
| `instance="server1:9100"`  | Alerts from that instance          |
| `severity="warning"`       | All warning alerts                 |
| `alertname=~".*"`          | All alert names matching the regex |

Important: To silence all alerts, use a matcher that matches all alert labels, such as `alertname=~".*"`, provided your alerts all have an `alertname` label.

## 4. Silence vs. inhibition vs. disabling

- Silence: Temporarily stops notifications for matching alerts.
- Inhibition: Suppresses notifications for certain alerts when another related alert is firing.
- Disable alerting: Changes the alerting rules or notification configuration; the alert may no longer be evaluated or delivered as before.

See the official [Alertmanager documentation](https://prometheus.io/docs/alerting/latest/alertmanager/?utm_source=chatgpt.com).&#x20;

[image](https://www.google.com/s2/favicons?domain=https://prometheus.io\&sz=32)

Prometheus+1



What do you want to silence?

One specific alert

All alerts from one server

All alerts temporarily

Recurring silence during maintenance hours

Duration

30 minutes

2 hours

24 hours

Until manually expired

Show configuration
