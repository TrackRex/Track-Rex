# How to cite this work for your future publications:

Please cite our open-access paper below:

Xun Zeng, Haoran Yi, Zhuoran Zeng, Liang Yuan, Sangbong Yi, Junheng Gao, Mark Rainforth, Dikai Guan, Track-Rex: a universal toolbox for tracking recrystallization nucleation and grain growth behaviors in polycrystalline materials, Journal of Materials Science & Technology (2024), https://doi.org/10.1016/j.jmst.2024.02.013.

We acknowledge all peer researchers whose excellent work has made this toolbox possible, especially MATLAB and MTEX. This toolkit is dedicated to realize the tracking of every single grain within a large in-situ Electron Backscatter Diffraction(EBSD) dataset, which usually contains thousands of grains. Applying this toolkit will greatly reduce data processing time, from several months to one or two days and does not require user interaction during implementation. Moreover, both statistical tracking results of all grains (for the very first time) and individual tracking of grain with interest can be obtained easily, enabling a range of further analysis. The application scenario in our paper is to investigate recrystallization and grain growth behaviors within two Magnesium alloys, notice that usage of the toolbox should apply to a broader range of polycrystalline materials where in-situ EBSD approaches could boost research advancement.

# Contact us:

General enquiries and questions: track-rex@soton.ac.uk

Potential collaborations: dikai.guan@soton.ac.uk 

# See our video instructions

_**Intro: What is Track-Rex**_ [Youtube](https://www.youtube.com/watch?v=hkKFDYwRhTQ) [Bilibili](https://www.bilibili.com/video/BV1mv421r77j)

_**Video1: Double Match**_ [Youtube](https://www.youtube.com/watch?v=_GstKJvMVOc) [BiliBili](https://www.bilibili.com/video/BV1YK421t7Na)

_**Video2: Tracking All**_ [Youtube](https://www.youtube.com/watch?v=VfS-a9o_TUI) [Bilibili](https://www.bilibili.com/video/BV1ix4y1C76C)

_**Video3: Specific Tracking**_ [Youtube](https://www.youtube.com/watch?v=_l_4D8OAZRc) [Bilibili](https://www.bilibili.com/video/BV1Ex4y1r7eF)

# Instructions & Setting up

We divide Track-Rex into three scripts, click the link below and you can find **annotated code** as well as **running instructions**.

1. Script 1: [**Check**](https://github.com/TrackRex/Track-Rex/blob/main/1.Check.md)

   A short script for users to quickly review the data, and obtain parameters to start the matching process.

4. Script 2:  [**Match**](https://github.com/TrackRex/Track-Rex/blob/main/2.Match.md)

   The core section, by which two in-situ EBSD maps are correlated, results will be used for further tracking.

5. Script 3: [**Track**](https://github.com/TrackRex/Track-Rex/blob/main/3.Track.md)

   After each two following maps are matched, run this to track all grains through the whole dataset.

All scripts work with [MATLAB](https://uk.mathworks.com/products/matlab.html) and [MTEX](https://mtex-toolbox.github.io/index). To [install MATLAB](https://login.mathworks.com/embedded-login/landing.html?cid=getmatlab&s_tid=gn_getml) you need firstly obtain a license (check if your organization provides one), and then follow the instructions. To [install MTEX](https://mtex-toolbox.github.io/download), please make sure the right version is deployed, we now supporting **_mtex-6.0.beta3_**.

# Now master Track-Rex by following this demonstration

Seven EBSD maps recording grains information of an Mg alloy from deformed state to fully recrystallized state are provided, [download](https://sotonac-my.sharepoint.com/:f:/g/personal/hy1v22_soton_ac_uk/EspZ87_7f1lDpcOm3537Q3kBsKB2qeoj4U2CkR0WyjqAlw?e=nyAZmb), below is a glance of the dataset:

![DemoDataSet](https://github.com/TrackRex/Track-Rex/assets/161822160/1e3f8b30-05c4-4b36-8d70-7690bea3697a)

Now start playing with Track_Rex by following this demonstration, data and scripts can be found in this repository, this will take about 2 hours, note that we run this using a 13th Gen Intel(R) Core(TM) i9-13900K PC.

If you computer does not have a high specification or you want to have a quick run/test, please use a dataset consisting of only 900 grains and this will only take about 30 minutes, files can be find in the main branch _**Samll_region_data.zip**_

### 1. Checking

Open Matlab and start MTEX, copy all lines in '**Check.txt**' into the command window then press Enter. Script will ask for path to EBSD1 & EBSD2, here let's check MG_5 & MG_6, by giving:

Path to EBSD1: _path_/MG_5.crc (_**replace with your path to ZE_5.crc**_)

Path to EBSD2: _path_/MG_6.crc (_**replace with your path to ZE_6.crc**_)

You should see two figures with dense grains ID labels, figure1 is EBSD1 (MG_5 here), figure2 is EBSD2 (MG_6 here).

When checking data, first find a grain to act as the reference grain for matching, here we use grain 3660 in ZE_5 & grain 2110 in ZE_6. Then review two maps from the aspect of grain size and orientation, this will help deciding matching parameters.

![IMG_1](https://github.com/TrackRex/Track_Rex/assets/161822160/932f231f-d6fd-45f3-a791-2e578cdc0980)

### 2. Matching

After checking, run a line of '**clear all;clc**' to clean variables. Then copy all lines in '**Match.txt**' into the command window and press Enter, script will ask for user inputs, here let's match MG_5 & MG_6, by giving:

Path to EBSD1: _path/MG_5.crc_ (**replace with your path to MG_5.crc**)

Path to EBSD2: _path/MG_6.crc_ (**replace with your path to MG_6.crc**)

Starting Grain in EBSD1: _3660_ (reference grain id in MG_5)

Starting Grain in EBSD2: _2110_ (reference grain id in MG_6)

Misangle Threshold: _5_ (two grains with angle difference below this threshold will be matched, adjust by the level of orientation difference you observe when checking data)

Searching Range: _50_ (the search box length (µm) in EBSD2, adjust by the average grain size you observe when checking data)

After giving the above parameters, you should see the calculation process running for several minutes (depending on the size of your data)

![Workflow](https://github.com/TrackRex/Track_Rex/assets/161822160/c1757a20-0401-4c7d-9b85-558c29600195)

When the calculation finishes, results will be plotted automatically, including grain size distribution and orientation

![IMG_2](https://github.com/TrackRex/Track_Rex/assets/161822160/8a70327c-0e94-453c-bc5f-7fd8ddc193b7)

![IMG_3](https://github.com/TrackRex/Track_Rex/assets/161822160/8211aba2-6482-4ed6-8989-bfe16cdba542)

All figures will be saved under _D:/Track_Rex_Temp_. Now take a look at **Workspace**, Three important variables containing matched results here are:

![IMG_4](https://github.com/TrackRex/Track_Rex/assets/161822160/ca2d8a9f-74ef-484d-a2d4-3e02539fd8f7)

The last step here is, saving the variables for tracking, here we need:

_**AllGrains**_ to be saved as _**A6_5**_

Then save the workspace together with figures and archive all, empty _D:/Track_Rex_Temp_ folder. Now try to match each two following maps and save the variables for tracking.

### 3. Tracking

Run '**clear all;clc**' then import all matching results, _A2_1_ to _A7_6_, the workspace should look like the image below. In case you have not finished all matching yet, just download _**Ready_to_Track.mat**_.

![IMG_5](https://github.com/TrackRex/Track_Rex/assets/161822160/26084bc2-91a7-4b69-b387-dc0d298fc815)

Now import _**Ready_to_Track.mat**_ worksheet then copy all lines in '**Track.txt**' into the command window and press Enter,

Tracking process will start automatically, taking about 140 minutes. Notice the time may change based on data size & PC specifications.

When finished, results will be plotted:

Example 1: Tracking all recrystallized grains 'born' in MG_2

![IMG_6](https://github.com/TrackRex/Track_Rex/assets/161822160/49a15b47-5c0e-433f-816d-35381207f825)

Example 2: Tracking the origination of all grains in MG_7

![IMG_7](https://github.com/TrackRex/Track_Rex/assets/161822160/4af38204-0bf6-4d38-8b95-7a59b13e2069)

![IMG_8](https://github.com/TrackRex/Track_Rex/assets/161822160/d35ebba4-5edc-4b8f-8c44-c565b535c900)

All figures will be saved under _D:/Track_Rex_Temp_. Now take a look at **Workspace**, tracking results stored in variables called _Track_x_, for example in _Track_1_:

![IMG_9](https://github.com/TrackRex/Track_Rex/assets/161822160/fefe1162-6fc6-4974-a4e7-bd1ad5a7e69b)

Now save the workspace together with figures and archive. All grains appeared in the _MG_1_ to _MG_7_ quasi-in-situ dataset has been tracked.

## Give it a go by yourself

Now with Track_rex at your service, try tracking 900 grains within this set of ebsd data, files can be find in the main branch _**Samll_region_data.zip**_

![IMG_10](https://github.com/TrackRex/Track_Rex/assets/161822160/87650bb6-60d6-495b-96ad-c21ad98814f5)

