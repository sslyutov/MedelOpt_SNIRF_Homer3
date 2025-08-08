### Purpose

This document provides a combined specification of SNIRF data format along with the corresponding HDF5 definitions for each data element.
a. It is requiedted by Marion to save raw red and IR data, regardless the fact SNIRF specification does not support such tipes of data
b. Homer3 expects to see label for data type HbO, HbR.
c minimum number of sample in snirf file is 9. This is a Homer3 reqirement.

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

### root
| Name            | HDF5 Type           | Description                                                          |
|-----------------|---------------------|----------------------------------------------------------------------|
| formatVersion   |Scalar Dataset; String; length = variable; padding = H5T_STR_NULLTERM; cset = H5T_CSET_ASCII||

### nirs - group; one per a data acquisition. 

### data1 Group (Group, always named 'data1'.)

| Name            | HDF5 Type           | Description                                                                                         |
|-----------------|---------------------|-----------------------------------------------------------------------------------------------------|
| dataTimeSeries  | 2-dimensional Dataset, 64-bit floating-point | First dimension: sample index (s) <br> Second dimension: channel index (c) <br> Data is ordered as:<br>`arr[s0][c0], arr[s0][c1], ..., arr[sn][c0], arr[sn][c1], ..., arr[sn][c_last]` |


### Multiple `measurementList` groups exist within the `data` group.  
The number of entries must match the number of channels in `dataTimeSeries`.

| Field           | HDF5 Type                        | Description                                        |
|-----------------|----------------------------------|----------------------------------------------------|
| `dataType`        | Scalar Dataset, 32-bit integer | Indicates data type (is the value 0-based or 1-based?) |
| `dataTypeIndex`   | Scalar Dataset, 32-bit integer | Index for data type (is the value 0-based or 1-based?) |
| `detectorIndex`   | Scalar Dataset, 32-bit integer | Index of the detector (is the value 0-based or 1-based?) |
| `sourceIndex`     | Scalar Dataset, 32-bit integer | Index of the source (is the value 0-based or 1-based?) |
| `wavelengthIndex` | Scalar Dataset, 32-bit integer | Index of the wavelength (is the value 0-based or 1-based?) |



| Field           | HDF5 Type                         | Description                                                                 |
|-----------------|-----------------------------------|-----------------------------------------------------------------------------|
| `time`          | 1-dimensional array, 64-bit floating-point | Number of elements must match the number of samples in `dataTimeSeries`.   |


### metaDataTags Group

One `metaDataTags` group is present per `nirs` group.

| Field             | HDF5 Type   | Description                                |
|-------------------|-------------|--------------------------------------------|
| `SubjectID`       | String Length = variable, padding = `H5T_STR_NULLTERM`, cset = `H5T_CSET_UTF8` ||
| `MeasurementDate` | String Length = variable, padding = `H5T_STR_NULLTERM`, cset = `H5T_CSET_UTF8` ||
| `MeasurementTime` | String Length = variable, padding = `H5T_STR_NULLTERM`, cset = `H5T_CSET_UTF8` ||
| `LengthUnit`      | String Length = variable, padding = `H5T_STR_NULLTERM`, cset = `H5T_CSET_UTF8` ||
| `TimeUnit`        | String Length = variable, padding = `H5T_STR_NULLTERM`, cset = `H5T_CSET_UTF8` ||
| `FrequencyUnit`   | String Length = variable, padding = `H5T_STR_NULLTERM`, cset = `H5T_CSET_UTF8` ||
| `SubjectName`     | String Length = variable, padding = `H5T_STR_NULLTERM`, cset = `H5T_CSET_UTF8` ||
| `StudyID`         | String Length = variable, padding = `H5T_STR_NULLTERM`, cset = `H5T_CSET_UTF8` ||
| `ManufacturerName`| String Length = variable, padding = `H5T_STR_NULLTERM`, cset = `H5T_CSET_UTF8` ||


### probe Group

Defines spatial and spectral configuration.

| Field           | HDF5 Type                            | Description                                                |
|-----------------|----------------------------------|------------------------------------------------------------|
| `detectorPos3D` | 2-dimensional Dataset, 64-bit floating-point | 3D positions of detectors (e.g., `[nDetectors][3]`)        |
| `sourcePos3D`   | 2-dimensional Dataset, 64-bit floating-point | 3D positions of sources (e.g., `[nSources][3]`)            |
| `wavelengths`   | 1-dimensional Dataset, 64-bit floating-point | Contains exactly 2 elements representing wavelengths used  |

### stim1, stim2, ..., stimN Groups

These groups describe stimulus (trigger) events.  
MedelOpt may support up to 4 triggers. Each `stim` group corresponds to one auxiliary trigger.

| Field   | Type                             | Description                                                                 |
|---------|----------------------------------|-----------------------------------------------------------------------------|
| `data`  | 2-dimensional Dataset 64-bit floating-point            | First dimension: data index; second dimension: measurement index.  
Data is organized as:  
`data[0][0], data[0][1], data[0][2], data[1][0], data[1][1], data[1][2]` |
| `name`  | Scalar Dataset, String  Length = variable, padding = `H5T_STR_NULLTERM`, cset = `H5T_CSET_UTF8`||
Notes:

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



