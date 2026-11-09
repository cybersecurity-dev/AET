<div align="center">
    <p align="center">
        <a href="https://developer.android.com/">
          <img width="35%" src="https://github.com/cybersecurity-dev/cybersecurity-dev/blob/main/assets/Android.svg" />
        </a>
    </p>

```mermaid
flowchart TB
    subgraph Sources["Android Event Sources"]
        direction LR
        APP["Application<br/>Activity"]
        PROC["Process and Thread<br/>Activity"]
        FILE["File-System<br/>Operations"]
        NET["Network<br/>Connections"]
        BINDER["Binder IPC<br/>Transactions"]
        PERM["Permission and API<br/>Access"]
        SENSOR["Sensor and Device<br/>Access"]
        AUTH["Authentication and<br/>User Activity"]
    end

    subgraph Instrumentation["Tracing and Instrumentation Layer"]
        direction LR
        LOGCAT["Logcat"]
        PERFETTO["Perfetto and<br/>Android Tracing"]
        EBPF["eBPF Programs"]
        TRACE["Kernel Tracepoints"]
        KPROBE["Kprobes and<br/>Uprobes"]
        AUDIT["Linux Audit<br/>Subsystem"]
        HOOKS["Framework and<br/>API Hooks"]
    end

    subgraph Collection["Event Collection Layer"]
        direction LR
        ADB["ADB Log and Trace<br/>Collector"]
        TRACED["Perfetto traced<br/>Service"]
        BUFFER["eBPF Ring Buffer"]
        AGENT["On-Device<br/>Monitoring Agent"]
        QUEUE["Event Buffer<br/>and Queue"]
    end

    subgraph Processing["Event Processing and Enrichment"]
        INGEST["Event Ingestion"]
        PARSE["Parsing and<br/>Schema Mapping"]
        NORMALIZE["Event Normalization"]
        ENRICH["Context Enrichment<br/>UID, PID, package, hash"]
        FILTER["Filtering and<br/>Aggregation"]
        CORRELATE["Cross-Event<br/>Correlation"]
        GRAPH["Behavior Graph<br/>Construction"]
    end

    subgraph Analysis["Malware Analysis and Detection"]
        RULES["Rule-Based<br/>Detection"]
        APIAN["Sensitive API<br/>Analysis"]
        BEHAVIOR["Behavioral<br/>Detection"]
        ML["Machine-Learning<br/>Model"]
        GNN["Graph-Based or<br/>GNN Analysis"]
        IOC["IOC and Signature<br/>Matching"]
        ATTACK["MITRE ATT&CK<br/>Mobile Mapping"]
        RISK["Application<br/>Risk Scoring"]
    end

    subgraph Storage["Storage Layer"]
        RAW[("Raw Trace Archive")]
        EVENTDB[("Normalized Event DB")]
        SEARCH[("Search Index")]
        GRAPHDB[("Behavior Graph DB")]
        APKDB[("APK Metadata DB")]
    end

    subgraph Response["Alerting and Response"]
        ALERT["Alert Generation"]
        INVEST["Application<br/>Investigation"]
        REPORT["Malware Analysis<br/>Report"]
        BLOCK["Block or Disable<br/>Application"]
        QUARANTINE["Quarantine APK"]
        FORENSICS["Preserve Forensic<br/>Evidence"]
    end

    subgraph Presentation["Access and Integration"]
        API["REST or gRPC API"]
        DASH["Security Dashboard"]
        TIMELINE["Event Timeline"]
        GRAPHVIEW["Behavior Graph<br/>Visualization"]
        SIEM["SIEM Integration"]
        MTD["Mobile Threat Defense<br/>Integration"]
    end

    APP --> LOGCAT
    APP --> HOOKS
    PROC --> PERFETTO
    PROC --> TRACE
    FILE --> TRACE
    FILE --> AUDIT
    NET --> EBPF
    NET --> AUDIT
    BINDER --> PERFETTO
    BINDER --> HOOKS
    PERM --> HOOKS
    SENSOR --> HOOKS
    AUTH --> LOGCAT
    AUTH --> AUDIT

    LOGCAT --> ADB
    PERFETTO --> TRACED
    TRACE --> TRACED
    EBPF --> BUFFER
    KPROBE --> BUFFER
    AUDIT --> AGENT
    HOOKS --> AGENT

    ADB --> QUEUE
    TRACED --> QUEUE
    BUFFER --> QUEUE
    AGENT --> QUEUE
    QUEUE --> INGEST

    INGEST --> PARSE
    PARSE --> NORMALIZE
    NORMALIZE --> ENRICH
    ENRICH --> FILTER
    FILTER --> CORRELATE
    CORRELATE --> GRAPH

    PARSE --> RAW
    ENRICH --> EVENTDB
    CORRELATE --> SEARCH
    GRAPH --> GRAPHDB
    ENRICH --> APKDB

    CORRELATE --> RULES
    CORRELATE --> APIAN
    CORRELATE --> BEHAVIOR
    CORRELATE --> IOC
    GRAPH --> ML
    GRAPH --> GNN

    RULES --> ATTACK
    APIAN --> ATTACK
    BEHAVIOR --> ATTACK
    ML --> ATTACK
    GNN --> ATTACK
    IOC --> ATTACK
    ATTACK --> RISK
    RISK --> ALERT

    ALERT --> INVEST
    INVEST --> REPORT
    ALERT --> BLOCK
    ALERT --> QUARANTINE
    ALERT --> FORENSICS

    RAW --> API
    EVENTDB --> API
    SEARCH --> API
    GRAPHDB --> API
    APKDB --> API
    ALERT --> API

    API --> DASH
    API --> TIMELINE
    API --> GRAPHVIEW
    API --> SIEM
    API --> MTD

    classDef source fill:#DBEAFE,stroke:#2563EB,color:#172554
    classDef trace fill:#EDE9FE,stroke:#7C3AED,color:#2E1065
    classDef collect fill:#D1FAE5,stroke:#059669,color:#064E3B
    classDef process fill:#FEF3C7,stroke:#D97706,color:#451A03
    classDef analysis fill:#FCE7F3,stroke:#DB2777,color:#500724
    classDef storage fill:#E0F2FE,stroke:#0284C7,color:#082F49
    classDef response fill:#FEE2E2,stroke:#DC2626,color:#450A0A
    classDef presentation fill:#F3E8FF,stroke:#9333EA,color:#3B0764

    class APP,PROC,FILE,NET,BINDER,PERM,SENSOR,AUTH source
    class LOGCAT,PERFETTO,EBPF,TRACE,KPROBE,AUDIT,HOOKS trace
    class ADB,TRACED,BUFFER,AGENT,QUEUE collect
    class INGEST,PARSE,NORMALIZE,ENRICH,FILTER,CORRELATE,GRAPH process
    class RULES,APIAN,BEHAVIOR,ML,GNN,IOC,ATTACK,RISK analysis
    class RAW,EVENTDB,SEARCH,GRAPHDB,APKDB storage
    class ALERT,INVEST,REPORT,BLOCK,QUARANTINE,FORENSICS response
    class API,DASH,TIMELINE,GRAPHVIEW,SIEM,MTD presentation
```

# **`AET`** | Event Tracing for Android
> AET is a tracing facility that allows a user to log events to a file (JSON, XML, CSV)
</div>

[![Android](https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)]()
[![YouTube](https://img.shields.io/badge/YouTube-%23FF0000.svg?style=for-the-badge&logo=YouTube&logoColor=white)]()
[![Reddit](https://img.shields.io/badge/Reddit-FF4500?style=for-the-badge&logo=reddit&logoColor=white)]()

<p align="center">
    <a href="https://github.com/cybersecurity-dev/"><img height="25" src="https://github.com/cybersecurity-dev/cybersecurity-dev/blob/main/assets/github.svg" alt="GitHub"></a>
    &nbsp;
    <a href="https://www.youtube.com/@CyberThreatDefence"><img height="25" src="https://github.com/cybersecurity-dev/cybersecurity-dev/blob/main/assets/youtube.svg" alt="YouTube"></a>
    &nbsp;
    <a href="https://cyberthreatdefence.com/my_awesome_lists"><img height="20" src="https://github.com/cybersecurity-dev/cybersecurity-dev/blob/main/assets/blog.svg" alt="My Awesome Lists"></a>
    <img src="https://github.com/cybersecurity-dev/cybersecurity-dev/blob/main/assets/bar.gif">
</p>

```mermaid
flowchart LR
    A["Android Device<br/>Apps, System Services, Kernel"]
    B["Event Collection<br/>Logcat, Perfetto, eBPF"]
    C["Event Processing<br/>Parse, Normalize, Filter"]
    D[("Event Storage")]
    E["Security Analysis<br/>and Dashboard"]
    F["Security Alerts"]

    A -->|Generate events| B
    B -->|Collect telemetry| C
    C -->|Store events| D
    D --> E
    C -->|Detect suspicious activity| F
    F --> E

    classDef source fill:#DBEAFE,stroke:#2563EB,color:#172554
    classDef collect fill:#EDE9FE,stroke:#7C3AED,color:#2E1065
    classDef process fill:#FEF3C7,stroke:#D97706,color:#451A03
    classDef storage fill:#DCFCE7,stroke:#16A34A,color:#052E16
    classDef output fill:#FEE2E2,stroke:#DC2626,color:#450A0A

    class A source
    class B collect
    class C process
    class D storage
    class E,F output
```

## 📖 Contents
- [My Awesome Lists](#my-awesome-lists)
- [Contributing](#contributing)
- [Contributors](#contributors)

## Installation Steps

<details>

<summary>Install required tools on Linux</summary>

### For Ubuntu 18.04, 20.04, 22.04

```bash
sudo apt-get update
```
</details>


<details>

<summary>Install required tools on Windows</summary>

### For Windows 11

```powershell
```
</details>


<details>

<summary>Install required python libs</summary>

### pip install
```script
pip install -r requirements.txt
python3 setup.py install
```

### conda install
```script
conda config --add channels conda-forge
conda install --file requirements_conda.txt
python3 setup.py install
```

</details>



## Common Android Kernel Event Types

| **Event Type**         | **Description**                                                              | **Subsystem / Use Case**               |
|------------------------|-------------------------------------------------------------------------------|----------------------------------------|
| `EV_KEY`               | Key/button pressed or released                                               | Input subsystem (`/dev/input`)         |
| `EV_REL`               | Relative axis movement (e.g., mouse movement, joystick)                      | Input subsystem                         |
| `EV_ABS`               | Absolute axis value change (e.g., touchscreen, accelerometer)                | Input subsystem                         |
| `EV_SYN`               | Synchronization event (marks end of a set of input events)                   | Input subsystem                         |
| `EV_MSC`               | Miscellaneous input events                                                    | Input subsystem                         |
| `EV_SW`                | Switch state changes (e.g., lid open/closed, headset inserted)               | Input subsystem                         |
| `EV_LED`               | LED status changes (caps lock, etc.)                                         | Input subsystem                         |
| `EV_SND`               | Sound output events (beep, bell)                                              | Input subsystem                         |
| `uevent`               | Kernel-generated device state change notification                            | Device manager (e.g., hotplug)          |
| `binder_transaction`   | IPC transaction event                                                        | Binder (Android IPC mechanism)          |
| `binder_transaction_fd`| IPC transaction with file descriptor                                         | Binder                                  |
| `binder_reply`         | Reply to a binder transaction                                                | Binder                                  |
| `binder_dead_binder`   | Notification that a binder node is no longer active                          | Binder                                  |
| `trace_sched_switch`   | Task context switch (scheduling trace event)                                 | Kernel tracing (ftrace)                 |
| `trace_sys_enter`      | System call entry                                                            | Tracing/debugging                       |
| `trace_sys_exit`       | System call exit                                                             | Tracing/debugging                       |
| `kprobe_event`         | Dynamic tracing via kernel probes                                            | Debugging/performance analysis          |
| `pm_wakeup`            | Power manager wakeup event                                                   | Power management                        |
| `thermal_event`        | Temperature threshold triggered (e.g., CPU/GPU thermal state)                | Thermal management                      |
| `battery_status_change`| Battery state change (e.g., charging/discharging)                            | Power subsystem                         |
| `ion_heap_shrink`      | Memory allocator (ION) event for memory shrink                               | Memory allocator (Android-specific)     |
| `vibrator_on/off`      | Vibration motor activation/deactivation                                      | Input/haptic feedback                   |

### My Awesome Lists
You can access the my awesome lists [here](https://cyberthreatdefence.com/my_awesome_lists)

### Contributing

[Contributions of any kind welcome, just follow the guidelines](contributing.md)!

### Contributors

[Thanks goes to these contributors](https://github.com/cybersecurity-dev/aet/graphs/contributors)!

[🔼 Back to top](#aet--event-tracing-for-android)
