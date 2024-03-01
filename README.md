# This toolkit contains scripts for our work in "Track-Rex: a universal toolbox for tracking recrystallization nucleation and grain growth behaviors in polycrystalline materials", Journal of Materials Science & Technology, by Xun Zeng, Haoran Yi, Dikai Guan (paper link).

We acknowledge all peer researchers whose excellent work has made this toolbox possible, especially MATLAB and MTEX. This toolkit is dedicated to realize the tracking of every single grain within a large in-situ Electron Backscatter Diffraction(EBSD) dataset, which usually contains thousands of grains. Applying this toolkit will greatly reduce data processing time, from several months to one or two days and does not require user interaction during running. Moreover, both statistical tracking results of all grains (for the very first time) and individual tracking of grain with interest can be obtained easily, enabling a range of further analysis. The application scenario in our paper is to investigate recrystallization and grain growth behaviors within two Magnesium alloys, notice that usage of the toolbox should apply to a broader range of polycrystalline materials where in-situ EBSD scan could boost research advancement.

Contact us at Track-rex@soton.ac.uk for general enquiries and potential collaboration.

## Instructions & Setting up

All scripts work with [MATLAB](https://uk.mathworks.com/products/matlab.html) and [MTEX](https://mtex-toolbox.github.io/index). To [install MATLAB](https://login.mathworks.com/embedded-login/landing.html?cid=getmatlab&s_tid=gn_getml) you need firstly obtain a license (check if your organization provides one), and then follow the instructions. To [install MTEX](https://mtex-toolbox.github.io/download), please read the link and make sure the right version is deployed, we now supporting **mtex-6.0.beta2**. The whole toolbox is divided into three parts, as follows:

1. Script 1: '**Check**'.

   A short script for users to quickly review the data, and obtain the parameters for starting the matching process.

4. Script 2: '**Match**'.

   The core section, by which two in-situ EBSD maps are correlated, results will be used for further tracking.

5. Script 3: '**Track**'.

   After each two following maps are matched, run this to track all grains through the whole dataset.

## Demonstration

Now start playing with Track_Rex by following this demonstration, data and scripts can be found in this repository, this will take about 2 hours.

Download data files from ZE_1.ctf.zip to ZE_8.ctf.zip, unzip all and store in a local path. Below is a glance of the dataset, all the grains will be tracked in this demonstration.

+ ZE_1		as-rolled		1648grains
+ ZE_2		420℃ 5min		4984grains
+ ZE_3		420℃ 10min		4228grains
+ ZE_4		420℃ 16min		4024grains
+ ZE_5		420℃ 24min		3081grains
+ ZE_6		420℃ 35min		2556grains
+ ZE_7		420℃ 50min		2438grains
+ ZE_8		420℃ 80min		1906grains

### 1. Checking

Open Matlab and start MTEX, copy all lines in '**Check.txt**' into the command window then press Enter. Script will ask for path to EBSD1 & EBSD2, here let's check ZE_4 & ZE_5, by giving:

Path to EBSD1: _path_/ZE_4.ctf (_**replace with your path to ZE_4.ctf**_)

Path to EBSD2: _path_/ZE_5.ctf (_**replace with your path to ZE_5.ctf**_)

You should see two figures with dense grains ID labels, figure1 is EBSD1 (ZE_4 here), figure2 is EBSD2 (ZE_5 here).

When checking data, first find a grain to act as the reference grain for matching, here we use grain 954 in ZE_4 & grain 810 in ZE_5. Then review two maps from the aspect of grain size and orientation, this will help deciding matching parameters.

![IMG_1](https://github.com/HaoranYi1996/Track_Rex/assets/94325739/e42a87f6-d7d1-4d29-a085-6413e3e1f192)

### 2. Matching

After checking, run a line of '**clear all;clc**' to clean variables. Then copy all lines in '**Match.txt**' into the command window and press Enter, script will ask for user inputs, here let's match ZE_4 & ZE_5, by giving:

Path to EBSD1: _path/ZE_4.ctf_ (**replace with your path to ZE_4.ctf**)

Path to EBSD2: _path/ZE_5.ctf_ (**replace with your path to ZE_5.ctf**)

Starting Grain in EBSD1: _954_ (reference grain id in ZE_4)

Starting Grain in EBSD2: _810_ (reference grain id in ZE_5)

Misangle Threshold: _5_ (two grains with angle difference below this threshold will be matched, adjust by the level of orientation difference you observe when checking data)

Searching Range: _50_ (the search box length (µm) in EBSD2, adjust by the average grain size you observe when checking data)

After giving the above parameters, you should see the calculation process running for several minutes (depending on the size of your data)

![Workflow](https://github.com/HaoranYi1996/Track_Rex/assets/94325739/4fa06823-488e-487f-9fee-bb23798f0e8e)

When the calculation finishes, results will be plotted automatically, including grain size distribution and orientation

![IMG_2](https://github.com/HaoranYi1996/Track_Rex/assets/94325739/2cac666b-6936-43f1-85e6-f0246ee0886a)

![IMG_3](https://github.com/HaoranYi1996/Track_Rex/assets/94325739/dceb307f-c904-4cdf-830a-5b66c72ad649)
![IMG_4](https://github.com/HaoranYi1996/Track_Rex/assets/94325739/622c44e2-4fd6-4788-8f45-67d65b5eb6bd)

All figures will be saved under _D:/Track_Rex_Temp_. Now take a look at **Workspace**, Three important variables containing matched results here are:

![IMG_5](https://github.com/HaoranYi1996/Track_Rex/assets/94325739/004cac32-982a-4adf-b071-955ea10f5b15)

The last step here is, saving the variables for tracking, here we need:

_**AllGrains**_ to be saved as _**A4_5**_

_**ebsd2_New**_ as _**N_5**_

Then save the workspace together with figures and archive all, empty _D:/Track_Rex_Temp_ folder. Now try to match each two following maps and save the variables for tracking.

### 3. Tracking

Run '**clear all;clc**' then import all matching results, _A1_2_ to _A7_8_ and _N_2_ to _N_8_, the work space should looks like the image below. In case you have not finished all matching yet, just download _**ReadytoTrack.mat**_.

![IMG_6](https://github.com/HaoranYi1996/Track_Rex/assets/94325739/b5bb2f70-00de-482f-9a57-96a0a1b1b2fa)

Now copy all lines in '**Track.txt**' into the command window and press Enter, script will ask for pathes to all 8 files:

Path to EBSD1: _path_/ZE_1.ctf    (**replace with your path to ZE_1.ctf**)

Path to EBSD2: _path_/ZE_2.ctf    (**replace with your path to ZE_2.ctf**)

Path to EBSD3: _path_/ZE_3.ctf    (**replace with your path to ZE_3.ctf**)

Path to EBSD4: _path_/ZE_4.ctf    (**replace with your path to ZE_4.ctf**)

Path to EBSD5: _path_/ZE_5.ctf    (**replace with your path to ZE_5.ctf**)

Path to EBSD6: _path_/ZE_6.ctf    (**replace with your path to ZE_6.ctf**)

Path to EBSD7: _path_/ZE_7.ctf    (**replace with your path to ZE_7.ctf**)

Path to EBSD8: _path_/ZE_8.ctf    (**replace with your path to ZE_8.ctf**)

Tracking process will start automatically, taking about 90 minutes. Notice the time may change base on data size & PC specifications.

When finished, results will be plotted:

Example 1: Tracking all recrystallized grains 'born' in ZE_2 (blue colour grains) 

![IMG_7](https://github.com/HaoranYi1996/Track_Rex/assets/94325739/150c43b1-b5a5-4350-a723-31a02afd6168)

Example 2: Tracking the origination of all grains in ZE_8

![IMG_8](https://github.com/HaoranYi1996/Track_Rex/assets/94325739/06b2f143-5d23-4532-94d0-8f0a45db518b)

![IMG_9](https://github.com/HaoranYi1996/Track_Rex/assets/94325739/0727c7b5-20ef-4dde-b11b-a8dd88d1e7d4)

All figures will be saved under _D:/Track_Rex_Temp_. Now take a look at **Workspace**, tracking results stored in variables called _Track_x_, for example in _Track_1_:

![IMG_10](https://github.com/HaoranYi1996/Track_Rex/assets/94325739/9edeeed9-9f6b-4440-9bfd-9a05e4cc8779)

Now save the workspace together with figures and archive. All grains appeared in the _ZE_1_ to _ZE_8_ quasi-in-situ dataset has been tracked.
