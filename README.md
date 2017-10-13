# **Finding Lane Lines on the Road** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

Overview
---

This is the first project of the Udacity "Self-Driving Car" Nanoprogram. In this project you are required to detect lane lines in images using Python 3 and OpenCV. I learned a lot as a roboticist with Mechanical Engineering background. This document will cover the usage instruction, a quick reflection of the project, and solutions for software setting issues. 

Usage Instruction
---

The project requirement can be found at [CarND-LaneLines-P1](https://github.com/udacity/CarND-LaneLines-P1). For my package, the folders are test and output images and videos: [solidWhiteRight.mp4](https://www.youtube.com/watch?v=ZqoLk4JHO7Y&list=PLKZsN6T-bc0avfBON7t6g9R70T2f4AuCn&index=1) and [solidYellowLeft.mp4](https://www.youtube.com/watch?v=Tua2K579PuA&list=PLKZsN6T-bc0avfBON7t6g9R70T2f4AuCn&index=2). [P1.ipynb](https://github.com/jwangjie/SDC-LaneLines-P1/blob/master/P1.ipynb) is the final notebook file, [P1_first.ipynb](https://github.com/jwangjie/SDC-LaneLines-P1/blob/master/P1_first.ipynb) is the techniques review and first attempt, and [P1_second.ipynb](https://github.com/jwangjie/SDC-LaneLines-P1/blob/master/P1_second.ipynb) is the images test only and the second attempt. 

Reflection 
---

An OpenCV based vision pipeline was developed for detecting lane lines and then drawing averaged boundary lines in the road videos. The pipeline can be developed and tested by the images in the "test_images" first. Then videos in the "test_videos" folder can be processed. In the pipeline development, color selection, Gaussian blurring, Canny edge detection, region of interest selection, and Hough transform line detection techniques were used. 

The built pipeline works fine for straight white and yellow line detections, but doesn't work for curved lines. This is due to the fact that the used "draw_lines()" method assuming the lane lines were linear. Moreover, even replacing the line drawing method, the "region_of_interest()" may loss normal functions for the steep roads. 

In order to work for the curved and steep road lane detections, more advanced and adaptive region of interest selection technique need to be applied. 

Software Setting Issues
---

This section cover solutions for the software settings problems I met before I started programming. All solutions are for Windows. 

**Step 1:** Set up the [CarND Term1 Starter Kit](https://github.com/udacity/CarND-Term1-Starter-Kit/blob/master/README.md)

The miniconda never installed properly using the provided link, so I downed the full version of [Anaconda](https://www.anaconda.com/download/). The Udacity course [Anaconda and Jupyter Notebooks](https://classroom.udacity.com/courses/ud1111) is useful for quick review, you got the basic feeling about went through the materials. 

After installing [Anaconda](https://www.anaconda.com/download/), I got totally confused by the following instructions. I did some search and found a guy with similar difficulties: [The Anaconda installation guide is so confusing](https://discussions.udacity.com/t/the-anaconda-installation-guide-is-so-confusing/312695). Based on the answers and my own trial and error, I summarized the following steps: 

1. Install the [Git](https://git-scm.com/downloads), open "Git CMD", clone the environment by pasting "git clone https://github.com/udacity/CarND-Term1-Starter-Kit.git"  
2. Open "Anaconda Prompt", navigate to the "CarND-Term1-Starter-Kit"folder by using "cd CarND-Term1-Starter-Kit" 
3. Set up the environment using "conda env create -f environment.yml" in "Anaconda Prompt"
4. Verify that the carnd-term1 environment was created in your environments by using "conda info --envs" in "Anaconda Prompt"
5. Activate the environment by using "activate carnd-term1". This MUST be done each time you begin a new working session i.e. open a new terminal window. 

**Step 2:** Open the code in a Jupyter Notebook

Everything worked fine until "Click on the file called 'P1.ipynb'". We don't even have the "P1.ipynb" in the "CarND Term1 Starter Kit". Got the answer immediately from the forum: [How and where do I write the code for the Term1Project1](https://discussions.udacity.com/t/how-and-where-do-i-write-the-code-for-the-term1project1/388155). Quoted from the reply of subodh.malgonde (Forum Mentor): "You actually need to setup your environment using the starter kit. Just downloading the starter kit won’t be sufficient. Once you set up the environment you need to clone this GitHub repository - CarND-LaneLines-P1. You will editing and running your code in something in the file P1.ipynb. The extension .ipynb stands for iPython notebook. You will be using Jupyter notebook to open/edit/run this file." So, steps summarized as:

1. Open "Git CMD", clone the environment by pasting "git clone https://github.com/udacity/CarND-LaneLines-P1.git" 
2. Open "Anaconda Prompt", navigate to the "CarND-LaneLines-P1"folder by using "cd CarND-LaneLines-P1" 
3. Activate the environment by using "activate carnd-term1". 
4. Open jupyter notebook by "jupyter notebook". Follow the instructions to open jupyter notebook in your browser. 

A hint for people with non-CS background: "cd" is a command used to change the current directory (i.e., the directory in which the user is currently working) to the directory you would like to go. Thus, you can clone package to wherever location you prefer by first change directory in "Git CMD". Then, you also need to change the directory in "Anaconda Prompt". 

**Step 3:** Test on Videos
In the [P1.ipynb](https://github.com/udacity/CarND-LaneLines-P1/blob/master/P1.ipynb), when started to "Test on Videos", I got errors as stated:  
```
NeedDownloadError: Need ffmpeg exe. 
You can download it by calling: 
imageio.plugins.ffmpeg.download()
```
I followed the answer in [Project: error of Test on Videos](https://discussions.udacity.com/t/project-error-of-test-on-videos/274082), then [this post](https://stackoverflow.com/questions/41402550/raise-needdownloaderrorneed-ffmpeg-exe-needdownloaderror-need-ffmpeg-exe). One answer was verifed to work: 

1. Manual download [ffmpg](https://github.com/imageio/imageio-binaries/blob/master/ffmpeg/ffmpeg-win32-v3.2.4.exe)
2. In your  lib\site-packages\imageio\plugins\ffmpeg.py  file, change  exe = get_remote_file('ffmpeg/' + FNAME_PER_PLATFORM[plat], auto=False)  to  exe = "YOUR_PATH_WITH_FFMPG\\ffmpeg.win32.exe" 
