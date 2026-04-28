# Risk Management

## FTP Log Analysis and Threat Detection Using Splunk

---

## Purpose

Risk management helps identify potential problems that could affect the success of the project and provides solutions to reduce those risks.

For this project, we identified technical, scheduling, and team coordination risks that could impact project completion.

By planning for these risks early, we improved the chances of completing the project successfully and on time.

---

## Risk Assessment Table

| Risk | Probability | Impact | Mitigation Strategy |
|---|---|---|---|
| Splunk installation issues | Medium | High | Use official documentation, tutorials, and troubleshooting guides |
| FTP logs not generating correctly | Medium | Medium | Use sample logs if live FTP logs are unavailable |
| Incorrect log parsing | Medium | High | Test source type settings and verify field extraction early |
| Time range search problems | High | Medium | Change Splunk time settings to All Time during verification |
| Dashboard creation difficulties | Medium | Medium | Use simple statistics tables instead of complex visualizations |
| Alert configuration errors | Medium | Medium | Use basic triggered alerts instead of advanced actions |
| Time constraints before deadline | High | High | Follow strict weekly milestones and complete high-priority tasks first |
| Team coordination issues | Low | Medium | Hold weekly check-ins and maintain communication through GitHub and group chat |
| Limited hardware resources | Low | Medium | Use free trial tools and lightweight sample log files |
| Lack of Docker experience | Medium | Low | Use local Splunk installation and document Docker as an alternative option |

---

## High Priority Risks

### Splunk Installation Issues

Splunk setup was one of the highest risks because the entire project depended on successful installation and configuration.

Mitigation:
We used the Splunk Enterprise Free Trial and followed official setup instructions to reduce installation problems.

---

### Time Constraints

Since the project had a fixed semester deadline, time management was critical.

Mitigation:
We followed a structured timeline and focused first on the most important deliverables such as log ingestion, dashboard creation, and alerts.

---

### Log Visibility Problems

Logs were uploaded successfully but initially did not appear due to incorrect time range filters.

Mitigation:
We changed the time range from “Last 24 Hours” to “All Time,” which resolved the issue immediately.

---

## Medium Priority Risks

### Dashboard and Alert Setup Complexity

Splunk dashboard creation and alert setup required additional learning and troubleshooting.

Mitigation:
We used simple table-based panels and standard triggered alerts instead of advanced configurations.

---

### Log Generation Issues

If a live FTP server failed to generate logs properly, project progress could stop.

Mitigation:
We prepared structured sample FTP logs to guarantee that analysis could continue without delay.

---

## Low Priority Risks

### Team Communication Problems

Miscommunication could delay progress or duplicate work.

Mitigation:
We maintained regular communication through GitHub updates and group messaging to keep tasks organized.

---

## Final Risk Evaluation

Most project risks were successfully controlled through planning, documentation, and simplified implementation choices.

The decision to use the Splunk Enterprise Free Trial instead of Docker reduced setup complexity and allowed the team to focus on the actual security monitoring objectives.

By identifying risks early and using clear mitigation strategies, the project remained on schedule and achieved all major deliverables successfully.

---
