Is a web-based Ui in [[Kibana]] for centrally managing [[Elastic Agents]] and their policies
Using Fleet:
- Fleet server deployed
- Kibana user with privileges.
## Fleet UI:
### Package Manager
The Fleet package manager is used behind the scenes to both manage and explain integrations provided by Elastic via Beats an Elastic Agent. Typically requires an internet connection because integrations are updated and released periodically, for air-gapped environments, a local package repository can be used.
### Integrations Page
Connects Elastic to external services and systems, can collect new sources of data, supports air-gapped environments and often ships with out-of-the-box assets.
### Policy Builder
Create an Agent policy to enroll Agents into, an Agent policy is set of individual integrations, each integration provides several settings.
### Agent Policies
Attach integrations to the Agent policy, multiple agents can be assigned to one policy, configure settings under each integration attached to the policy.
### Agents
Centrally manage your deployed Agents, monitor/troubleshoot Agents status and deployment.

## Fleet Server
Used to centrally manage Elastic Agents, it allows remote Elastic Agents to communicate with Elasticserach, deployed as a special agent policy via Elastic Agent. Allows for a scalable infrastructure, supported in Elastic Cloud and self-managed.
