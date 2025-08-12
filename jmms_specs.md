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

|parent|name|type|description|
|---|---|---|---|
|root|eegChannels|array|Array of EEG channel configuration objects|
|eegChannels[]|id|string|id of the element used for programmatic detecting of this object. example "EEG1".
|eegChannels[]|label|string|Human-readable label (e.g., "EEG-1")
|eegChannels[]|acquire|number|1 to indicate the channel is acquired; 0 otherwise| 
|eegChannels[]|plot|number|1 to indicate the channel is displayed/visible; 0 otherwise|
|eegChannels[]|value|number|1 to indicate the channel is plot of output panel; 0 otherwise|

  

  "channels": [
    { "name": "LED1_DET1", "distance_cm": 2.9 },
    { "name": "LED1_DET2", "distance_cm": 3.2 }
    ],
      "montage_positions": [
    {
      "position": "Oz",
      "medelopt": "LED1",
      "dist_to_cz_cm": 21,
      "dist_to_middle_of_curve_cm": 11.4,
	  "pos2D_X_mm": -85.0,
	  "pos2D_Y_mm": 85.0,
	  "pos3D_X_mm": -45.3,
	  "pos3D_Y_mm": 62.26,
	  "pos3D_Z_mm": -9.39,
    },


### example of the file ###
{
  "version": "MeMoSoft v1.0",
  "participant_id": 1,
  "head_distances": {
    "nasion_inion": "57.0 cm",
    "lpa_rpa": "58.0 cm",
    "circumference": "57.0 cm"
  },
  "eegChannels": [
    {
      "id": "EEG1", 
      "label": "EEG-1", 
      "acquire": 1, 
      "plot": 1, 
      "value": 0
    },
    {
      "id": "EEG2", 
      "label": "EEG-2", 
      "acquire": 1, 
      "plot": 1, 
      "value": 0
    },
    {
      "id": "EEG3", 
      "label": "EEG-3", 
      "acquire": 1, 
      "plot": 1, 
      "value": 0
    },

    {
      "id": "EEG4", 
      "label": "EEG-4", 
      "acquire": 1, 
      "plot": 1, 
      "value": 0
    },

    {
      "id": "EEG5", 
      "label": "EEG-5", 
      "acquire": 1, 
      "plot": 0, 
      "value": 0
    },
    {
      "id": "EEG6", 
      "label": "EEG-6", 
      "acquire": 1, 
      "plot": 0, 
      "value": 0
    },
    {
      "id": "EEG7", 
      "label": "EEG-7", 
      "acquire": 1, 
      "plot": 1, 
      "value": 0
    },
    {
      "id": "EEG8", 
      "label": "EEG-8", 
      "acquire": 1, 
      "plot": 0, 
      "value": 0
    }
  ],
  "channels": [
    { "name": "LED1_DET1", "distance_cm": 2.9 },
    { "name": "LED1_DET2", "distance_cm": 3.2 },
    { "name": "LED1_DET3", "distance_cm": 3.2 },
    { "name": "LED1_DET4", "distance_cm": 3.2 },
    { "name": "LED2_DET5", "distance_cm": 3.2 },
    { "name": "LED2_DET6", "distance_cm": 3.2 },
    { "name": "LED2_DET7", "distance_cm": 3.2 },
    { "name": "LED3_DET8", "distance_cm": 3.2 },
    { "name": "LED3_DET9", "distance_cm": 3.2 },
    { "name": "LED3_DET10", "distance_cm": 3.2 },
    { "name": "LED4_DET11", "distance_cm": 3.2 },
    { "name": "LED4_DET12", "distance_cm": 3.2 },
    { "name": "LED4_DET13", "distance_cm": 3.2 },
    { "name": "LED4_DET14", "distance_cm": 3.2 },
    { "name": "LED4_DET15", "distance_cm": 3.2 },
    { "name": "LED4_DET16", "distance_cm": 3.2 }
  ],
  "montage_positions": [
    {
      "position": "Oz",
      "medelopt": "LED1",
      "dist_to_cz_cm": 21,
      "dist_to_middle_of_curve_cm": 11.4,
	  "pos2D_X_mm": -85.0,
	  "pos2D_Y_mm": 85.0,
	  "pos3D_X_mm": -45.3,
	  "pos3D_Y_mm": 62.26,
	  "pos3D_Z_mm": -9.39,
    },
    {
      "position": "POz",
      "medelopt": "DET1",
      "dist_to_cz_cm": 21,
      "dist_to_middle_of_curve_cm": 11.4
    },
    {
      "position": "Iz",
      "medelopt": "DET2",
      "dist_to_cz_cm": 21,
      "dist_to_middle_of_curve_cm": 11.4
    },
    {
      "position": "O1",
      "medelopt": "DET3",
      "dist_to_cz_cm": 21,
      "dist_to_middle_of_curve_cm": 11.4
    },
    {
      "position": "O2",
      "medelopt": "DET4",
      "dist_to_cz_cm": 21,
      "dist_to_middle_of_curve_cm": 11.4
    },
    {
      "position": "P7",
      "medelopt": "LED2",
      "dist_to_cz_cm": 21,
      "dist_to_middle_of_curve_cm": 11.4
    },
    {
      "position": "P9",
      "medelopt": "DET5",
      "dist_to_cz_cm": 21,
      "dist_to_middle_of_curve_cm": 11.4
    },
    {
      "position": "P5",
      "medelopt": "DET6",
      "dist_to_cz_cm": 21,
      "dist_to_middle_of_curve_cm": 11.4
    },
    {
      "position": "PO7",
      "medelopt": "DET7",
      "dist_to_cz_cm": 21,
      "dist_to_middle_of_curve_cm": 11.4
    },
    {
      "position": "P1",
      "medelopt": "LED3",
      "dist_to_cz_cm": 21,
      "dist_to_middle_of_curve_cm": 11.4
    },
    {
      "position": "P3",
      "medelopt": "DET8",
      "dist_to_cz_cm": 21,
      "dist_to_middle_of_curve_cm": 11.4
    },
    {
      "position": "PO3",
      "medelopt": "DET9",
      "dist_to_cz_cm": 21,
      "dist_to_middle_of_curve_cm": 11.4
    },
    {
      "position": "Pz",
      "medelopt": "DET10",
      "dist_to_cz_cm": 21,
      "dist_to_middle_of_curve_cm": 11.4
    },
    {
      "position": "PO8",
      "medelopt": "LED4",
      "dist_to_cz_cm": 21,
      "dist_to_middle_of_curve_cm": 11.4
    },
    {
      "position": "PO4",
      "medelopt": "DET11",
      "dist_to_cz_cm": 21,
      "dist_to_middle_of_curve_cm": 11.4
    },
    {
      "position": "P2",
      "medelopt": "DET12",
      "dist_to_cz_cm": 21,
      "dist_to_middle_of_curve_cm": 11.4
    },
    {
      "position": "P4",
      "medelopt": "DET13",
      "dist_to_cz_cm": 21,
      "dist_to_middle_of_curve_cm": 11.4
    },
    {
      "position": "P6",
      "medelopt": "DET14",
      "dist_to_cz_cm": 21,
      "dist_to_middle_of_curve_cm": 11.4
    },
    {
      "position": "P8",
      "medelopt": "DET15",
      "dist_to_cz_cm": 21,
      "dist_to_middle_of_curve_cm": 11.4
    },
    {
      "position": "P10",
      "medelopt": "DET16",
      "dist_to_cz_cm": 21,
      "dist_to_middle_of_curve_cm": 11.4
    }
  ]
}
    
