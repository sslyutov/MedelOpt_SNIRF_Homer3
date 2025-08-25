This file contains the fNIRS montage configuration data in a format intended for direct transfer from MeMoSoft (Seenel Imaging) to AcqKnowledge (Biopac Systems, Inc.), ensuring compatibility of optode layout, channel assignments, and acquisition settings between the two applications.
The data is stored in json format

|icon|description|
|---|---|
|🔴|not supported by acqknowledge|
|🟥|not supported by memosoft|
|🟡|need to check in acqknowledge|
|🟨|need to check in memosoft|
|🟢|supported by acqknowledge|
|🟩|supported by memosoft|


### file structure ###

|parent|name|type|description|
|---|---|---|---|
|🟢🟩root|version|string|Description of MeMpSoft version|
|🟢🟩root|participant_id|number|Participant ID as a numeric value|
|🟢🟩root|head_distances|object|Contains head measurement properties|
|🟢🟩head_distances|nasion_inion|string number|Distance from nasion to inion (e.g., "57.0 cm")|
|🟢🟩head_distances|lpa_rpa|string number|Distance from left preauricular point to right preauricular point (e.g., "58.0 cm")|
|🟢🟩head_distances|circumference|string number|Head circumference (e.g., "57.0 cm")|
|🟢🟨root|eegChannels|array|Array of EEG channel configuration objects|
|🟢🟨eegChannels[]|id|string|ID used for programmatic detection of this element (e.g., "EEG1")|
|🟢🟨eegChannels[]|label|string|Human-readable label (e.g., "EEG-1")|
|🟢🟨eegChannels[]|acquire|number|1 = channel is acquired; 0 = not acquired| 
|🟢🟨eegChannels[]|plot|number|1 = channel is displayed/visible; 0 = not displayed|
|🟢🟨eegChannels[]|value|number|1 = channel is plotted in the output panel; 0 = not plotted|
|🟢🟩root|channels|array|Collection of optode pairs configuration|
|🟢🟩channels[]|name|string|Fixed format: <source_id>_<detector_id> (e.g., "LED1_DET1")|
|🟢🟩channels[]|distance_cm|number (float)|Distance between source and detector in centimeters (e.g., 2.9)|
|🟢🟩root|montage_positions|array|Collection of montage position descriptions|
|🟢🟩montage_positions[]|position|string|Standard position name (e.g., "Oz")|
|🟢🟩montage_positions[]|medelopt|string|Optode identifier (e.g., "LED1" for LED and "DET1" for detector)|
|🟢🟩montage_positions[]|dist_to_cz_cm|string|Distance to CZ in centimeters (e.g., "21")|
|🟢🟩montage_positions[]|dist_to_middle_of_curve_cm|number (float)|Distance to middle of head curve in centimeters (e.g., 11.4)|
|🔴🟥montage_positions[]|pos2D_X_mm|number (float)|2D X position in millimeters (e.g., -85.0)|
|🔴🟥montage_positions[]|pos2D_Y_mm|number (float)|2D Y position in millimeters (e.g., 85.0)|
|🔴🟥montage_positions[]|pos3D_X_mm|number (float)|3D X position in millimeters (e.g., -45.3)|
|🔴🟥montage_positions[]|pos3D_Y_mm|number (float)|3D Y position in millimeters (e.g., 62.26)|
|🔴🟥montage_positions[]|pos3D_Z_mm|number (float)|3D Z position in millimeters (e.g., -9.39)|

probe->montage_positions
  pos2D_X_mm Identifies the x-position in 2D for an LED or DET with the corresponding value (such as LED1 or DET1) of the 'medelopt' property.
  pos2D_Y_mm Identifies the y-position in 2D for an LED or DET with the corresponding value (such as LED1 or DET1) of the 'medelopt' property.
  pos3D_X_mm Identifies the x-position in 3D for an LED or DET with the corresponding value (such as LED1 or DET1) of the 'medelopt' property.
  pos3D_Y_mm Identifies the y-position in 3D for an LED or DET with the corresponding value (such as LED1 or DET1) of the 'medelopt' property.
  pos3D_X_mm Identifies the z-position in 3D for an LED or DET with the corresponding value (such as LED1 or DET1) of the 'medelopt' property.
  

### example of the file ###
[EEG fNIRS example](examples/eeg_fnirs.jmms)
