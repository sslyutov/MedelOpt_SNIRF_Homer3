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
  "version": "MeMoSoft v1.0",<br>
  "participant_id": 1,<br>
  "head_distances": {<br>
    "nasion_inion": "57.0 cm",<br>
    "lpa_rpa": "58.0 cm",<br>
    "circumference": "57.0 cm"<br>
  },<br>
  "eegChannels": [<br>
    {<br>
      "id": "EEG1",<br> 
      "label": "EEG-1",<br> 
      "acquire": 1,<br> 
      "plot": 1,<br> 
      "value": 0<br>
    },<br>
    {<br>
      "id": "EEG2",<br> 
      "label": "EEG-2",<br> 
      "acquire": 1,<br> 
      "plot": 1,<br> 
      "value": 0<br>
    },<br>
    {<br>
      "id": "EEG3",<br> 
      "label": "EEG-3",<br> 
      "acquire": 1,<br> 
      "plot": 1,<br> 
      "value": 0<br>
    },<br>
    {<br>
      "id": "EEG4",<br> 
      "label": "EEG-4",<br> 
      "acquire": 1,<br> 
      "plot": 1,<br> 
      "value": 0<br>
    },<br>
    {<br>
      "id": "EEG5",<br> 
      "label": "EEG-5",<br> 
      "acquire": 1,<br> 
      "plot": 0,<br> 
      "value": 0<br>
    },<br>
    {<br>
      "id": "EEG6",<br> 
      "label": "EEG-6",<br> 
      "acquire": 1,<br> 
      "plot": 0,<br> 
      "value": 0<br>
    },<br>
    {<br>
      "id": "EEG7",<br> 
      "label": "EEG-7",<br> 
      "acquire": 1,<br> 
      "plot": 1,<br> 
      "value": 0<br>
    },<br>
    {<br>
      "id": "EEG8",<br> 
      "label": "EEG-8",<br> 
      "acquire": 1,<br> 
      "plot": 0,<br> 
      "value": 0<br>
    }<br>
  ],<br>
  "channels": [<br>
    { "name": "LED1_DET1", "distance_cm": 2.9 },<br>
    { "name": "LED1_DET2", "distance_cm": 3.2 },<br>
    { "name": "LED1_DET3", "distance_cm": 3.2 },<br>
    { "name": "LED1_DET4", "distance_cm": 3.2 },<br>
    { "name": "LED2_DET5", "distance_cm": 3.2 },<br>
    { "name": "LED2_DET6", "distance_cm": 3.2 },<br>
    { "name": "LED2_DET7", "distance_cm": 3.2 },<br>
    { "name": "LED3_DET8", "distance_cm": 3.2 },<br>
    { "name": "LED3_DET9", "distance_cm": 3.2 },<br>
    { "name": "LED3_DET10", "distance_cm": 3.2 },<br>
    { "name": "LED4_DET11", "distance_cm": 3.2 },<br>
    { "name": "LED4_DET12", "distance_cm": 3.2 },<br>
    { "name": "LED4_DET13", "distance_cm": 3.2 },<br>
    { "name": "LED4_DET14", "distance_cm": 3.2 },<br>
    { "name": "LED4_DET15", "distance_cm": 3.2 },<br>
    { "name": "LED4_DET16", "distance_cm": 3.2 }<br>
  ],<br>
  "montage_positions": [<br>
    {<br>
      "position": "Oz",<br>
      "medelopt": "LED1",<br>
      "dist_to_cz_cm": 21,<br>
      "dist_to_middle_of_curve_cm": 11.4,<br>
      "pos2D_X_mm": -85.0,<br>
      "pos2D_Y_mm": 85.0,<br>
      "pos3D_X_mm": -45.3,<br>
      "pos3D_Y_mm": 62.26,<br>
      "pos3D_Z_mm": -9.39,<br>
    },<br>
    {<br>
      "position": "POz",<br>
      "medelopt": "DET1",<br>
      "dist_to_cz_cm": 21,<br>
      "dist_to_middle_of_curve_cm": 11.4<br>
    },<br>
    {<br>
      "position": "Iz",<br>
      "medelopt": "DET2",<br>
      "dist_to_cz_cm": 21,<br>
      "dist_to_middle_of_curve_cm": 11.4<br>
    },<br>
    {<br>
      "position": "O1",<br>
      "medelopt": "DET3",<br>
      "dist_to_cz_cm": 21,<br>
      "dist_to_middle_of_curve_cm": 11.4<br>
    },<br>
    {<br>
      "position": "O2",<br>
      "medelopt": "DET4",<br>
      "dist_to_cz_cm": 21,<br>
      "dist_to_middle_of_curve_cm": 11.4<br>
    },<br>
    {<br>
      "position": "P7",<br>
      "medelopt": "LED2",<br>
      "dist_to_cz_cm": 21,<br>
      "dist_to_middle_of_curve_cm": 11.4<br>
    },<br>
    {<br>
      "position": "P9",<br>
      "medelopt": "DET5",<br>
      "dist_to_cz_cm": 21,<br>
      "dist_to_middle_of_curve_cm": 11.4<br>
    },<br>
    {<br>
      "position": "P5",<br>
      "medelopt": "DET6",<br>
      "dist_to_cz_cm": 21,<br>
      "dist_to_middle_of_curve_cm": 11.4<br>
    },<br>
    {<br>
      "position": "PO7",<br>
      "medelopt": "DET7",<br>
      "dist_to_cz_cm": 21,<br>
      "dist_to_middle_of_curve_cm": 11.4<br>
    },<br>
    {<br>
      "position": "P1",<br>
      "medelopt": "LED3",<br>
      "dist_to_cz_cm": 21,<br>
      "dist_to_middle_of_curve_cm": 11.4<br>
    },<br>
    {<br>
      "position": "P3",<br>
      "medelopt": "DET8",<br>
      "dist_to_cz_cm": 21,<br>
      "dist_to_middle_of_curve_cm": 11.4<br>
    },<br>
    {<br>
      "position": "PO3",<br>
      "medelopt": "DET9",<br>
      "dist_to_cz_cm": 21,<br>
      "dist_to_middle_of_curve_cm": 11.4<br>
    },<br>
    {<br>
      "position": "Pz",<br>
      "medelopt": "DET10",<br>
      "dist_to_cz_cm": 21,<br>
      "dist_to_middle_of_curve_cm": 11.4<br>
    },<br>
    {<br>
      "position": "PO8",<br>
      "medelopt": "LED4",<br>
      "dist_to_cz_cm": 21,<br>
      "dist_to_middle_of_curve_cm": 11.4<br>
    },<br>
    {<br>
      "position": "PO4",<br>
      "medelopt": "DET11",<br>
      "dist_to_cz_cm": 21,<br>
      "dist_to_middle_of_curve_cm": 11.4<br>
    },<br>
    {<br>
      "position": "P2",<br>
      "medelopt": "DET12",<br>
      "dist_to_cz_cm": 21,<br>
      "dist_to_middle_of_curve_cm": 11.4<br>
    },<br>
    {<br>
      "position": "P4",<br>
      "medelopt": "DET13",<br>
      "dist_to_cz_cm": 21,<br>
      "dist_to_middle_of_curve_cm": 11.4<br>
    },<br>
    {<br>
      "position": "P6",<br>
      "medelopt": "DET14",<br>
      "dist_to_cz_cm": 21,<br>
      "dist_to_middle_of_curve_cm": 11.4<br>
    },<br>
    {<br>
      "position": "P8",<br>
      "medelopt": "DET15",<br>
      "dist_to_cz_cm": 21,<br>
      "dist_to_middle_of_curve_cm": 11.4<br>
    },<br>
    {<br>
      "position": "P10",<br>
      "medelopt": "DET16",<br>
      "dist_to_cz_cm": 21,<br>
      "dist_to_middle_of_curve_cm": 11.4<br>
    }<br>
  ]<br>
}    
