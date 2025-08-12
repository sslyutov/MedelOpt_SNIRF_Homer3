This file contains the fNIRS montage configuration data in a format intended for direct transfer from MeMoSoft (Seenel Imaging) to AcqKnowledge (Biopac Systems, Inc.), ensuring compatibility of optode layout, channel assignments, and acquisition settings between the two platforms.
The data is stored in json format

### file structure ###

|parent|name|type|description|
|---|---|---|---|
|root|version|string|Description of MeMpSoft version|
|root|participant_id|number|Participant ID as a numeric value|
|root|head_distances|object|Contains head measurement properties|
|head_distances|nasion_inion|string number|Distance from nasion to inion (e.g., "57.0 cm")|
|head_distances|lpa_rpa|string number|Distance from left preauricular point to right preauricular point (e.g., "58.0 cm")|
|head_distances|circumference|string number|Head circumference (e.g., "57.0 cm")|
|root|eegChannels|array|Array of EEG channel configuration objects|
|eegChannels[]|id|string|ID used for programmatic detection of this element (e.g., "EEG1")|
|eegChannels[]|label|string|Human-readable label (e.g., "EEG-1")|
|eegChannels[]|acquire|number|1 = channel is acquired; 0 = not acquired| 
|eegChannels[]|plot|number|1 = channel is displayed/visible; 0 = not displayed|
|eegChannels[]|value|number|1 = channel is plotted in the output panel; 0 = not plotted|
|root|channels|array|Collection of optode pairs configuration|
|channels[]|name|string|Fixed format: <source_id>_<detector_id> (e.g., "LED1_DET1")|
|channels[]|distance_cm|number (float)|Distance between source and detector in centimeters (e.g., 2.9)|
|root|montage_positions|array|Collection of montage position descriptions|
|montage_positions[]|position|string|Standard position name (e.g., "Oz")|
|montage_positions[]|medelopt|string|Optode identifier (e.g., "LED1" for LED and "DET1" for detector)|
|montage_positions[]|dist_to_cz_cm|string|Distance to CZ in centimeters (e.g., "21")|
|montage_positions[]|dist_to_middle_of_curve_cm|number (float)|Distance to middle of head curve in centimeters (e.g., 11.4)|
|montage_positions[]|pos2D_X_mm|number (float)|2D X position in millimeters (e.g., -85.0)|
|montage_positions[]|pos2D_Y_mm|number (float)|2D Y position in millimeters (e.g., 85.0)|
|montage_positions[]|pos3D_X_mm|number (float)|3D X position in millimeters (e.g., -45.3)|
|montage_positions[]|pos3D_Y_mm|number (float)|3D Y position in millimeters (e.g., 62.26)|
|montage_positions[]|pos3D_Z_mm|number (float)|3D Z position in millimeters (e.g., -9.39)|


### example of the file ###
{
  "version": "MeMoSoft v1.0",\n
  "participant_id": 1,\n
  "head_distances": {\n
    "nasion_inion": "57.0 cm",\n
    "lpa_rpa": "58.0 cm",\n
    "circumference": "57.0 cm"\n
  },\n
  "eegChannels": [\n
    {\n
      "id": "EEG1",\n 
      "label": "EEG-1",\n 
      "acquire": 1,\n 
      "plot": 1,\n 
      "value": 0\n
    },\n
    {\n
      "id": "EEG2",\n 
      "label": "EEG-2",\n 
      "acquire": 1,\n 
      "plot": 1,\n 
      "value": 0\n
    },\n
    {\n
      "id": "EEG3",\n 
      "label": "EEG-3",\n 
      "acquire": 1,\n 
      "plot": 1,\n 
      "value": 0\n
    },\n
    {\n
      "id": "EEG4",\n 
      "label": "EEG-4",\n 
      "acquire": 1,\n 
      "plot": 1,\n 
      "value": 0\n
    },\n
    {\n
      "id": "EEG5",\n 
      "label": "EEG-5",\n 
      "acquire": 1,\n 
      "plot": 0,\n 
      "value": 0\n
    },\n
    {\n
      "id": "EEG6",\n 
      "label": "EEG-6",\n 
      "acquire": 1,\n 
      "plot": 0,\n 
      "value": 0\n
    },\n
    {\n
      "id": "EEG7",\n 
      "label": "EEG-7",\n 
      "acquire": 1,\n 
      "plot": 1,\n 
      "value": 0\n
    },\n
    {\n
      "id": "EEG8",\n 
      "label": "EEG-8",\n 
      "acquire": 1,\n 
      "plot": 0,\n 
      "value": 0\n
    }\n
  ],\n
  "channels": [\n
    { "name": "LED1_DET1", "distance_cm": 2.9 },\n
    { "name": "LED1_DET2", "distance_cm": 3.2 },\n
    { "name": "LED1_DET3", "distance_cm": 3.2 },\n
    { "name": "LED1_DET4", "distance_cm": 3.2 },\n
    { "name": "LED2_DET5", "distance_cm": 3.2 },\n
    { "name": "LED2_DET6", "distance_cm": 3.2 },\n
    { "name": "LED2_DET7", "distance_cm": 3.2 },\n
    { "name": "LED3_DET8", "distance_cm": 3.2 },\n
    { "name": "LED3_DET9", "distance_cm": 3.2 },\n
    { "name": "LED3_DET10", "distance_cm": 3.2 },\n
    { "name": "LED4_DET11", "distance_cm": 3.2 },\n
    { "name": "LED4_DET12", "distance_cm": 3.2 },\n
    { "name": "LED4_DET13", "distance_cm": 3.2 },\n
    { "name": "LED4_DET14", "distance_cm": 3.2 },\n
    { "name": "LED4_DET15", "distance_cm": 3.2 },\n
    { "name": "LED4_DET16", "distance_cm": 3.2 }\n
  ],\n
  "montage_positions": [\n
    {\n
      "position": "Oz",\n
      "medelopt": "LED1",\n
      "dist_to_cz_cm": 21,\n
      "dist_to_middle_of_curve_cm": 11.4,\n
      "pos2D_X_mm": -85.0,\n
      "pos2D_Y_mm": 85.0,\n
      "pos3D_X_mm": -45.3,\n
      "pos3D_Y_mm": 62.26,\n
      "pos3D_Z_mm": -9.39,\n
    },\n
    {\n
      "position": "POz",\n
      "medelopt": "DET1",\n
      "dist_to_cz_cm": 21,\n
      "dist_to_middle_of_curve_cm": 11.4\n
    },\n
    {\n
      "position": "Iz",\n
      "medelopt": "DET2",\n
      "dist_to_cz_cm": 21,\n
      "dist_to_middle_of_curve_cm": 11.4\n
    },\n
    {\n
      "position": "O1",\n
      "medelopt": "DET3",\n
      "dist_to_cz_cm": 21,\n
      "dist_to_middle_of_curve_cm": 11.4\n
    },\n
    {\n
      "position": "O2",\n
      "medelopt": "DET4",\n
      "dist_to_cz_cm": 21,\n
      "dist_to_middle_of_curve_cm": 11.4\n
    },\n
    {\n
      "position": "P7",\n
      "medelopt": "LED2",\n
      "dist_to_cz_cm": 21,\n
      "dist_to_middle_of_curve_cm": 11.4\n
    },\n
    {\n
      "position": "P9",\n
      "medelopt": "DET5",\n
      "dist_to_cz_cm": 21,\n
      "dist_to_middle_of_curve_cm": 11.4\n
    },\n
    {\n
      "position": "P5",\n
      "medelopt": "DET6",\n
      "dist_to_cz_cm": 21,\n
      "dist_to_middle_of_curve_cm": 11.4\n
    },\n
    {\n
      "position": "PO7",\n
      "medelopt": "DET7",\n
      "dist_to_cz_cm": 21,\n
      "dist_to_middle_of_curve_cm": 11.4\n
    },\n
    {\n
      "position": "P1",\n
      "medelopt": "LED3",\n
      "dist_to_cz_cm": 21,\n
      "dist_to_middle_of_curve_cm": 11.4\n
    },\n
    {\n
      "position": "P3",\n
      "medelopt": "DET8",\n
      "dist_to_cz_cm": 21,\n
      "dist_to_middle_of_curve_cm": 11.4\n
    },\n
    {\n
      "position": "PO3",\n
      "medelopt": "DET9",\n
      "dist_to_cz_cm": 21,\n
      "dist_to_middle_of_curve_cm": 11.4\n
    },\n
    {\n
      "position": "Pz",\n
      "medelopt": "DET10",\n
      "dist_to_cz_cm": 21,\n
      "dist_to_middle_of_curve_cm": 11.4\n
    },\n
    {\n
      "position": "PO8",\n
      "medelopt": "LED4",\n
      "dist_to_cz_cm": 21,\n
      "dist_to_middle_of_curve_cm": 11.4\n
    },\n
    {\n
      "position": "PO4",\n
      "medelopt": "DET11",\n
      "dist_to_cz_cm": 21,\n
      "dist_to_middle_of_curve_cm": 11.4\n
    },\n
    {\n
      "position": "P2",\n
      "medelopt": "DET12",\n
      "dist_to_cz_cm": 21,\n
      "dist_to_middle_of_curve_cm": 11.4\n
    },\n
    {\n
      "position": "P4",\n
      "medelopt": "DET13",\n
      "dist_to_cz_cm": 21,\n
      "dist_to_middle_of_curve_cm": 11.4\n
    },\n
    {\n
      "position": "P6",\n
      "medelopt": "DET14",\n
      "dist_to_cz_cm": 21,\n
      "dist_to_middle_of_curve_cm": 11.4\n
    },\n
    {\n
      "position": "P8",\n
      "medelopt": "DET15",\n
      "dist_to_cz_cm": 21,\n
      "dist_to_middle_of_curve_cm": 11.4\n
    },\n
    {\n
      "position": "P10",\n
      "medelopt": "DET16",\n
      "dist_to_cz_cm": 21,\n
      "dist_to_middle_of_curve_cm": 11.4\n
    }\n
  ]\n
}
    
