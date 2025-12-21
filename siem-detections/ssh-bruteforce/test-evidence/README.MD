# Attack commands
```
user@PC:~$ ssh root@server
root@server's password: 
Permission denied, please try again.
root@server's password: 
Permission denied, please try again.
root@server's password: 
root@server: Permission denied (publickey,password).
user@PC:~$ ssh root@server
root@server's password: 
Permission denied, please try again.
root@server's password: 
Permission denied, please try again.
root@server's password: 
root@server: Permission denied (publickey,password).
user@PC:~$ 
```
# Elasticsearch logs
![Image of logs from Elasticsearch showing 6 failed login attempts](siem-detections/ssh-bruteforce/test-evidence/images/SSHElasticLog.png)

# Attack detection log
```
{
  "@timestamp": [
    "2025-12-19T03:38:34.520Z"
  ],
  "event.kind": [
    "signal"
  ],
  "kibana.alert.ancestors.depth": [
    0
  ],
  "kibana.alert.ancestors.id": [
    "16b6bd30-abbe-5141-bca9-7ae3413934d4"
  ],
  "kibana.alert.ancestors.index": [
    "apm-*-transaction*,auditbeat-*,endgame-*,filebeat-*,logs-*,packetbeat-*,traces-apm*,winlogbeat-*,-*elastic-cloud-logs-*"
  ],
  "kibana.alert.ancestors.type": [
    "event"
  ],
  "kibana.alert.depth": [
    1
  ],
  "kibana.alert.intended_timestamp": [
    "2025-12-19T03:38:34.520Z"
  ],
  "kibana.alert.last_detected": [
    "2025-12-19T03:38:34.659Z"
  ],
  "kibana.alert.original_time": [
    "2025-12-19T03:37:26.109Z"
  ],
  "kibana.alert.reason": [
    "event with source 192.168.1.21 created medium alert SSH Brute force login detected."
  ],
  "kibana.alert.reason.text": [
    "event with source 192.168.1.21 created medium alert SSH Brute force login detected."
  ],
  "kibana.alert.risk_score": [
    47
  ],
  "kibana.alert.rule.actions.action_type_id": [
    ".index"
  ],
  "kibana.alert.rule.actions.frequency.notifyWhen": [
    "onActiveAlert"
  ],
  "kibana.alert.rule.actions.frequency.summary": [
    true
  ],
  "kibana.alert.rule.actions.group": [
    "default"
  ],
  "kibana.alert.rule.actions.id": [
    "6dc7fcdc-1753-4d31-81a2-e50eb0f0d3a7"
  ],
  "kibana.alert.rule.actions.params.documents.host": [
    "{{context.host.hostname}}"
  ],
  "kibana.alert.rule.actions.params.documents.message": [
    "SSH brute force alert for RPI server"
  ],
  "kibana.alert.rule.actions.params.documents.rule_name": [
    "{{rule.name}}"
  ],
  "kibana.alert.rule.actions.params.documents.source_ip": [
    "{{context.group.source.ip}}"
  ],
  "kibana.alert.rule.actions.uuid": [
    "bf776b78-66c5-42f9-b21f-c4a74db0dc9c"
  ],
  "kibana.alert.rule.category": [
    "Threshold Rule"
  ],
  "kibana.alert.rule.consumer": [
    "siem"
  ],
  "kibana.alert.rule.created_at": [
    "2025-12-19T02:58:28.767Z"
  ],
  "kibana.alert.rule.created_by": [
    "elastic"
  ],
  "kibana.alert.rule.description": [
    "A threshold of 5 or more failed ssh login attempts has been exceeded"
  ],
  "kibana.alert.rule.enabled": [
    "true"
  ],
  "kibana.alert.rule.execution.timestamp": [
    "2025-12-19T03:38:34.659Z"
  ],
  "kibana.alert.rule.execution.type": [
    "scheduled"
  ],
  "kibana.alert.rule.execution.uuid": [
    "562776e9-fb05-43b2-b4d1-bce650e37064"
  ],
  "kibana.alert.rule.from": [
    "now-6m"
  ],
  "kibana.alert.rule.immutable": [
    "false"
  ],
  "kibana.alert.rule.indices": [
    "apm-*-transaction*",
    "auditbeat-*",
    "endgame-*",
    "filebeat-*",
    "logs-*",
    "packetbeat-*",
    "traces-apm*",
    "winlogbeat-*",
    "-*elastic-cloud-logs-*"
  ],
  "kibana.alert.rule.interval": [
    "5m"
  ],
  "kibana.alert.rule.license": [
    ""
  ],
  "kibana.alert.rule.max_signals": [
    100
  ],
  "kibana.alert.rule.meta.kibana_siem_app_url": [
    "http://192.168.1.55:5601/app/security"
  ],
  "kibana.alert.rule.name": [
    "SSH Brute force login detected"
  ],
  "kibana.alert.rule.parameters": [
    {
      "severity": "medium",
      "max_signals": 100,
      "rule_source": {
        "type": "internal"
      },
      "risk_score": 47,
      "query": "process.name: \"sshd\" AND event.action: \"ssh_login\" AND event.outcome: \"failure\" ",
      "description": "A threshold of 5 or more failed ssh login attempts has been exceeded",
      "index": [
        "apm-*-transaction*",
        "auditbeat-*",
        "endgame-*",
        "filebeat-*",
        "logs-*",
        "packetbeat-*",
        "traces-apm*",
        "winlogbeat-*",
        "-*elastic-cloud-logs-*"
      ],
      "language": "kuery",
      "threshold": {
        "field": [
          "source.ip"
        ],
        "value": 5,
        "cardinality": [
          {
            "field": "@timestamp",
            "value": 5
          }
        ]
      },
      "type": "threshold",
      "version": 1,
      "rule_id": "3c9e55d4-fac2-47f0-96eb-b705f819dacc",
      "license": "",
      "immutable": false,
      "meta": {
        "kibana_siem_app_url": "http://192.168.1.55:5601/app/security"
      },
      "setup": "",
      "from": "now-6m",
      "to": "now"
    }
  ],
  "kibana.alert.rule.producer": [
    "siem"
  ],
  "kibana.alert.rule.revision": [
    3
  ],
  "kibana.alert.rule.risk_score": [
    47
  ],
  "kibana.alert.rule.rule_id": [
    "3c9e55d4-fac2-47f0-96eb-b705f819dacc"
  ],
  "kibana.alert.rule.rule_type_id": [
    "siem.thresholdRule"
  ],
  "kibana.alert.rule.severity": [
    "medium"
  ],
  "kibana.alert.rule.to": [
    "now"
  ],
  "kibana.alert.rule.type": [
    "threshold"
  ],
  "kibana.alert.rule.updated_at": [
    "2025-12-19T03:34:07.279Z"
  ],
  "kibana.alert.rule.updated_by": [
    "elastic"
  ],
  "kibana.alert.rule.uuid": [
    "23e84c86-b650-4235-b66c-1f509fc1ad73"
  ],
  "kibana.alert.rule.version": [
    "1"
  ],
  "kibana.alert.severity": [
    "medium"
  ],
  "kibana.alert.start": [
    "2025-12-19T03:38:34.659Z"
  ],
  "kibana.alert.status": [
    "active"
  ],
  "kibana.alert.threshold_result.cardinality.field": [
    "@timestamp"
  ],
  "kibana.alert.threshold_result.cardinality.value": [
    6
  ],
  "kibana.alert.threshold_result.count": [
    6
  ],
  "kibana.alert.threshold_result.from": [
    "2025-12-19T03:37:02.179Z"
  ],
  "kibana.alert.threshold_result.terms.field": [
    "source.ip"
  ],
  "kibana.alert.threshold_result.terms.value": [
    "192.168.1.21"
  ],
  "kibana.alert.uuid": [
    "a820e92786dbfcdd4fd08b9b12938649710b4caa634ec479510d7979878c1c95"
  ],
  "kibana.alert.workflow_status": [
    "open"
  ],
  "kibana.space_ids": [
    "default"
  ],
  "kibana.version": [
    "8.19.8"
  ],
  "signal.ancestors.depth": [
    0
  ],
  "signal.ancestors.id": [
    "16b6bd30-abbe-5141-bca9-7ae3413934d4"
  ],
  "signal.ancestors.index": [
    "apm-*-transaction*,auditbeat-*,endgame-*,filebeat-*,logs-*,packetbeat-*,traces-apm*,winlogbeat-*,-*elastic-cloud-logs-*"
  ],
  "signal.ancestors.type": [
    "event"
  ],
  "signal.depth": [
    1
  ],
  "signal.original_time": [
    "2025-12-19T03:37:26.109Z"
  ],
  "signal.reason": [
    "event with source 192.168.1.21 created medium alert SSH Brute force login."
  ],
  "signal.rule.created_at": [
    "2025-12-19T02:58:28.767Z"
  ],
  "signal.rule.created_by": [
    "elastic"
  ],
  "signal.rule.description": [
    "A threshold of 5 or more failed ssh login attempts has been exceeded"
  ],
  "signal.rule.enabled": [
    "true"
  ],
  "signal.rule.from": [
    "now-6m"
  ],
  "signal.rule.id": [
    "23e84c86-b650-4235-b66c-1f509fc1ad73"
  ],
  "signal.rule.immutable": [
    "false"
  ],
  "signal.rule.interval": [
    "5m"
  ],
  "signal.rule.license": [
    ""
  ],
  "signal.rule.max_signals": [
    100
  ],
  "signal.rule.name": [
    "SSH Brute force login detected"
  ],
  "signal.rule.risk_score": [
    47
  ],
  "signal.rule.rule_id": [
    "3c9e55d4-fac2-47f0-96eb-b705f819dacc"
  ],
  "signal.rule.severity": [
    "medium"
  ],
  "signal.rule.to": [
    "now"
  ],
  "signal.rule.type": [
    "threshold"
  ],
  "signal.rule.updated_at": [
    "2025-12-19T03:34:07.279Z"
  ],
  "signal.rule.updated_by": [
    "elastic"
  ],
  "signal.rule.version": [
    "1"
  ],
  "signal.status": [
    "open"
  ],
  "signal.threshold_result.cardinality.field": [
    "@timestamp"
  ],
  "signal.threshold_result.cardinality.value": [
    6
  ],
  "signal.threshold_result.count": [
    6
  ],
  "signal.threshold_result.from": [
    "2025-12-19T03:37:02.179Z"
  ],
  "signal.threshold_result.terms.field": [
    "source.ip"
  ],
  "signal.threshold_result.terms.value": [
    "192.168.1.21"
  ],
  "source.ip": [
    "192.168.1.21"
  ],
  "_id": "a820e92786dbfcdd4fd08b9b12938649710b4caa634ec479510d7979878c1c95",
  "_index": ".internal.alerts-security.alerts-default-000001",
  "_score": null
}
```
