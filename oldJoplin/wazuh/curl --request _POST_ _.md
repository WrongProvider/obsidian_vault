curl --request 'POST' \
  --url 'https://events.pagerduty.com/v2/enqueue' \
  --header 'Content-Type: application/json' \
  --data '{
    "payload": {
        "summary": "Test Incident",
        "severity": "critical",
        "source": "Default Service on fire!"
    },
    "routing_key": "36e630b908f34900d05357a634bddc46",
    "event_action": "trigger"
  }'


<integration>
    <name>custom-teams</name>
    <hook_url>https://aim7inf.webhook.office.com/webhookb2/80417f33-3ee2-4ec6-893e-a2d472e0c555@5a74019a-bd28-47d6-81dd-c76cde0e99de/IncomingWebhook/061b0627d34f46c0a58c82db131f6e8e/7f5aa97d-77bd-45ed-86b2-b50e1fd594b2</hook_url> <!-- teams webhook-->
    <level>12</level>
    <alert_format>json</alert_format>
</integration>

  <integration>
    <name>custom-w2thive</name>
    <hook_url>http://192.168.0.22:9000</hook_url>
    <api_key>FAYIBeQI9ktNn6INV2DqPzM9h18cajDY</api_key>
    <alert_format>json</alert_format>
  </integration>

FAYIBeQI9ktNn6INV2DqPzM9h18cajDY