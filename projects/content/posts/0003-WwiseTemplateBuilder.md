---
title: "Wwise+Wwapi - WwiseTemplateBuilder Script"
description: "A WAAPI script for importing audio into a pre-existing Wwise template"
date: 2024-12-01
draft: true
tags: ["Wwise", "WWAPI", "Template", "Templates", "Audiokinetic", "Audio", "Sound"]
cover:
    image: "/images/0003-WwiseTemplateBuilder/07-WTBScreenshot.png"
summary: "A WAAPI script for importing audio into a pre-existing Wwise template"
---

**WwiseTemplateBuilder** is a command add-on tool written in Python for importing audio into a pre-existing Wwise templates for easy and consistent setup of actor-mixer structures and events. The tool allows users to streamline the process of setting up complex Wwise project structures, making it easier to manage consistent audio implementation across large-scale Wwise projects.

- Do you find yourself building similar structures over and over again in Wwise? 
- Do you work with large amount of content that is set up in a similar way (skins, foley, materials)? 
- Do you work with an awesome team of audio folks who need more time to focus on creating great sound design and not waste time setting up large or complex Wwise structures?

Instead you can point this tool at a template Wwise structure, a destination location in Wwise, and your folder of files. WwiseTemplateBuilder will recreate the actor-mixer/event structure in Wwise, then intelligently scan the file names and place them accordingly in the mixer structure. The tool does rely on the file naming to be the same as the intended template for placement of the audio in the actor-mixer structure.

### Why not just use the template feature built into Wwise when importing audio?
- Events! Not just for the actor-mixer setup, events can be templated to complete a full setup
- Doesn't require saving files in particular folders
- Doesn't require manual mapping audio files to Wwise structure 
- Doesn't require the use of a particular DAW
- Uses file name matching to find proper location for audio in template actor-mixer structure

## OVERVIEW VIDEO
{{< youtube 1_J7osMAB8Q >}}


## Features
- **Actor-Mixer Templates**: Create new actor-mixer structures based on re-usable template
- **Event Templates**: Event templates can reference actor-mixer templates to complete a full setup
- **String Replacement**: Find and replace strings in templates with user-specified values
- **Create Template in Wwise**: Create as many templates as needed directly in Wwise

## INSTALLATION VIDEO
{{< youtube n6-XA2kPW9M >}}
## Installation
1. Install Python 3.8+ -  Download at https://www.python.org/downloads/
2. Download the WwiseTemplateBuilder_v01 release at https://github.com/LathamAudio/WwiseTemplateBuilder/releases/tag/v0.1
3. Unzip 'Add-Ons' folder to Wwise project folder
4. Run **'Add-Ons\Scripts\WwiseTemplateBuilder\InstallDependencies.bat'** to install python dependencies like pss-pywaapi
5. Ensure WAAPI is enabled in Wwise (should be setup by default):
	1. Open Wwise.
	2. Go to **User Preferences**
	3. Enable **WAAPI** and confirm the WAMP port is set to 8080 (can be changed in the script on line 608 in main.pyw)

## Usage
1. **Run the Script**:
	- In Wwise, choose "WwiseTemplateBuilder" from the Scripts pulldown menu

2. **Choose Source Template**:
	- In Wwise select the actor-mixer structure that will act as the template
	- In the WwiseTemplateBuilder tool press the 'Select Source' button to set the path to the source template

3. **Choose Destination Location**:
	- In Wwise select the actor-mixer object that will act as the destination for the template (typically a folder or work unit)
	- In the WwiseTemplateBuilder tool press the 'Select Destination' button to set the path to the detination location

4. Select WAV assets
	- Press the 'Select Folder' button in the WwiseTemplateBuilder tool and select the folder of audio assets to import in to the template actor-mixer structure

5. Set the Find & Replace strings
	- In the 'Find' field type the string that will be replaced in the template name
	- In the 'Replace' field type the string that will replace the find string in the template name
	- The application will automatically replace instances of find string in the template names and paths with the replace string, adapting them to your project structure.

6. Preview template
	- Pressing the 'Preview Template' button populates the preview pane below with a preview of how the template will look in Wwise
	- This will show a preview of the actor-mixer structure will the new names and placement of audio assets in the structure

7. Generate Template
	- Pressing the 'Generate Template' button will create the new actor-mixer structure in the destination location that matches the original source structure. The find string will be replaces with the provided replace string. The audio assets are imported into Wwise and placed into the matching actor-mixer structure locations.

8. **Event Template**:
	- Switch to the 'Events' tab to use event templates for that reference the actor-mixer templates
	- Select the location of the source event template in Wwise and press 'Select Source'
	- Select the location of the destination event template in Wwise and press 'Select Destination'
	- Select the destination location of target actor-mixer in Wwise and press 'Select Actor-Mixer', this will set the destination actor-mixer as the target of the event actions instead of the original template to replace the defaults set
	- Set the same find & replace strings to replace in the events and actions
	- Pressing 'Preview Template' with show a preview of the event template before generation
	- Pressing 'Generate Template' will create the resulting event structure in Wwise, replacing any instance of the `TEMPLATE` string found, and re-targeting event actions to the destination template actor-mixer structure

## Contributing

Contributions are welcome! If you’d like to help improve WwiseTemplateBuilder, please follow these steps:

1. Fork the repository.
2. Create a new branch with a descriptive name.
3. Make your changes and submit a pull request.


## License

This project is licensed under the MIT License

## Acknowledgements

- Special thanks to 
	- **Audiokinetic** for Wwise and WAAPI.
	- Simon Gumbleton for [pss_pywaapi](https://github.com/some_repo), a Python-WAAPI integration.

