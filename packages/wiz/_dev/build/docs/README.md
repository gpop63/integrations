# Wiz

Wiz continuously prioritizes critical risks based on a deep cloud analysis across misconfigurations, network exposure, secrets, vulnerabilities, malware, and identities to build a single prioritized view of risk for your cloud. This [Wiz](https://www.wiz.io/) integration enables you to consume and analyze Wiz data within Elastic Security including issues, audit events, [misconfigurations](https://ela.st/cspm) and [vulnerabilities](https://ela.st/cnvm), providing you with visibility and context for your cloud environments within Elastic Security.

## Data streams

The Wiz integration collects four types of data: Audit, Cloud Configuration Finding, Issue and Vulnerability.

## Requirements

This integration supports using Elastic Agent or agentless ingestion of data.

## Elastic Agent

Elastic Agent must be installed. For more information, refer to the link [here](https://www.elastic.co/guide/en/fleet/current/elastic-agent-installation.html).

### Installing and managing an Elastic Agent:

You have a few options for installing and managing an Elastic Agent:

### Install a Fleet-managed Elastic Agent (recommended):

With this approach, you install Elastic Agent and use Fleet in Kibana to define, configure, and manage your agents in a central location. We recommend using Fleet management because it makes the management and upgrade of your agents considerably easier.

### Install Elastic Agent in standalone mode (advanced users):

With this approach, you install Elastic Agent and manually configure the agent locally on the system where it’s installed. You are responsible for managing and upgrading the agents. This approach is reserved for advanced users only.

### Install Elastic Agent in a containerized environment:

You can run Elastic Agent inside a container, either with Fleet Server or standalone. Docker images for all versions of Elastic Agent are available from the Elastic Docker registry, and we provide deployment manifests for running on Kubernetes.

There are some minimum requirements for running Elastic Agent and for more information, refer to the link [here](https://www.elastic.co/guide/en/fleet/current/elastic-agent-installation.html).

The minimum **kibana.version** required is **8.10.1**.
This module has been tested against the **Wiz API Version v1**.

## Agentless Enabled Integration

Agentless integrations allow you to collect data without having to manage Elastic Agent in your cloud. They make manual agent deployment unnecessary, so you can focus on your data instead of the agent that collects it. For more information, refer to [Agentless integrations](https://www.elastic.co/guide/en/serverless/current/security-agentless-integrations.html) and the [Agentless integrations FAQ](https://www.elastic.co/guide/en/serverless/current/agentless-integration-troubleshooting.html).

Agentless deployments are only supported in Elastic Serverless and Elastic Cloud environments.  This functionality is in beta and is subject to change. Beta features are not subject to the support SLA of official GA features.

## Setup

### To collect data from Wiz, the following parameters from your Wiz instance are required:

1. Client ID
2. Client Secret
3. Token url
4. API Endpoint url
5. Required scopes for each data stream :

    | Data Stream   | Scope         |
    | ------------- | ------------- |
    | Audit         | admin:audit   |
    | Issue         | read:issues   |
    | Vulnerability | read:vulnerabilities |
    | Cloud Configuration Finding | read:cloud_configuration |
    | Cloud Configuration Finding Full Posture | read:cloud_configuration |

### To obtain the Wiz URL
1. Navigate to your user profile and copy the API Endpoint URL.

### Steps to obtain Client ID and Client Secret:

1. In the Wiz dashboard Navigate to Settings > Service Accounts.
2. Click Add Service Account.
3. Name the new service account, for example: Elastic Integration.
4. If you desire, narrow the scope of this service account to specific projects.
5. Select the permission read:resources and click Add Service Account.
6. Copy the Client Secret. Note that you won't be able to copy it after this stage.
7. Copy the Client ID, which is displayed under the Service Accounts page.

### Enabling the integration in Elastic:

1. In Kibana go to Management > Integrations
2. In "Search for integrations" search bar, type Wiz
3. Click on the "Wiz" integration from the search results.
4. Click on the "Add Wiz" button to add the integration.
5. Add all the required integration configuration parameters, such as Client ID, Client Secret, URL, and Token URL. For all data streams, these parameters must be provided in order to retrieve logs.
6. Save the integration.

**Note:**
  - Vulnerability data_stream pulls vulnerabilities from the previous day.

## Logs Reference

### Audit

This is the `Audit` dataset.

#### Example

{{event "audit"}}

{{fields "audit"}}

### Cloud Configuration Finding

This is the `Cloud Configuration Finding` dataset.

#### Example

{{event "cloud_configuration_finding"}}

{{fields "cloud_configuration_finding"}}

### Cloud Configuration Finding Full Posture

This is the `Cloud Configuration Finding Full Posture` dataset.

#### Example

{{event "cloud_configuration_finding_full_posture"}}

{{fields "cloud_configuration_finding_full_posture"}}

### Issue

This is the `Issue` dataset.

#### Example

{{event "issue"}}

{{fields "issue"}}

### Vulnerability

This is the `Vulnerability` dataset.

#### Example

{{event "vulnerability"}}

{{fields "vulnerability"}}
