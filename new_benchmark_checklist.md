# MLPerf Inference New Benchmark Checklist Documentation

This document provides guidelines and requirements for setting up and validating a new MLPerf Inference benchmark implementation.

---

## 1. Applicable Categories
Specify whether the benchmark applies to:
- **Edge**
- **Datacenter**
- **Both**

## 2. Applicable Scenarios for Each Category
List each scenario applicable to the selected categories. Examples of scenarios include:
- **Single-stream**
- **Multi-stream**
- **Server**
- **Offline**

## 3. Applicable Compliance Tests
Identify the compliance tests required for each applicable category and scenario. Note:
- **TEST04** is **not applicable** if processing times vary significantly for different inputs.

## 4. Latency Threshold for Server Scenarios
If the **Server** scenario is applicable:
- Document the latency threshold. **(99% of the samples must be processed within the specified latency threshold)**.

## 5. Validation Dataset: Unique Samples
Specify the number of **unique samples** in the validation dataset and the **QSL size**. Note that:
- The unique samples will be repeated as necessary to meet the minimum required duration for the inference run.
- QSL size determines the number of inputs which are loaded to the memory at a time - typically large enough to overflow the system cache. 

## 6. Equal Issue Mode Applicability
Document whether **Equal Issue Mode** is applicable:
- This is relevant if the time required to process a sample is not consistent across all inputs.

## 7. Expected accuracy and `accuracy.txt` Contents
Detail the expected contents of the `accuracy.txt` file after running the reference accuracy script. This file should reflect the accuracy performance based on the validation dataset and reference model. 

## 8. Reference Model details
Number of Parameters of the model, FLOPs and the data type used for determining the reference accuracy. **For example, Number of Parameters: 25.6 million, FLOPs: 3.8 billion, Datatype: fp16**

## 9. Reference Implementation Dataset Coverage
Ensure the reference implementation can successfully processes the entire validation dataset during **performance**, **accuracy**, and applicable **compliance** runs and generate valid log files.

## 10. Test Runs with Smaller Input Sets
Verify that the reference implementation can perform test runs with a smaller subset of inputs for **performance** and **accuracy** runs.

## 11. Dataset and Reference Model Instructions
Provide clear instructions on:
- **Downloading** the dataset and reference model.
- **Using** the dataset and model for the benchmark.

## 12. CPU-Only and Minimum GPU Requirements
Document:
- Whether the reference implementation can run on **CPUs only**.
- The **minimum number** of GPUs and **required memory** if GPU usage is necessary.

## 13. System Memory and Storage Requirements
Specify the minimum system requirements to run the reference implementation:
- **System RAM**: Units of 256 GB RAM.
- **Storage**: Units of 500 GB storage.

## 14. Submission Checker Modifications
Ensure all necessary changes are made to the **submission checker** to validate the benchmark correctly.

## 15. Sample Log Files
Include sample logs for all applicable scenario runs:
- `mlperf_log_summary.txt`
- `mlperf_log_detail.txt`
  
These files should successfully pass the submission checker and represent a compliant run.
