# Cluster overview.

![cluster](_assets/cluster.jpg){: style="height:450px"}

### 🟣 Nodes.

| **Hostname** | **Model**   | **CPU**    | **Memory** | **Role** | **Operating System**    |
| ------------ | ----------- | ---------- | ---------- | -------- | ----------------------- |
| Pipboy       | RNUC11PAKI5 | i5-1135G7  | 16GB       | Master   | Ubuntu Server 22.04 LTS |
| Lighthouse   | NUC8i5BEK   | i5-8259U   | 16GB       | Master   | Ubuntu Server 22.04 LTS |
| Persephone   | NUC8i5BEK   | i5-8259U   | 16GB       | Master   | Ubuntu Server 22.04 LTS |
| Arcadia      | NUC8i5BEK   | i5-8259U   | 16GB       | Worker   | Ubuntu Server 22.04 LTS |
| Hephaestus   | NUC8i5BEK   | i5-8259U   | 16GB       | Worker   | Ubuntu Server 22.04 LTS |
| `Total`      |             | `20c/40t ` | `80GB`     |          |                         |

### 🌱 Environment.

| **Role**          | **Device**                  |
| ----------------- | --------------------------- |
| **Router**        | Mikrotik RB4011iGS.         |
| **NAS1**          | Helios64 by Kobol           |
| **NAS2**          | Synology DS918+             |
| **Access Points** | 2 x UAP-FlexHD Meshed       |
| **Cooling**       | AC Infinity AIRPLATE T8 PRO |

### ⚖️ Dependancy structure.

``` mermaid
graph TD
Apps --> Core
Apps --> Networking
Core --> Charts
Networking --> Charts
Charts --> Config
Charts --> CRDS
Charts --> Base

classDef fill fill:#12141c,stroke:#333,stroke-width:0px,color:#d4dafe
classDef zone fill:#0e0f16,stroke:#333,stroke-width:0px,color:#d4dafe
classDef zone2 fill:#09090f,stroke:#333,stroke-width:0px,color:#d4dafe
classDef outside fill:#0e0f16,stroke:#333,stroke-width:0px,color:#d4dafe
class Apps,Core,Networking,Charts,Config,CRDS,Base fill
class openshift zone
class service zone2
class client outside
```

```mermaid
flowchart LR

%% nodes ----------------------------------------------------------
client["client"]
load_balancer["load balancer"]
api1["API (replica 1)"]
api2["API (replica 2)"]
apin["API (replica N)"]

%% edges ----------------------------------------------------------
client --- load_balancer
subgraph openshift
    subgraph service
        api1 --- api2 --- apin
    end
    load_balancer --- service
end

%% style ----------------------------------------------------------
classDef fill fill:#12141c,stroke:#333,stroke-width:0px,color:#d4dafe
classDef zone fill:#0e0f16,stroke:#333,stroke-width:0px,color:#d4dafe
classDef zone2 fill:#09090f,stroke:#333,stroke-width:0px,color:#d4dafe
classDef outside fill:#0e0f16,stroke:#333,stroke-width:0px,color:#d4dafe
class api1,api2,apin,load_balancer fill
class openshift zone
class service zone2
class client outside
```
