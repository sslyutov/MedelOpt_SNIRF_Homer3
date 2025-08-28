### Purpose

This document provides a combined specification of SNIRF data format along with the corresponding HDF5 definitions for each data element.<br>
a. It is requiedted by Marion to save raw red and IR data, regardless the fact SNIRF specification does not support such tipes of data<br>
b. Homer3 expects to see label for data type HbO, HbR.<br>
c minimum number of sample in snirf file is 9. This is a Homer3 reqirement.<br>
d hmrR_BandpassFilt requires data larger than 15 samples.

### Intro

### SNIRF/HDF5 File Structure

- /
  - formatVersion
  - nirs
    - data1
      - dataTimeSeries
      - measurementList1, measurementList2, ... measurementListN
        - dataType
        - dataTypeIndex
        - detectorIndex
        - sourceIndex
        - wavelengthIndex
      - time
    - metaDataTags
      - SubjectID
      - MeasurementDate
      - MeasurementTime
      - LengthUnit
      - TimeUnit
      - FrequencyUnit
      - SubjectName
      - StudyID
      - ManufacturerName
    - probe
      - detectorPos3D
      - sourcePos3D
      - wavelengths
    - stim1, stim2, ..., stimN
      - data
      - name
    - aux
      - [TBD]

Every segment/acquisition of data should be saved into an individual "SNIRF" file.

### legend
|color code|description|
|---|---|
|🔴| required, high severity, requires addition information|
|🟡| low severiry |
|🟢| implemented in AcqKnowledge |
|🟩| supported by the Seenel Imaging Coversion Utility |

### root
| Name            | HDF5 Type           | Description                                                          |
|-----------------|---------------------|----------------------------------------------------------------------|
| formatVersion   |Scalar Dataset; String; length = variable; padding = H5T_STR_NULLTERM; cset = H5T_CSET_ASCII||

### nirs - group; one per a data acquisition. 

### data1 Group (Group, always named 'data1'.)

| Name            | HDF5 Type           | Description                                                                                         |
|-----------------|---------------------|-----------------------------------------------------------------------------------------------------|
| 🟢dataTimeSeries  | 2-dimensional Dataset, 64-bit floating-point | First dimension: sample index (s) <br> Second dimension: channel index (c) <br> Data is ordered as:<br>`arr[s0][c0], arr[s0][c1], ..., arr[sn][c0], arr[sn][c1], ..., arr[sn][c_last]` |


### Multiple `measurementList` groups exist within the `data` group.  
The number of entries must match the number of channels in `dataTimeSeries`.

| Field           | HDF5 Type                        | Description                                        |
|-----------------|----------------------------------|----------------------------------------------------|
| 🟡`dataType`        | Scalar Dataset, 32-bit integer | Indicates data type 1 -  |
| 🟡`dataTypeIndex`   | Scalar Dataset, 32-bit integer | Index for data type. 1 - amplitude |
| 🟢`detectorIndex`   | Scalar Dataset, 32-bit integer | Index of the detector (is the value 0-based or 1-based?) |
| 🟢`sourceIndex`     | Scalar Dataset, 32-bit integer | Index of the source (is the value 0-based or 1-based?) |
| 🟢`wavelengthIndex` | Scalar Dataset, 32-bit integer | Index of the wavelength (is the value 0-based or 1-based?) |



| Field           | HDF5 Type                         | Description                                                                 |
|-----------------|-----------------------------------|-----------------------------------------------------------------------------|
| 🟢`time`          | 1-dimensional array, 64-bit floating-point | Number of elements must match the number of samples in `dataTimeSeries`.   |


### metaDataTags Group

One 🟡`metaDataTags` group is present per `nirs` group. mandatory for SNIRF format, not required in Homer3

| Field             | HDF5 Type   | Description                                |
|-------------------|-------------|--------------------------------------------|
| 🟡`SubjectID`       | String Length = variable, padding = `H5T_STR_NULLTERM`, cset = `H5T_CSET_UTF8` ||
| 🟡`MeasurementDate` | String Length = variable, padding = `H5T_STR_NULLTERM`, cset = `H5T_CSET_UTF8` ||
| 🟡`MeasurementTime` | String Length = variable, padding = `H5T_STR_NULLTERM`, cset = `H5T_CSET_UTF8` ||
| 🟡`LengthUnit`      | String Length = variable, padding = `H5T_STR_NULLTERM`, cset = `H5T_CSET_UTF8` ||
| 🟡`TimeUnit`        | String Length = variable, padding = `H5T_STR_NULLTERM`, cset = `H5T_CSET_UTF8` ||
| 🟡`FrequencyUnit`   | String Length = variable, padding = `H5T_STR_NULLTERM`, cset = `H5T_CSET_UTF8` ||
| 🟡`SubjectName`     | String Length = variable, padding = `H5T_STR_NULLTERM`, cset = `H5T_CSET_UTF8` ||
| 🟡`StudyID`         | String Length = variable, padding = `H5T_STR_NULLTERM`, cset = `H5T_CSET_UTF8` ||
| 🟡`ManufacturerName`| String Length = variable, padding = `H5T_STR_NULLTERM`, cset = `H5T_CSET_UTF8` ||


### probe Group

Defines spatial and spectral configuration.

| Field           | HDF5 Type                            | Description                                                |
|-----------------|----------------------------------|------------------------------------------------------------|
| 🟡`detectorPos3D` | 2-dimensional Dataset, 64-bit floating-point | 3D positions of detectors (e.g., `[nDetectors][3]`)        |
| 🟡`sourcePos3D`   | 2-dimensional Dataset, 64-bit floating-point | 3D positions of sources (e.g., `[nSources][3]`)            |
| 🟢`wavelengths`   | 1-dimensional Dataset, 64-bit floating-point | Contains exactly 2 elements representing wavelengths used  |

- **`sourcePos2D` / `sourcePos3D`**
  - Always contain a number of records equal to the number of physical sources (LEDs) on the device.  
  - Example: if the device has **16 LEDs**, the probe group will have **16 records**.  
  - If the position for a source is undefined, its coordinate values are set to `0.0`.  

- **`detectorPos2D` / `detectorPos3D`**
  - Always contain a number of records equal to the number of physical detectors on the device.  
  - Example: for **MedelOpt**, the number of records is **32**.  
  - If the position for a detector is undefined, its coordinate values are set to `0.0`.  

- **Indexing rule**
  - The record index corresponds directly to the source or detector **ID**.  
  - It does **not depend on the `measurementList` order** or discovery order.  
  - Example: `sourcePos3D[5]` always represents the position of **source #6** (if indices are 1-based in the file).
    

### stim1, stim2, ..., stimN Groups

These groups describe stimulus (trigger) events as well as manually set markers in AcqKnowledge.<br>  
MedelOpt may support up to 4 triggers. Each `stim` group corresponds to one auxiliary trigger.<br>
Also a stim group is created for each manual trigger set from AcqKnowledge. The duration for manual trigger is set to .001 second
as a minimal value.<br>
The total number of stim groups depends on a number of event sources registered during a data acquisition.
In AcqKnowledge, if the trigger(gpio) is set to the ON position before the start of data acquisition, the trigger marker is added at the second sample.
<br>

| Field   | Type                             | Description                                                                 |
|---------|----------------------------------|-----------------------------------------------------------------------------|
| 🟢`data`  | 2-dimensional Dataset 64-bit floating-point            | First dimension: data which includes three fields<br>timestamp in seconds<br>duration in seconds<>;value - for MedelOpt used only value 1<br> second dimension: measurement index.  
Data is organized as:  
`data[0][0], data[0][1], data[0][2], data[1][0], data[1][1], data[1][2]`|
| 🟢`name`  | Scalar Dataset, String  Length = variable, padding = `H5T_STR_NULLTERM`, cset = `H5T_CSET_UTF8`||

addition descrition for two–dimensional array of data field:
- **First dimension** → record index  
- **Second dimension** → data fields  

| **Dimension** | **Description** | **Fields** | **Notes** |
|---------------|-----------------|------------|------------|
| 1 (record index) | Identifies each record | – | Sequential index |
| 2 (data) | Contains fields for each record | • `timestamp` (seconds)<br>• `duration` (seconds)<br>• `value` (always `1` for MedelOpt) | Fixed structure |

Notes:

|AcqKnowledge markers recognized as stim group| description |
|---|---|
|kUser1EventType| user event set from keyboard during a data acquisition |
|kUser2EventType| user event set from keyboard during a data acquisition |
|kUser3EventType| user event set from keyboard during a data acquisition |
|kUser4EventType| user event set from keyboard during a data acquisition |
|kUser5EventType| user event set from keyboard during a data acquisition |
|kUser6EventType| user event set from keyboard during a data acquisition |
|kUser7EventType| user event set from keyboard during a data acquisition |
|kUser8EventType| user event set from keyboard during a data acquisition |
|kUser9EventType| user event set from keyboard during a data acquisition |
|||
|kTrigger1OnEventType| MedelOpt device trigger 1 On - used to get trigger starting timestamp|
|kTrigger1OffEventType| MedelOpt device trigger 1 Off - used for calculating a duration|
|kTrigger2OnEventType| MedelOpt device trigger 2 On - used to get trigger starting timestamp|
|kTrigger2OffEventType| MedelOpt device trigger 2 Off - used for calculating a duration|
|kTrigger3OnEventType| MedelOpt device trigger 3 On - used to get trigger starting timestamp|
|kTrigger3OffEventType| MedelOpt device trigger 3 Off - used for calculating a duration|
|kTrigger4OnEventType| MedelOpt device trigger 4 On - used to get trigger starting timestamp|
|kTrigger4OffEventType| MedelOpt device trigger 4 Off - used for calculating a duration|


### aux Group

The `aux` group is **reserved** for describing accelerometer or similar auxiliary data sources.  
It is currently **unknown** whether multiple `aux` groups should be numbered (e.g., `aux1`, `aux2`, ...).

| Field | Type | Description |
|-------|------|-------------|
| *TBD* | *TBD* | Structure and content of this group are not fully defined yet. 


### History of Changes
|date|description|
|----|-----------|
||no changes|





















