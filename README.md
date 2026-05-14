# BLOCKFECS Proof-of-Concept Datasets

Hi! This repo shares the datasets from our BlockFECS proof-of-concept work. We hope it helps with similar research.

**BlockFECS: A Blockchain-Based Proof-of-Concept System for Metadata-Driven Evidence Correlation in Digital Forensics**

The data supports the evaluation of **BlockFECS**, a blockchain-backed digital forensic evidence management and metadata-driven evidence correlation system. The repository includes the proof-of-concept forensic metadata dataset, correlation correctness results, baseline performance results, scalability results, and concurrency test results.

> **Important note:** This dataset is intended for proof-of-concept evaluation. It is not a real criminal investigation dataset and should not be interpreted as containing real forensic evidence. Some forensic metadata fields were synthetically generated or adapted to simulate a smart city / Internet of Vehicles (IoV) accident investigation scenario.

---

## Repository Link

GitHub repository: <https://github.com/igsamoshoke/BLOCKFECS-POC-DATASET>

---

The dataset supports the experiments reported in the manuscript, including:

- correctness evaluation of the metadata-driven evidence correlation algorithm;
- baseline transaction latency and throughput testing;
- scalability testing across increasing batch sizes;
- concurrency testing across increasing request send rates; and
- summary statistics used in the manuscript tables and figures.

We adapted the dataset from the publicly available TON_IoT dataset, extending it with structured forensic metadata fields required for evidence correlation.

---

## Dataset Overview

The core dataset, `BlockFECS_dataset.csv`, contains 89 evidence metadata records representing heterogeneous digital evidence in a simulated smart city accident scenario. The metadata was structured to support evidence correlation using fields such as timestamp, geolocation, device ID, user ID, case ID, file type, file hash, and cloud storage placeholder IDs.

The experimental result files were generated from tests conducted across four system configurations:

| System | RAM | vCPUs | Disk |
|---|---:|---:|---:|
| System 1 | 4 GB | 2 | 30 GB |
| System 2 | 8 GB | 4 | 30 GB |
| System 3 | 16 GB | 8 | 30 GB |
| System 4 | 32 GB | 16 | 30 GB |

---

## Repository Contents

| File | Description |
|---|---|
| `BlockFECS_dataset.csv` | Main proof-of-concept forensic metadata dataset. Contains 89 evidence records with synthetic/adapted metadata used for evidence correlation. |
| `correctnessdataforanalysis.csv` | Summary correctness results for the evidence correlation algorithm, including Precision, Recall, and F1 Score by category. |
| `average_performance_by_system.csv` | Average baseline performance summary by system for Create, Transfer, Delete, and Correlate operations. |
| `performance_results_combined.csv` | Combined baseline performance results across all four systems and 30 trials per system. |
| `performance_results_system1.csv` | Baseline performance results for System 1. |
| `performance_results_system2.csv` | Baseline performance results for System 2. |
| `performance_results_system3.csv` | Baseline performance results for System 3. |
| `performance_results_system4.csv` | Baseline performance results for System 4. |
| `Combined_Scalability_Data.csv` | Combined scalability results across all systems and batch sizes. |
| `scalability_results_system1.csv` | Scalability results for System 1. |
| `scalability_results_system2.csv` | Scalability results for System 2. |
| `scalability_results_system3.csv` | Scalability results for System 3. |
| `scalability_results_system4.csv` | Scalability results for System 4. |
| `Combined_Concurrency_Results.csv` | Combined concurrency stress-test results across all four systems. |
| `concurrency_results_system1.csv` | Concurrency stress-test results for System 1. |
| `concurrency_results_system2.csv` | Concurrency stress-test results for System 2. |
| `concurrency_results_system3.csv` | Concurrency stress-test results for System 3. |
| `concurrency_results_system4.csv` | Concurrency stress-test results for System 4. |

---

## Main Evidence Metadata Fields

The main file, `BlockFECS_dataset.csv`, uses the following fields:

| Field | Description |
|---|---|
| `evidenceID` | Unique identifier assigned to each evidence item. |
| `title` | Non-analytical evidence title used for display and dataset readability. |
| `description` | Non-analytical evidence description used for display and dataset readability. |
| `timestamp` | Date and time associated with the evidence record. |
| `latitude` | Simulated or adapted latitude value used for location-based correlation. |
| `longitude` | Simulated or adapted longitude value used for location-based correlation. |
| `deviceId` | Identifier of the source device or sensor associated with the evidence. |
| `userId` | Logical user or witness identifier associated with the evidence, where available. |
| `caseId` | Investigation/case grouping identifier. |
| `fileType` | Evidence file type, such as image, video, sensor log, or other digital artefact type. |
| `fileHash` | SHA-256-style hash value used to support integrity checking and duplicate detection. |
| `googleDriveId` | Proof-of-concept placeholder for a cloud storage reference, not a functional Google Drive ID. For testing purposes only |

---

## The Experimental Result File Schemas

### Correctness Results

`correctnessdataforanalysis.csv`

| Field | Description |
|---|---|
| `Category` | Correlation class: Related, Supplementary, Duplicate, or Unrelated. |
| `Precision` | Precision score for the category. |
| `Recall` | Recall score for the category. |
| `F1 Score` | F1 Score for the category. |

### Baseline Performance Results

Files:

- `performance_results_combined.csv`
- `performance_results_system1.csv`
- `performance_results_system2.csv`
- `performance_results_system3.csv`
- `performance_results_system4.csv`
- `average_performance_by_system.csv`

Common fields include:

| Field | Description |
|---|---|
| `Trial` | Trial number for baseline performance testing. |
| `System` | Test system identifier, where present. |
| `CreateTime(s)` | Latency in seconds for the CreateEvidence operation. |
| `CreateTPS` | Throughput for the CreateEvidence operation. |
| `TransferTime(s)` | Latency in seconds for the TransferEvidence operation. |
| `TransferTPS` | Throughput for the TransferEvidence operation. |
| `DeleteTime(s)` | Latency in seconds for the DeleteEvidence operation. |
| `DeleteTPS` | Throughput for the DeleteEvidence operation. |
| `CorrelateTime(s)` | Latency in seconds for the evidence correlation operation. |
| `CorrelateTPS` | Throughput for the evidence correlation operation. |

### Scalability Results

Files:

- `Combined_Scalability_Data.csv`
- `scalability_results_system1.csv`
- `scalability_results_system2.csv`
- `scalability_results_system3.csv`
- `scalability_results_system4.csv`

Common fields include:

| Field | Description |
|---|---|
| `BatchSize` | Number of evidence records processed in the test batch. |
| `CreateTime(s)` | Total time in seconds for create operations at the specified batch size. |
| `TransferTime(s)` | Total time in seconds for transfer operations at the specified batch size. |
| `AvgCorrelationTime(s)` | Average evidence correlation time in seconds. |
| `TotalEvidenceInSystem` | Total number of evidence records in the system during the test. |
| `System` | Test system identifier, where present. |

### Concurrency Results

Files:

- `Combined_Concurrency_Results.csv`
- `concurrency_results_system1.csv`
- `concurrency_results_system2.csv`
- `concurrency_results_system3.csv`
- `concurrency_results_system4.csv`

Common fields include:

| Field | Description |
|---|---|
| `SendRate` | Number of concurrent or near-concurrent requests submitted during the stress test. |
| `AvgSuccess` | Average number of successful requests across trials. |
| `AvgFail` | Average number of failed requests across trials. |
| `AvgMinLatency(s)` | Average minimum latency in seconds. |
| `AvgMaxLatency(s)` | Average maximum latency in seconds. |
| `AvgLatency(s)` | Average latency in seconds. |
| `AvgThroughput(tps)` | Average throughput measured in transactions per second. |
| `System` | Test system identifier, where present. |

---

## Methodological Notes

We prepared this dataset for a simulated smart city / IoV forensic investigation scenario. We added synthetic forensic metadata because publicly available IoV forensic datasets with structured evidence-level metadata remain limited. Metadata fields such as title and description help with dataset readability and do not determine the experimental results. Our correlation algorithm evaluates evidence relationships using weighted metadata similarity across timestamp, location, device ID, user ID, and file hash. We treat exact file hash matches as duplicate evidence relationships. The dataset and results are suitable for reproducing our proof-of-concept evaluation reported in the manuscript, but they should not be treated as a real-world forensic benchmark.

---

## Data Availability Statement

The original data presented in this study are openly available in GitHub at <https://github.com/igsamoshoke/BLOCKFECS-POC-DATASET>. The repository contains the proof-of-concept forensic metadata datasets, correlation evaluation data, stress-test data, and experimental outputs used to support the findings reported in this study.

---

## Citation

If you use this dataset or refer to the BlockFECS proof-of-concept evaluation, please cite the associated manuscript: 

---

## License

This dataset is made available under the Creative Commons Attribution 4.0 International License (CC BY 4.0). Users may share and adapt the dataset, including for research and educational purposes, provided that appropriate credit is given to the authors and the associated manuscript is cited.
---

## Contact

Got questions about the dataset or the associated manuscript? We'd love to hear from you!

**Oshoke Samson Igonor**  
School of Information and Communication Technology  
University of Tasmania  
Email: oshoke.igonor@utas.edu.au
