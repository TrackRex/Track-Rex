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

   Function: A short script for users to quickly review the data, and obtain parameters to start the matching process.

4. Script 2:  [**Match**](https://github.com/TrackRex/Track-Rex/blob/main/2.Match.md)

   Function: The core section, by which two in-situ EBSD maps are correlated, results will be used for further tracking.

5. Script 3: [**Track**](https://github.com/TrackRex/Track-Rex/blob/main/3.Track.md)

   Function: After each two following maps are matched, run this to track all grains through the whole dataset.

All scripts work with [MATLAB](https://uk.mathworks.com/products/matlab.html) and [MTEX](https://mtex-toolbox.github.io/index). To [install MATLAB](https://login.mathworks.com/embedded-login/landing.html?cid=getmatlab&s_tid=gn_getml) you need firstly obtain a license (check if your organization provides one), and then follow the instructions. To [install MTEX](https://mtex-toolbox.github.io/download), please make sure the right version is deployed, we now supporting **_mtex-6.0.beta3_**.

# Now master Track-Rex by following this demonstration

Seven EBSD maps recording grains information of an Mg alloy from deformed state to fully recrystallized state are provided, [download](https://sotonac-my.sharepoint.com/:f:/g/personal/hy1v22_soton_ac_uk/EspZ87_7f1lDpcOm3537Q3kBsKB2qeoj4U2CkR0WyjqAlw?e=nyAZmb), a glance of the dataset:

![DemoDataSet](https://github.com/TrackRex/Track-Rex/assets/161822160/1e3f8b30-05c4-4b36-8d70-7690bea3697a)

Please first read through the rest of this demonstration, which will show how Track-Rex works and then you can run the scripts yourself, either with our example dataset or your own datasets. Note that to track all grains above, it took roughly 2.5 hours on a 13th Gen Intel(R) Core(TM) i9-13900K PC. In case this dataset is too large to handle, use a small subset [_**Samll_region_data.zip**_](https://github.com/TrackRex/Track-Rex/blob/main/Small_region_data.zip) containing 900 grains, which should be able to handle easily.

## 1. Checking

Before matching two EBSD maps, review the data first to get the parameters you need: 

i. **Reference Grain**: a grain exists in both two maps, note its IDs.

ii. **Misangle Threshold**: below which misorientation 2 grains will be matched, adjust by the texture difference you observe.

iii. **Searching Range**: search box length (µm) in EBSD2, adjust by the grain size you observe.

To check MG_5 & MG_6 for example, open Matlab and start MTEX, run [**Check**](https://github.com/TrackRex/Track-Rex/blob/main/1.Check.md) and give the input:

Path to EBSD1: _path_/MG_5.crc (_**replace with your path to ZE_5.crc**_);

Path to EBSD2: _path_/MG_6.crc (_**replace with your path to ZE_6.crc**_);

![check](https://github.com/TrackRex/Track-Rex/assets/161822160/8c9c450e-df22-498a-a7c2-0579460c6942)

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

![MG_5   MG_6](https://github.com/TrackRex/Track-Rex/assets/161822160/7136a795-9584-4c2f-9af2-cec7ed41eff7)

![Match_Results](https://github.com/TrackRex/Track-Rex/assets/161822160/df573239-d8c3-40f4-8714-a7d09daec51f)

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

![Track_Result](https://github.com/TrackRex/Track-Rex/assets/161822160/e280df31-04df-4bce-9e71-fe0b03e2c520)

Example 2: Tracking the origination of all grains in MG_7

![Vertical Tracking](https://github.com/TrackRex/Track-Rex/assets/161822160/7c5c3c96-97f7-4ac6-b757-f22f66b83d0c)

![vertical_Tracking_2](https://github.com/TrackRex/Track-Rex/assets/161822160/851156d6-290c-4d77-98da-424bcd6f3cca)

All figures will be saved under _D:/Track_Rex_Temp_. Now take a look at **Workspace**, tracking results stored in variables called _Track_x_, for example in _Track_1_:

![IMG_9](https://github.com/TrackRex/Track_Rex/assets/161822160/fefe1162-6fc6-4974-a4e7-bd1ad5a7e69b)

Now save the workspace together with figures and archive. All grains appeared in the _MG_1_ to _MG_7_ quasi-in-situ dataset has been tracked.

## Give it a go by yourself

Now with Track_rex at your service, try tracking 900 grains within this set of ebsd data, files can be find in the main branch _**Samll_region_data.zip**_

![IMG_10](https://github.com/TrackRex/Track_Rex/assets/161822160/87650bb6-60d6-495b-96ad-c21ad98814f5)

