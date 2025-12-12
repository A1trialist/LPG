# LPG

This repository contains artifact of our USENIX Security'26 paper *LPG: Raise Your Location Privacy Game in Direct-to-Cell LEO Satellite Networks*.

LPG is a framework for protecting location privacy at the protocol level operating on an our academic satellite. 

The LEO satellite used in our experiments are not for commercial use, only for acadamic research. It replicates the satellite structure for COTS computing devices to minimize the impact of unrelated factors. Due to the double-blindness and licensing restrictions, we do not disclose all parameters, protocols and agreement contents of the satellite. We only make those contents that have no impact on the safety of satellite operation publicly available, and they can prove the conclusions and procedures of LPG. 

This repository provides artifacts about LPG, and it also could help the community understand how to conduct experiments on acadamic satellites.


## On-Board Satellite Experiment Procedures

In `./On-Board-Satellite-Procedures`, we discussed the basic procedures of on-board experiments, covering ground instruction making, experiment process generation, result acquisition, experiment execution and other aspects. 

Due to the lack of interactive shell access (e.g., SSH) in orbit, all procedures are executed via pre-scripted remote commands. This section contains:

**tcgen.sh:** The command-line utility used to convert human-readable shell commands into the hexadecimal packet format required by the satellite's On-Board Computer (OBC).

**Reconstruction_Workflow.md:** A detailed guide on the on-orbit software installation and update process.

**Onboard.md:** The general workflow for preparing, executing, and retrieving results from on-orbit experiments.



## Telemetry

In `./telemetry`, we provide the communication and measurement interface of the satellite payload. It contains:

**Telecommand_Protocol.md & Telemetry_Specification.md:** The formal specifications for the remote control and telemetry data packets, detailing every field and data type. These definitions correspond directly to the data collected in our evaluation.

**ReadPower.sh, ReadTemp.sh, etc.:** Shell scripts that interface with the onboard sensors to read real-time power and temperature data.

## Protocol Scripts

In `./scripts`, we provide the scripts for LPG and the baseline systems. 

`./scripts/satellite` contains the scripts that run on the satellite's ARM processor. This includes scripts for running the different components of LPG, LOCA, and other baseline protocols.(LOCA, PGPP, MOSAIC, SPACECORE)

`./scripts/phone` contains the client-side scripts that run on the UE phone. These scripts are used to drive the experiments, push necessary data, and benchmark performance.

The plot.ipynb file can generate all figures in section 5 of LPG paper.

## Evaluation Results

In `./Results`  we provide the datasets used in the LPG section 5 Evaluation. By comparing the timestamps of log and telemetry records, we can get the temperature and power metrics of the on-board implementation of certain protocols.


## Hardware Settings

Our in-orbit testbed consists of three main components:

**LEO Satellite:** our experiments are conducted on BUPT-3, a space science and technology demonstration satellite. It operates in a sun-synchronous orbit and is equipped with commodity servers (8-core ARM processors, 16 GB DDR4 RAM, 256 GB storage) as payload to support in-orbit computing tasks.

The detailed parameters of the BUPT-3 satellite are summarized below:

| Parameter                   | Value                                     |
|-----------------------------|-------------------------------------------|
| Name                        | BUPT-3 (TY46)                             |
| COSPAR ID                   | 2025-103F                                 |
| NORAD / SATCAT ID           | 64053                                     |
| Launch Vehicle              | Zhuque-2E                                 |
| Launch Date                 | 2025-05-17 04:12 UTC                      |
| Orbit Type                  | Sun-synchronous Orbit                     |
| Orbital Altitude            | ~509.6 km to ~514.3 km                    |
| Semi-major Axis             | ~6890 km                                  |
| Orbital Inclination         | 97.41°                                    |
| Eccentricity                | ~0.00034                                  |
| Argument of Perigee         | 183.5°                                    |
| Local Time of Ascending Node| 10:30 AM                                  |
| Orbital Period              | ~95 min                                   |
| Repeat Cycle                | ~12 days                                  |
| Mass                        | ~63 kg                                    |
| Mission Type                | Space science & technology demonstration  |
| Data Transmission           | 100 Mbps downlink; 1 Mbps uplink          |
| BSTAR (Drag Term)           | 0.00033725                                |
| Developer / Operator        | Spacety with BUPT                         |

**Ground Server:** A terrestrial server acting as the MNO, with an Intel Xeon Gold 6330 CPU and 256 GB of RAM.

**User Equipment (UE):** Two commodity phones, a Xiaomi 14 Ultra and a Google Pixel 9 Pro, used for end-to-end testing.


## References

[Anonymous tokens (AT)](https://github.com/google/anonymous-tokens)

[Scalable Collaborative ZK-snark](https://github.com/LBruyne/Scalable-Collaborative-zkSNARK)

[ZKLP](https://github.com/tumberger/zk-Location)

[ECIES](https://github.com/ecies)


