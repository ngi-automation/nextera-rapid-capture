# Automated Nextera Rapid Capture Installation Guide #
**For Agilent NGS Workstation Option B**

## Contents ##
1. [Description](#Description)
2. [Requirements](#requirements)
3. [Installation](#installation)
4. [Protocol](#protocol)
5. [License](#license)

## Description ##
This document describes how to set up the automated Nextera Rapid Capture protocol for the Agilent NGS Workstation created at NGI Stockholm.

## Requirements ##
- Agilent NGS Workstation :warning: <i><b>Option B only</i></b>
- Consumables
   - Eppendorf twin.tec 96 PCR plate (Eppendorf, cat# 0030 128.672 (int); 951020460 (US))
   - Nunc deepwell 1.3 mL plate (Thermo Scientific, cat# 260251)
   - ABgene 2.2 mL storage plate Mk.II (Thermo Scientific, cat# # AB-0933)
- Deepwell plate adaptor on position 6 (Agilent Technologies, cat# G5498B#012) and supporting device file
- Labware definitions*
- Liquid classes definition*

\* provided in `all_labware_liquids.vzp`

#### Included files ####
```
nextera.pro
nextera_capture_elute.pro
nextera_capture_hyb.pro
nextera_capture_runset.rst
nextera_capture_wash.pro
nextera_form.VWForm
nextera_intermission1.pro
nextera_intermission2.pro
nextera_intermission3.pro
all_labware_liquids.vzp
nextera_pcr.pro
nextera_runset.rst
nextera_script.js
nextera_spri.pro
resources/1313497192_media_controls_light_pause.png
resources/1313497517_media_controls_light_play.png
resources/clear_inventory.bat
resources/clear_inventory.sql
```

## Installation ##
### Download files ###


##### Using Git #####
Clone into `https://github.com/ngi-automation/nextera-rapid-capture.git` from the `Protocol Files` directory:

```bash
cd "C:\VWorks Workspace\Protocol Files"
git clone https://github.com/ngi-automation/nextera-rapid-capture.git
```

Alternatively, download the compressed folder from:
[`https://github.com/ngi-automation/nextera-rapid-capture/archive/master.zip`][zip]
and extract to `C:\VWorks Workspace\Protocol Files`. Rename the resulting `nextera-rapid-capture-master` folder to `nextera-rapid-capture`. The path to the folder containing the extracted files should then be `C:\VWorks Workspace\Protocol Files\nextera-rapid-capture`.

### Configure ###
#### Labware and and liquid class definitions ####
Use the import feature in VWorks from `File › Import`in the toolbar and select the `all_labware_liquids.vzp` file included. See the [VWorks Knowledge Base][import] for more information.

#### Device files ####
Device files and profiles are system specific and will not be provided. Two different Bravo configurations are used in the NRC protocols (one being the "standard" configuration):

##### Standard configuration #####
Position | Type | Part#
-------: | ---- | -----
1&ndash;3, 8  | Deck Platepad | G5498b#004
4, 6     | Peltier Thermal Station (Inheco) | G5498b#021
5        | Orbital Shaking Station | G5498b#033
7        | Magnetic Bead Accessory | G5498b#008
9        | Thermal Station (ThermoCube) | G5498b#036/7/8

##### Capture configuration #####
Same as above but with the following modification:

Position | Type | Part#
-------: | ---- | -----
6        | Thermal Station w Deepwell Plate Insert | G5498b#012

For reference see Agilent's [accessories catalog][catalog] for the Bravo.

Each `.pro` file must have the correct device file set:

Protocol file | Device file
-------- | -----------
`nextera.pro` | Standard
`nextera_pcr.pro` | Standard
`nextera_spri.pro` | Standard
`nextera_capture_hyb.pro` | Standard
`nextera_capture_wash.pro` | Capture
`nextera_capture_elute.pro` | Capture
`nextera_intermisson1.pro` | Standard
`nextera_intermission2.pro` | Standard
`nextera_intermission3.pro` | Standard

See the [VWorks Knowledge Base][device-file] for more information on how to select the device file.

## Protocol ##

See the NGI Stockholm/SciLifeLab [Standard Operating Procedure][sop].

## License ##
> Licensed under the Apache License, Version 2.0 (the "License");
> you may not use this file except in compliance with the License.
> You may obtain a copy of the License at
> 
> http://www.apache.org/licenses/LICENSE-2.0
>
> Unless required by applicable law or agreed to in writing, software
> distributed under the License is distributed on an "AS IS" BASIS,
> WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
> See the License for the specific language governing permissions and limitations under the License.

The full license can also be found in the file LICENSE and must included when redistributing the software.

If this method is used to generate results for publication we ask that you include a reference to this repository, something like:
```
Automation protocols made available by NGI Sweden at https://github.com/ngi-automation/nextera-rapid-capture
```
*VWorks Automation Control*, *Bravo* and other things relating to the *Agilent NGS Workstation* are trademarks owned by Agilent Technologies, Inc. (Santa Clara, CA 95052-8058, US).

*Nextera Rapid Capture* is a trademark owned by Illumina, Inc. (San Diego, CA 92122 US)

[email]: mailto:joel.gruselius@scilifelab.se "E-mail author"
[ngi]: https://portal.scilifelab.se/genomics/ "NGI Stockholm"
[scilife]: http://www.scilifelab.se/platforms/ngi/ "SciLifeLab"
[zip]: https://github.com/ngi-automation/nextera-rapid-capture/archive/master.zip
[import]: http://www.velocity11.com/techdocs/AutomationSolutionsKB/vworks4_ug/11_Troubleshooting.15.03.html#2005458
[catalog]: http://www.chem.agilent.com/Library/catalogs/Public/5991-0369EN.pdf
[sop]: http://goo.gl/UAMdzX
[device-file]: http://www.velocity11.com/techdocs/AutomationSolutionsKB/vworks4_ug/02_CreateProtocolBasic.04.08.html#1981042

---

>[National Genomics Infrastructure][ngi] at [SciLifeLab][scilife]  
<joel.gruselius@scilifelab.se>  
May 2014
