# Real-World Predictive Maintenance Datasets List

## Overview

This repository curates a growing list of **publicly available,
real‑world predictive maintenance (PdM) datasets**. The goal is to
provide a single place where researchers and practitioners can quickly
identify datasets for anomaly detection, remaining‑useful‑life (RUL)
estimation and context‑aware maintenance modelling. Each dataset entry
consolidates information on sensor modalities, sampling cadence, size,
labelling strategy and licence to help you assess whether it suits your
needs. By focusing on datasets with contextual labels (maintenance
events, fault windows or operating regimes) we hope to encourage the
development of new methods.
## ⚡ TL;DR — Quick Overview of Datasets

- **[CWRU Bearing Data Center](https://engineering.case.edu/bearingdatacenter)**  
  - Classic bearing fault dataset with vibration signals (12–48 kHz).  
  - 4 sets covering normal and 3 fault types (inner, outer, ball).  
  - MATLAB files; well-documented and widely used.  
  - ✅ Labelled anomalies | ⚙️ Real data | 🧠 Moderate suitability for RNN-VAE.  

- **[Paderborn Bearing (KAt DataCenter)](https://mb.uni-paderborn.de/kat/forschung/kat-datacenter/bearing-datacenter/data-sets-and-download)**  
  - 32 bearing states under 4 conditions; real and artificial faults.  
  - Multi-sensor MAT files (current, vibration, torque, etc.).  
  - ✅ Labelled anomalies | ⚙️ Real data | 🧠 Moderate suitability for RNN-VAE.  

- **[Bearing Ring Grinder (SKF)](https://researchdata.se/en/catalogue/dataset/2022-136-1)**  
  - Multi-sensor TDMS dataset from industrial grinding process.  
  - 7 runs × 7 dressing cycles × 15 rings (~735 cycles).  
  - Rich vibration/acoustic data with failure classification.  
  - ✅ Labelled anomalies | ⚙️ Real data | 🧠 High suitability for RNN-VAE.  

- **[Hydropower Turbine Friction Monitoring](https://researchdata.se/en/catalogue/dataset/2025-35)**  
  - 2 turbines monitored via pressure & temperature (1 sample/min).  
  - CSV files with clear variable documentation.  
  - ⚠️ No anomaly labels | ⚙️ Real data | 🧠 Moderate (drift modeling).  

- **[IMAD-DS (Industrial Multi-Sensor Anomaly Detection)](https://zenodo.org/records/12665499)**  
  - Two machines (RoboticArm, BrushlessMotor) with domain shifts.  
  - Multi-rate audio and vibration sensors (Parquet + CSV).  
  - ✅ Train/test split | 🧠 High suitability for RNN-VAE.  
  - 🪪 CC BY-SA 4.0 | Excellent modern benchmark.  

- **[MetroPT-3 (UCI)](https://archive.ics.uci.edu/dataset/791/metropt+3+dataset)**  
  - 1.5 M samples, 15 features from metro propulsion systems.  
  - Failure logs allow anomaly labeling; ideal for long-sequence modeling.  
  - ✅ Labelled failures | ⚙️ Real data | 🧠 High suitability for RNN-VAE.  

- **[Microsoft Azure Predictive Maintenance](https://www.kaggle.com/datasets/arnabbiswas1/microsoft-azure-predictive-maintenance)**  
  - Large synthetic-style dataset (telemetry + logs + failures).  
  - 5 linked CSVs, suitable for supervised PdM tasks.  
  - ✅ Labelled anomalies | ⚙️ Realistic synthetic | 🧠 High suitability for RNN-VAE.  

- **[SCANIA Component X](https://researchdata.se/en/catalogue/dataset/2024-34)**  
  - High-dimensional truck telemetry dataset for failure prediction.  
  - 107 features + time-to-event and classification labels.  
  - ✅ Labelled failures | ⚙️ Real data | 🧠 High suitability for RNN-VAE.  

- **[Wind Turbine SCADA (CARE to Compare)](https://zenodo.org/records/15846963)**  
  - 95 turbine datasets (44 anomalous, 51 normal).  
  - 86 – 957 features, 10-min resolution, 1 year of training each.  
  - ✅ Labelled anomalies | ⚙️ Real data | 🧠 High suitability for RNN-VAE.  


---

### ⚠️ Disclaimer  
This document was prepared with the assistance of **OpenAI’s GPT-5** model.  
While the content has been carefully reviewed, it may contain **minor inaccuracies or omissions** due to the automated generation process.  
Please **verify critical dataset details** (e.g., licensing terms, sample rates, and feature definitions) before using them in research or production.

---
## Dataset summary

Below you will find detailed descriptions of each dataset, including
information on labelling, file formats, availability of pre‑defined
training/testing splits and suitability for recurrent VAE methods. Where
possible we provide citations to original papers or dataset
descriptions.

### CWRU Bearing Data Center

**Domain & sensors:** The Case Western Reserve University (CWRU) dataset
contains high‑frequency vibration signals acquired on a laboratory test
rig equipped with a 2 hp induction motor and rolling bearings.
Single‑point faults of various sizes were introduced on the inner race,
outer race and ball using electro‑discharge machining, while a baseline
set of healthy bearings was also
recorded[\[1\]](https://arxiv.org/html/2407.14625v1#:~:text=The%20CWRU%20bearing%20fault%20dataset,world%20scenarios).
Acceleration signals were measured at the drive end, fan end and bearing
base at 12--48 kHz and the motor speed (rpm) was logged.

**Context labels:** Each file corresponds to a specific bearing
condition (healthy or a particular fault type and size). There are no
explicit maintenance events or run‑to‑failure sequences; users must
treat the fault labels as
anomalies[\[1\]](https://arxiv.org/html/2407.14625v1#:~:text=The%20CWRU%20bearing%20fault%20dataset,world%20scenarios).

**Short description & characteristics:**

-   **Run‑to‑failure:** No -- samples are short bursts with seeded
    faults.
-   **Ease of use:** Moderate; data are provided in MATLAB (.mat) files
    at high sampling rates, requiring resampling or feature extraction.
-   **File format:** MATLAB (.mat).
-   **Has description:** Yes -- the dataset page and many papers
    describe sampling rates and experimental
    setup[\[1\]](https://arxiv.org/html/2407.14625v1#:~:text=The%20CWRU%20bearing%20fault%20dataset,world%20scenarios).
-   **Number of datasets:** Four sets (normal baseline and three fault
    types) at multiple motor loads.
-   **Rows:** Varies -- each file contains 4--10 s of vibration and
    speed data.
-   **Columns:** 2--3 sensors (drive‑end, fan‑end, base) plus rpm.
-   **Labelled events:** No -- only fault vs normal classification.
-   **Labelled anomalies:** Yes -- each file is labelled by fault type
    and size.
-   **Labelled components:** Yes -- faults are labelled by location
    (inner race, outer race, ball). The motor itself is not anonymised.
-   **Separate train/test:** No -- users typically split data manually;
    however, caution is needed to avoid leakage because the same bearing
    appears under different
    loads[\[2\]](https://arxiv.org/html/2407.14625v1#:~:text=The%20CWRU%20bearing%20fault%20dataset,world%20scenarios).
-   **Data type:** Real.
-   **Literature:** Numerous publications; see e.g. the dataset
    description[\[2\]](https://arxiv.org/html/2407.14625v1#:~:text=The%20CWRU%20bearing%20fault%20dataset,world%20scenarios).
-   **GitHub examples:** Many open‑source examples of bearing fault
    diagnosis using this dataset.
-   **Suitability for RNN‑VAE:** Moderate -- short, high‑frequency
    segments are well suited for classification but offer limited
    temporal context.
-   **License:** Not explicitly stated (research use only).
-   **Version:** N/A.
-   **Dataset link:** <https://engineering.case.edu/bearingdatacenter>.

### Paderborn Bearing (KAt DataCenter)

**Domain & sensors:** This dataset from the Paderborn University
KAt DataCenter contains vibration and current measurements of rolling
bearings under various conditions. It includes healthy bearings,
artificially damaged bearings (single point faults) and bearings with
accelerated life‑induced failures. Sensors measure motor current,
vibration, rotational speed and torque; some versions include additional
load
parameters[\[3\]](https://mb.uni-paderborn.de/kat/forschung/kat-datacenter/bearing-datacenter/data-sets-and-download#:~:text=The%20main%20characteristic%20of%20the,data%20set%20are).

**Context labels:** Each measurement is associated with a specific
bearing state (e.g. healthy, inner race fault, outer race fault, ball
fault). There are no run‑to‑failure sequences or maintenance events; the
labels are categorical damage classes.

**Short description & characteristics:**

-   **Run‑to‑failure:** No -- data are collected as 4‑s segments for
    each bearing state.
-   **Ease of use:** Moderate; multiple MATLAB (.mat) files with fact
    sheets describing the states and measurement conditions.
-   **File format:** MATLAB (.mat).
-   **Has description:** Yes -- the KAt DataCenter provides detailed
    descriptions of states, sensors and measurement
    numbers[\[3\]](https://mb.uni-paderborn.de/kat/forschung/kat-datacenter/bearing-datacenter/data-sets-and-download#:~:text=The%20main%20characteristic%20of%20the,data%20set%20are).
-   **Number of datasets:** 32 bearing states comprising 6 healthy
    bearings and 26 faulty bearings (12 artificial and 14 natural
    faults).
-   **Rows:** Varies -- each measurement is a 4‑s high‑rate recording.
-   **Columns:** Motor current, vibration, speed, torque and torque
    variation signals.
-   **Labelled events:** No -- only damage class labels.
-   **Labelled anomalies:** Yes -- normal vs fault labels.
-   **Labelled components:** Yes -- bearing states are identifiable and
    not anonymised.
-   **Separate train/test:** No -- the user must create splits.
-   **Data type:** Real.
-   **Literature:** Data described in KAt DataCenter documentation and
    numerous Paderborn publications.
-   **GitHub examples:** Multiple open‑source fault diagnosis examples
    exist.
-   **Suitability for RNN‑VAE:** Moderate -- multiple sensors provide a
    multivariate signal, but segments are short and lack context.
-   **License:** Unknown (available for academic use).
-   **Version:** N/A.
-   **Dataset link:**
    <https://mb.uni-paderborn.de/kat/forschung/kat-datacenter/bearing-datacenter/data-sets-and-download>.

### Bearing Ring Grinder (SKF)

**Domain & sensors:** This dataset from SKF documents a real industrial
bearing‑ring grinding process. During seven test runs and seven dressing
cycles on a production grinding machine, multiple sensor channels were
recorded, including vibration, acoustic emission, grinding force and
temperature[\[4\]](https://researchdata.se/en/catalogue/dataset/2022-136-1).
Additional meta‑data describe the set‑up (wheel dressing, ring ID) and
quality parameters of the finished rings.

**Context labels:** Each ring is labelled with its failure mode or
quality class; process variables (e.g. dressing cycles) act as
contextual events. This allows the user to study how new set‑ups change
the normal operating regime.

**Short description & characteristics:**

-   **Run‑to‑failure:** No -- data represent quality monitoring rather
    than run‑to‑failure experiments.
-   **Ease of use:** Complex -- sensor data are stored in National
    Instruments TDMS files and accompanied by CSV and PDF documentation.
    Dedicated libraries (e.g. `nptdms`) are required to extract
    time‑series
    signals[\[4\]](https://researchdata.se/en/catalogue/dataset/2022-136-1).
-   **File format:** TDMS, CSV and
    PDF[\[4\]](https://researchdata.se/en/catalogue/dataset/2022-136-1).
-   **Has description:** Yes -- `readme_data_description.pdf` and
    associated documentation explain sensors, test runs and quality
    parameters[\[4\]](https://researchdata.se/en/catalogue/dataset/2022-136-1).
-   **Number of datasets:** Approximately seven test runs × seven
    dressing cycles × 15 rings (\~735 rings).
-   **Rows:** Not specified -- continuous raw time‑series are provided.
-   **Columns:** Multiple analogue (vibration, acoustic emission, force,
    temperature) and digital channels.
-   **Labelled events:** Yes -- meta‑data include quality parameters and
    process data (setup/dress cycles).
-   **Labelled anomalies:** Yes -- rings are classified by failure mode
    or quality class.
-   **Labelled components:** Yes -- sensor channels and ring identifiers
    are not anonymised.
-   **Separate train/test:** No -- users must define their own splits.
-   **Data type:** Real.
-   **Literature:** See Ahmer et al., 2022 (International Journal of
    Advanced Manufacturing Technology) and associated SKF publications.
-   **GitHub examples:** Only a few examples exist due to the TDMS
    format.
-   **Suitability for RNN‑VAE:** High -- long, multi‑sensor sequences
    with varying operating regimes and quality labels provide a rich
    testbed for continual adaptation.
-   **License:**
    CC BY 4.0[\[5\]](https://researchdata.se/en/catalogue/dataset/2022-136-1#:~:text=).
-   **Version:** N/A.
-   **Dataset link:**
    <https://researchdata.se/en/catalogue/dataset/2022-136-1>.

### Hydropower Turbine Friction Monitoring

**Domain & sensors:** This dataset collects hydraulic monitoring data
from two Kaplan turbines at a hydropower plant. Each CSV file logs
pressure and temperature statistics (mean, minimum and median) at
1‑minute intervals and includes a binary flag indicating whether
glycerol (lubricant) is
present[\[6\]](https://researchdata.se/en/catalogue/dataset/2025-35#:~:text=The%20datasets%20contain%20pressure%20and,than%201%20sample%20per%20minute).

**Context labels:** The glycerol flag acts as a context label,
distinguishing periods when lubrication is present or absent. There are
no explicit fault labels; rather, the data are intended for detecting
changes in friction behaviour across these regimes.

**Short description & characteristics:**

-   **Run‑to‑failure:** No.
-   **Ease of use:** Easy -- two CSV files with self‑explaining column
    names and a
    README[\[6\]](https://researchdata.se/en/catalogue/dataset/2025-35#:~:text=The%20datasets%20contain%20pressure%20and,than%201%20sample%20per%20minute).
-   **File format:** CSV.
-   **Has description:** Yes -- the dataset page explains all variables
    and the lubrication
    context[\[6\]](https://researchdata.se/en/catalogue/dataset/2025-35#:~:text=The%20datasets%20contain%20pressure%20and,than%201%20sample%20per%20minute).
-   **Number of datasets:** Two (Turbine 1 and Turbine 2).
-   **Rows:** Not specified -- 1‑minute sampling over the monitoring
    period (several months).
-   **Columns:** Pressure and temperature variables (mean, min, median)
    and the glycerol flag.
-   **Labelled events:** Yes -- lubrication flag provides a context
    event.
-   **Labelled anomalies:** No -- there are no failure labels.
-   **Labelled components:** Yes -- variables correspond to specific
    hydraulic components.
-   **Separate train/test:** No.
-   **Data type:** Real.
-   **Literature:** Sandström et al., 2025.
-   **GitHub examples:** Limited.
-   **Suitability for RNN‑VAE:** Moderate -- low‑frequency time series
    are useful for studying gradual drift and changing regimes.
-   **License:**
    CC BY 4.0[\[7\]](https://researchdata.se/en/catalogue/dataset/2025-35#:~:text=License%3A).
-   **Version:**
    1[\[7\]](https://researchdata.se/en/catalogue/dataset/2025-35#:~:text=License%3A).
-   **Dataset link:**
    <https://researchdata.se/en/catalogue/dataset/2025-35>.

### IMAD‑DS (Industrial Multi‑Sensor Anomaly Detection)

**Domain & sensors:** IMAD‑DS provides multi‑rate sensor recordings from
two scaled test benches: a robotic arm and a brushless DC motor. Each
segment contains an analogue audio signal, a three‑axis accelerometer
and a three‑axis gyroscope. Data are sampled at different rates and
stored as Parquet files accompanied by metadata
CSVs[\[8\]](https://zenodo.org/records/12665499#:~:text=Description).

**Context labels:** Metadata indicate the operating condition (normal vs
anomalous), fault mechanism (e.g. removing bolts, adding magnets or
tightening belts) and environmental noise conditions. This allows
domain‑shift evaluation across operating speeds and noise
levels[\[9\]](https://zenodo.org/records/12665499#:~:text=Data%20is%20collected%20using%20the,the%20dataset%20are%20the%20following).

**Short description & characteristics:**

-   **Run‑to‑failure:** No -- anomalies are injected artificially.
-   **Ease of use:** Moderate -- data are packaged in `.7z` archives;
    the sensor streams are stored in Parquet with separate metadata
    CSVs[\[10\]](https://zenodo.org/records/12665499#:~:text=Data%20Format%3A%20Files%20are%20already,parquet%27%20file).
-   **File format:** Parquet (sensor data) and CSV (metadata).
-   **Has description:** Yes -- the Zenodo page and the DCASE 2024 paper
    describe machines, sensors and anomaly
    types[\[8\]](https://zenodo.org/records/12665499#:~:text=Description).
-   **Number of datasets:** Two machines with separate normal and
    anomalous segments.
-   **Rows:** Not specified -- each segment has a variable length.
-   **Columns:** 7 sensor streams (1 microphone + 3 accelerometer + 3
    gyroscope axes).
-   **Labelled events:** Yes -- metadata provide context (operating
    speed, environment, etc.).
-   **Labelled anomalies:** Yes -- anomalies introduced by bolt removal,
    magnet addition or belt
    tightening[\[9\]](https://zenodo.org/records/12665499#:~:text=Data%20is%20collected%20using%20the,the%20dataset%20are%20the%20following).
-   **Labelled components:** Yes -- machine type and segment conditions
    are explicit in the metadata.
-   **Separate train/test:** Yes -- files are divided into training and
    testing
    sets[\[10\]](https://zenodo.org/records/12665499#:~:text=Data%20Format%3A%20Files%20are%20already,parquet%27%20file).
-   **Data type:** Real.
-   **Literature:** Albertini et al., "IMAD‑DS: Industrial Multi‑Sensor
    Anomaly Detection under Domain Shift" (DCASE 2024).
-   **GitHub examples:** The authors provide a baseline repository.
-   **Suitability for RNN‑VAE:** High -- multi‑rate, multi‑sensor data
    with domain shifts test robustness and latent modelling.
-   **License:**
    CC BY‑SA 4.0[\[11\]](https://zenodo.org/records/12665499#:~:text=License).
-   **Version:**
    v2[\[11\]](https://zenodo.org/records/12665499#:~:text=License).
-   **Dataset link:** <https://zenodo.org/records/12665499>.

### MetroPT‑3 (UCI)

**Domain & sensors:** MetroPT‑3 is a multivariate time series collected
from a sewerage‑treatment‑plant compressor system. It comprises seven
analogue sensors (e.g. pressures, temperatures, currents) and eight
digital signals capturing valve states and
alarms[\[12\]](https://archive.ics.uci.edu/dataset/791/metropt%203%20dataset).

**Context labels:** Maintenance reports were used to derive ground‑truth
failure windows. The dataset includes timestamps for the start and end
of three catastrophic failures (two air leaks and one oil leak), so you
can analyse how measurements drift before and after
maintenance[\[13\]](https://archive.ics.uci.edu/dataset/791/metropt%203%20dataset#:~:text=Data%20Set%20Information%3A%20The%20dataset,You%20can).

**Short description & characteristics:**

-   **Run‑to‑failure:** No -- failure events exist, but the system
    continues operation; the data are not full run‑to‑failure sequences.
-   **Ease of use:** Easy -- provided as a single CSV file with
    1 516 948 instances across 15
    features[\[12\]](https://archive.ics.uci.edu/dataset/791/metropt%203%20dataset).
-   **File format:** CSV.
-   **Has description:** Yes -- the UCI repository includes feature
    descriptions and recommended train/test
    splits[\[13\]](https://archive.ics.uci.edu/dataset/791/metropt%203%20dataset#:~:text=Data%20Set%20Information%3A%20The%20dataset,You%20can).
-   **Number of datasets:** One.
-   **Rows:** 1 516 948.
-   **Columns:** 15 features (seven analogue & eight digital sensors).
-   **Labelled events:** Yes -- ground‑truth failure windows derived
    from maintenance
    reports[\[13\]](https://archive.ics.uci.edu/dataset/791/metropt%203%20dataset#:~:text=Data%20Set%20Information%3A%20The%20dataset,You%20can).
-   **Labelled anomalies:** Partially -- the raw CSV does not include
    anomaly labels, but the failure windows can be treated as anomalies.
-   **Labelled components:** Yes -- sensors correspond to physical
    components (compressor pressure, current, oil temperature, etc.).
-   **Separate train/test:** Recommended -- the accompanying paper
    suggests using the first month for training and the remainder for
    evaluation[\[14\]](https://archive.ics.uci.edu/dataset/791/metropt%203%20dataset#:~:text=Are%20there%20recommended%20data%20splits%3F).
-   **Data type:** Real.
-   **Literature:** Davari et al., 2021; UCI dataset
    documentation[\[12\]](https://archive.ics.uci.edu/dataset/791/metropt%203%20dataset).
-   **GitHub examples:** Several examples exist using the UCI ML
    repository.
-   **Suitability for RNN‑VAE:** High -- long, labelled multivariate
    sequences with maintenance events are ideal for continual anomaly
    detection.
-   **License:**
    CC BY 4.0[\[15\]](https://archive.ics.uci.edu/dataset/791/metropt%203%20dataset#:~:text=License).
-   **Version:**
    MetroPT‑3[\[15\]](https://archive.ics.uci.edu/dataset/791/metropt%203%20dataset#:~:text=License).
-   **Dataset link:**
    <https://archive.ics.uci.edu/dataset/791/metropt+3+dataset>.

### Microsoft Azure Predictive Maintenance

**Domain & sensors:** Microsoft's Azure sample dataset (also known as
AI4I 2020 or PdM) simulates a small fleet of machines sending hourly
telemetry streams containing voltage, rotation speed, pressure and
vibration readings. Separate files log error codes, maintenance
operations and component
failures[\[16\]](https://www.mdpi.com/2076-3417/11/1/18#:~:text=The%20data%20were%20acquired%20over,records%20for%20the%20year%202014).

**Context labels:** The maintenance log records the date of each
scheduled service; the error log lists error codes (five types) and the
failure log lists the component that failed (four
components)[\[17\]](https://www.mdpi.com/2076-3417/11/1/18#:~:text=The%20second%20source%20of%20information,type%20over%20the%20year%202015).

**Short description & characteristics:**

-   **Run‑to‑failure:** No -- the dataset is synthetic and covers one
    year of operation with eight failures per
    machine[\[16\]](https://www.mdpi.com/2076-3417/11/1/18#:~:text=The%20data%20were%20acquired%20over,records%20for%20the%20year%202014).
-   **Ease of use:** Moderate -- data are provided in multiple CSV files
    (telemetry, errors, failures, maintenance and machine description).
-   **File format:** CSV.
-   **Has description:** Yes -- the MEDEP article and the Microsoft
    documentation describe each file and its
    columns[\[16\]](https://www.mdpi.com/2076-3417/11/1/18#:~:text=The%20data%20were%20acquired%20over,records%20for%20the%20year%202014).
-   **Number of datasets:** Five files (telemetry, errors, failures,
    maintenance, machine
    features)[\[17\]](https://www.mdpi.com/2076-3417/11/1/18#:~:text=The%20second%20source%20of%20information,type%20over%20the%20year%202015).
-   **Rows:** Telemetry: 876 100 records; Errors: 3 919; Maintenance:
    3 286; Failures:
    761[\[17\]](https://www.mdpi.com/2076-3417/11/1/18#:~:text=The%20second%20source%20of%20information,type%20over%20the%20year%202015).
-   **Columns:** Telemetry includes datetime, machine ID and four sensor
    variables (voltage, rotation, pressure, vibration); other files
    include categorical
    codes[\[17\]](https://www.mdpi.com/2076-3417/11/1/18#:~:text=The%20second%20source%20of%20information,type%20over%20the%20year%202015).
-   **Labelled events:** Yes -- maintenance and error logs can be
    interpreted as
    events[\[17\]](https://www.mdpi.com/2076-3417/11/1/18#:~:text=The%20second%20source%20of%20information,type%20over%20the%20year%202015).
-   **Labelled anomalies:** Yes -- the failure file provides anomaly
    labels[\[17\]](https://www.mdpi.com/2076-3417/11/1/18#:~:text=The%20second%20source%20of%20information,type%20over%20the%20year%202015).
-   **Labelled components:** Yes -- four components are named
    (comp1--comp4).
-   **Separate train/test:** No -- users define splits.
-   **Data type:** Real (synthetic simulation).
-   **Literature:** The MEDEP paper ("Maintenance Event Detection for
    Multivariate Time Series Based on the PELT Approach") analyses this
    dataset[\[16\]](https://www.mdpi.com/2076-3417/11/1/18#:~:text=The%20data%20were%20acquired%20over,records%20for%20the%20year%202014).
-   **GitHub examples:** Numerous notebooks on Kaggle and GitHub.
-   **Suitability for RNN‑VAE:** High -- multivariate time series with
    maintenance logs and failures are suitable for supervised and
    unsupervised PdM experiments.
-   **License:** Not explicitly stated (public Kaggle dataset).
-   **Version:** N/A.
-   **Dataset link:**
    <https://www.kaggle.com/datasets/arnabbiswas1/microsoft-azure-predictive-maintenance>.

### SCANIA Component X

**Domain & sensors:** The SCANIA Component X dataset comprises
high‑dimensional operational data from a fleet of vehicles. Each
observation contains 107 histogram/counter features reflecting various
engine and vehicle operating conditions along with a label indicating
the remaining time to failure in
classes[\[18\]](https://researchdata.se/en/catalogue/dataset/2024-34#:~:text=This%20data%20is%20a%20real,The%20objective%20of).

**Context labels:** Validation and test sets use a five‑class label
representing the time window before failure: \>48 hours, 48--24 hours,
24--12 hours, 12--6 hours and
6--0 hours[\[19\]](https://researchdata.se/en/catalogue/dataset/2024-34#:~:text=).

**Short description & characteristics:**

-   **Run‑to‑failure:** No -- data are labelled by proximity to failure
    rather than full run‑to‑failure trajectories.
-   **Ease of use:** Moderate -- multiple CSV files (train, validation
    and test) with large file sizes (train \~1.1 GB; validation/test
    \~205 MB).
-   **File format:** CSV.
-   **Has description:** Yes -- the dataset description explains the
    features and label
    scheme[\[19\]](https://researchdata.se/en/catalogue/dataset/2024-34#:~:text=).
-   **Number of datasets:** Three splits: train, validation and
    test[\[19\]](https://researchdata.se/en/catalogue/dataset/2024-34#:~:text=).
-   **Rows:** Not specified; training file is \~1.1 GB.
-   **Columns:** 107 features (histograms and counters) plus
    specification
    meta‑data[\[18\]](https://researchdata.se/en/catalogue/dataset/2024-34#:~:text=This%20data%20is%20a%20real,The%20objective%20of).
-   **Labelled events:** Yes -- validation/test labels indicate the time
    window before
    failure[\[19\]](https://researchdata.se/en/catalogue/dataset/2024-34#:~:text=).
-   **Labelled anomalies:** Yes -- classes represent proximity to
    failure.
-   **Labelled components:** The component itself is anonymised
    (Component X); individual sensors and measurements are not named.
-   **Separate train/test:** Yes -- train/validation/test splits are
    provided[\[19\]](https://researchdata.se/en/catalogue/dataset/2024-34#:~:text=).
-   **Data type:** Real.
-   **Literature:** "An annotated dataset for predictive maintenance of
    truck components" and associated arXiv
    paper[\[18\]](https://researchdata.se/en/catalogue/dataset/2024-34#:~:text=This%20data%20is%20a%20real,The%20objective%20of).
-   **GitHub examples:** Several notebooks and competitions use this
    dataset.
-   **Suitability for RNN‑VAE:** High -- the high dimensionality and
    time‑to‑event labels support sequence modelling and survival
    analysis.
-   **License:**
    CC BY 4.0[\[20\]](https://researchdata.se/en/catalogue/dataset/2024-34#:~:text=).
-   **Version:**
    Version 3[\[20\]](https://researchdata.se/en/catalogue/dataset/2024-34#:~:text=).
-   **Dataset link:**
    <https://researchdata.se/en/catalogue/dataset/2024-34>.

### Wind Turbine SCADA (CARE to Compare)

**Domain & sensors:** CARE to Compare is a large collection of wind
turbine supervisory control and data acquisition (SCADA) datasets used
for anomaly detection research. It contains SCADA measurements from 36
turbines in three farms, spanning 89 years of operating data and
released as 95 sub‑datasets. Each dataset comprises one year of training
data and 4--98 days of prediction data with 10‑minute sampling. The
number of features differs by farm: 86 for farm A, 257 for farm B and
957 for
farm C[\[21\]](https://www.mdpi.com/2306-5729/9/12/138#:~:text=The%20data%20consist%20of%2095,points%20of%20the%20time%20series)[\[22\]](https://www.mdpi.com/2306-5729/9/12/138#:~:text=The%20number%20of%20features%20in,indicating%20the%20turbine%20status%20at).

**Context labels:** Each dataset is labelled as either normal or
containing an anomaly event. Within each dataset, a `status_id`
identifies turbine operating modes (normal, service mode, fault, etc.),
and anomaly windows are defined based on logbooks and service
reports[\[23\]](https://www.mdpi.com/2306-5729/9/12/138#:~:text=The%20data%20are%20labeled%20on,the%20data%2C%20and%20expert%20knowledge).

**Short description & characteristics:**

-   **Run‑to‑failure:** No -- the datasets capture operating periods
    before and after fault events rather than complete run‑to‑failure
    histories.
-   **Ease of use:** Moderate -- 95 CSV files with high‑dimensional
    features; requires careful pre‑processing to align features across
    farms[\[22\]](https://www.mdpi.com/2306-5729/9/12/138#:~:text=The%20number%20of%20features%20in,indicating%20the%20turbine%20status%20at).
-   **File format:** CSV.
-   **Has description:** Yes -- the Fraunhofer IEE report and Kaggle
    data card describe data structure and anomaly
    windows[\[23\]](https://www.mdpi.com/2306-5729/9/12/138#:~:text=The%20data%20are%20labeled%20on,the%20data%2C%20and%20expert%20knowledge).
-   **Number of datasets:** 95 (44 with anomaly events, 51 normal).
-   **Rows:** Each dataset contains 1 year of training data plus
    4--98 days of prediction data at 10‑minute resolution (≈52 560
    training rows).
-   **Columns:** 86--957 features depending on the wind
    farm[\[22\]](https://www.mdpi.com/2306-5729/9/12/138#:~:text=The%20number%20of%20features%20in,indicating%20the%20turbine%20status%20at).
-   **Labelled events:** Yes -- datasets are labelled as containing an
    anomaly or not; `status_id` labels individual
    timestamps[\[23\]](https://www.mdpi.com/2306-5729/9/12/138#:~:text=The%20data%20are%20labeled%20on,the%20data%2C%20and%20expert%20knowledge).
-   **Labelled anomalies:** Yes -- anomaly windows derived from logbooks
    serve as anomaly
    labels[\[23\]](https://www.mdpi.com/2306-5729/9/12/138#:~:text=The%20data%20are%20labeled%20on,the%20data%2C%20and%20expert%20knowledge).
-   **Labelled components:** Partially -- sensor names are anonymised in
    some farms; power and energy signals are identifiable.
-   **Separate train/test:** Yes -- a `train_test` column specifies
    training and prediction
    periods[\[23\]](https://www.mdpi.com/2306-5729/9/12/138#:~:text=The%20data%20are%20labeled%20on,the%20data%2C%20and%20expert%20knowledge).
-   **Data type:** Real.
-   **Literature:** Fraunhofer IEE "CARE to Compare" report and
    associated Kaggle
    documentation[\[23\]](https://www.mdpi.com/2306-5729/9/12/138#:~:text=The%20data%20are%20labeled%20on,the%20data%2C%20and%20expert%20knowledge).
-   **GitHub examples:** Some code notebooks are available via Kaggle.
-   **Suitability for RNN‑VAE:** High -- long, multivariate time series
    with labelled anomaly windows support early fault detection and
    continual learning.
-   **License:** CC BY‑SA 4.0 (Kaggle
    re‑upload)[\[24\]](https://www.kaggle.com/datasets/azizkasimov/wind-turbine-scada-data-for-early-fault-detection).
-   **Version:**
    Version 6[\[24\]](https://www.kaggle.com/datasets/azizkasimov/wind-turbine-scada-data-for-early-fault-detection).
-   **Dataset link:** <https://zenodo.org/records/15846963>.

## Contributing

This list is maintained as a community resource. If you know of other
open PdM datasets or notice an error, feel free to open an issue or
submit a pull request. When adding a new dataset, please include as much
detail as possible: domain, sensor modalities, sampling rate, labelling
scheme, file formats, licence and a link to the official download page.

[\[1\]](https://arxiv.org/html/2407.14625v1#:~:text=The%20CWRU%20bearing%20fault%20dataset,world%20scenarios)
[\[2\]](https://arxiv.org/html/2407.14625v1#:~:text=The%20CWRU%20bearing%20fault%20dataset,world%20scenarios)
Benchmarking deep learning models for bearing fault diagnosis using the
CWRU dataset: A multi-label approach

<https://arxiv.org/html/2407.14625v1>

[\[3\]](https://mb.uni-paderborn.de/kat/forschung/kat-datacenter/bearing-datacenter/data-sets-and-download#:~:text=The%20main%20characteristic%20of%20the,data%20set%20are)
Data Sets and Download - Konstruktions- und Antriebstechnik (KAt) \|
Universität Paderborn

<https://mb.uni-paderborn.de/kat/forschung/kat-datacenter/bearing-datacenter/data-sets-and-download>

[\[4\]](https://researchdata.se/en/catalogue/dataset/2022-136-1)
[\[5\]](https://researchdata.se/en/catalogue/dataset/2022-136-1#:~:text=)
Dataset Concerning the Process Monitoring and Condition Monitoring Data
of a Bearing Ring Grinder

<https://researchdata.se/en/catalogue/dataset/2022-136-1>

[\[6\]](https://researchdata.se/en/catalogue/dataset/2025-35#:~:text=The%20datasets%20contain%20pressure%20and,than%201%20sample%20per%20minute)
[\[7\]](https://researchdata.se/en/catalogue/dataset/2025-35#:~:text=License%3A)
Hydropower Turbine Friction Monitoring Dataset

<https://researchdata.se/en/catalogue/dataset/2025-35>

[\[8\]](https://zenodo.org/records/12665499#:~:text=Description)
[\[9\]](https://zenodo.org/records/12665499#:~:text=Data%20is%20collected%20using%20the,the%20dataset%20are%20the%20following)
[\[10\]](https://zenodo.org/records/12665499#:~:text=Data%20Format%3A%20Files%20are%20already,parquet%27%20file)
[\[11\]](https://zenodo.org/records/12665499#:~:text=License) IMAD-DS: A
Dataset for Industrial Multi-Sensor Anomaly Detection Under Domain Shift
Conditions

<https://zenodo.org/records/12665499>

[\[12\]](https://archive.ics.uci.edu/dataset/791/metropt%203%20dataset)
[\[13\]](https://archive.ics.uci.edu/dataset/791/metropt%203%20dataset#:~:text=Data%20Set%20Information%3A%20The%20dataset,You%20can)
[\[14\]](https://archive.ics.uci.edu/dataset/791/metropt%203%20dataset#:~:text=Are%20there%20recommended%20data%20splits%3F)
[\[15\]](https://archive.ics.uci.edu/dataset/791/metropt%203%20dataset#:~:text=License)
UCI Machine Learning Repository

<https://archive.ics.uci.edu/dataset/791/metropt%203%20dataset>

[\[16\]](https://www.mdpi.com/2076-3417/11/1/18#:~:text=The%20data%20were%20acquired%20over,records%20for%20the%20year%202014)
[\[17\]](https://www.mdpi.com/2076-3417/11/1/18#:~:text=The%20second%20source%20of%20information,type%20over%20the%20year%202015)
Application of Predictive Maintenance Concepts Using Artificial
Intelligence Tools

<https://www.mdpi.com/2076-3417/11/1/18>

[\[18\]](https://researchdata.se/en/catalogue/dataset/2024-34#:~:text=This%20data%20is%20a%20real,The%20objective%20of)
[\[19\]](https://researchdata.se/en/catalogue/dataset/2024-34#:~:text=)
[\[20\]](https://researchdata.se/en/catalogue/dataset/2024-34#:~:text=)
SCANIA Component X Dataset: A Real-World Multivariate Time Series
Dataset for Predictive Maintenance

<https://researchdata.se/en/catalogue/dataset/2024-34>

[\[21\]](https://www.mdpi.com/2306-5729/9/12/138#:~:text=The%20data%20consist%20of%2095,points%20of%20the%20time%20series)
[\[22\]](https://www.mdpi.com/2306-5729/9/12/138#:~:text=The%20number%20of%20features%20in,indicating%20the%20turbine%20status%20at)
[\[23\]](https://www.mdpi.com/2306-5729/9/12/138#:~:text=The%20data%20are%20labeled%20on,the%20data%2C%20and%20expert%20knowledge)
CARE to Compare: A Real-World Benchmark Dataset for Early Fault
Detection in Wind Turbine Data

<https://www.mdpi.com/2306-5729/9/12/138>

[\[24\]](https://www.kaggle.com/datasets/azizkasimov/wind-turbine-scada-data-for-early-fault-detection)
Wind Turbine SCADA Data For Early Fault Detection

<https://www.kaggle.com/datasets/azizkasimov/wind-turbine-scada-data-for-early-fault-detection>
