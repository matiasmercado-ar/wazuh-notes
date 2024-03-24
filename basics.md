
# Community links

Slack Wazuh: wazuh.slack.com
Google groups: https://groups.google.com/g/wazuh
GitHub Code: https://github.com/wazuh
Wazuh Cloud: https://wazuh.com/cloud/

# Docs on h-t install wazuh
### Quickstart: https://documentation.wazuh.com/current/quickstart.html
### Full instalation guide: https://documentation.wazuh.com/current/installation-guide/index.html
### Docker install: https://documentation.wazuh.com/current/deployment-options/docker/docker-installation.html
### Kubernetes install: https://documentation.wazuh.com/current/deployment-options/deploying-with-kubernetes/kubernetes-deployment.html


# Requirements

### Hardware
depend on the number of protected endpoints and cloud workloads

Following this quickstart implies deploying the Wazuh server, the Wazuh indexer, and the Wazuh dashboard on the same host. This is usually enough for monitoring up to 100 endpoints and for 90 days of queryable/indexed alert data.

| Agents | CPU    | RAM   | Storage (90 days) |
|--------|--------|-------|-------------------|
| 1–25   | 4 vCPU | 8 GiB | 50 GB             |
| 25–50  | 8 vCPU | 8 GiB | 100 GB            |
| 50–100 | 8 vCPU | 8 GiB | 200 GB            |

For larger environments, we recommend a distributed deployment. Multi-node cluster configuration is available for the Wazuh server and for the Wazuh indexer, providing high availability and load balancing.

### Software
| Operating System        | Versions           |
|-------------------------|--------------------|
| Amazon Linux 2          |                    |
| CentOS                  | 7, 8               |
| Red Hat Enterprise Linux| 7, 8, 9            |
| Ubuntu                  | 16.04, 18.04, 20.04, 22.04 |

# Wazuh Central Components

All components could be installed in a single host or in multiple hosts. Depends on this is the installation procedure you have to follow. 

## Indexer 📄

Engine full text search and analytics. It's scalable. This component indexes and store alerts generated bu Wazuh server and provides real time data search and analytics capabilities

#### Hardware recommendations for each node

| Component      | RAM (GB) - Minimum | CPU (cores) - Minimum | RAM (GB) - Recommended | CPU (cores) - Recommended |
|----------------|--------------------|-----------------------|-------------------------|----------------------------|
| Wazuh indexer | 4                  | 2                     | 16                      | 8                          |

#### Disk space requirements

The amount of data depends on the generated alerts per second (APS). This table details the estimated disk space needed per agent to store 90 days of alerts on a Wazuh indexer server, depending on the type of monitored endpoints.

| Monitored endpoints | APS  | Storage in Wazuh indexer (GB/90 days) |
|---------------------|------|---------------------------------------|
| Servers             | 0.25 | 3.7                                   |
| Workstations        | 0.1  | 1.5                                   |
| Network devices     | 0.5  | 7.4                                   |

For an environment with 80 workstations, 10 servers, and 10 network devices, the storage of Indexer server for 90 days of alerts is 230 GB.

Installation Step-by-step: https://documentation.wazuh.com/current/installation-guide/wazuh-indexer/step-by-step.html

Unistall indexer: https://documentation.wazuh.com/current/installation-guide/uninstalling-wazuh/central-components.html#uninstall-indexer

## Server 🧠 

Analyze the data received from the agents, triggers alerts for threats or anomalies. Can manage the agents configuration and monitor the status. 

Installation step-by-step: https://documentation.wazuh.com/current/installation-guide/wazuh-server/step-by-step.html


Unistall server: https://documentation.wazuh.com/current/installation-guide/uninstalling-wazuh/central-components.html#uninstall-server


### Hardware recommendations

| Component       | RAM (GB) - Minimum | CPU (cores) - Minimum | RAM (GB) - Recommended | CPU (cores) - Recommended |
|-----------------|--------------------|-----------------------|-------------------------|----------------------------|
| Wazuh server    | 2                  | 2                     | 4                       | 8                          |


## Dashboard 📈

Web interface for mining, analyzing and visualizing security data. With the Wazuh dashboard, users can visualize security events, detected vulnerabilities, file integrity monitoring data, configuration assessment results, cloud infrastructure monitoring events, and regulatory compliance standards


#### Hardware recommendations

| Component         | RAM (GB) - Minimum | CPU (cores) - Minimum | RAM (GB) - Recommended | CPU (cores) - Recommended |
|-------------------|--------------------|-----------------------|-------------------------|----------------------------|
| Wazuh dashboard  | 4                  | 2                     | 8                       | 4                          |

Wazuh dashboard supports the following web browsers:

    Chrome 95 or later

    Firefox 93 or later

    Safari 13.7 or later

Installation step-by-step: https://documentation.wazuh.com/current/installation-guide/wazuh-dashboard/step-by-step.html

Unistall dashboard: https://documentation.wazuh.com/current/installation-guide/uninstalling-wazuh/central-components.html#uninstall-dashboard