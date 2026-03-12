# Day 1 – SOC Architecture Design

The first step of the SOC Automation Lab is designing the logical architecture.

This diagram shows how data flows between the endpoint, detection platform, automation system, and the SOC analyst.

## Components

### Windows 10 Endpoint
Simulates a user workstation running the Wazuh agent.

### Wazuh Manager
Acts as the SIEM platform responsible for:
- log collection
- detection
- alert generation
- response actions

### Shuffle
Acts as the SOAR platform responsible for:
- receiving alerts from Wazuh
- automating investigation steps
- enriching indicators of compromise
- sending alerts to TheHive

### TheHive
Incident response case management platform used to track alerts and investigations.

### SOC Analyst
Receives notifications and decides whether automated response actions should be executed.

## Workflow

1. Endpoint sends telemetry to Wazuh
2. Wazuh generates an alert
3. Alert is sent to Shuffle
4. Shuffle enriches IOCs using OSINT
5. Alert is sent to TheHive
6. Email notification is sent to the SOC analyst
7. Analyst approves response action
8. Shuffle sends action to Wazuh
9. Wazuh executes response on endpoint
